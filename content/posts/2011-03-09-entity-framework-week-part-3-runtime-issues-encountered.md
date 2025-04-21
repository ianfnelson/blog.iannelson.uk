---
title: 'Entity Framework Week Part 3: Runtime Issues Encountered'

date: 2011-03-09T09:03:00+00:00
url: /entity-framework-week-part-3-runtime-issues-encountered/

categories:
  - Tech
tags:
  - tidy

---
_This is the third in a series of five posts recounting my experiences using Entity Framework Code-First to replace ADO.NET and stored procedures in a client’s existing application. [The introductory post in the series is here][1]._

Having configured and initialized [Entity Framework][2], and tweaked the mappings, by Day 3 I was all set to start consuming my shiny new DbContext implementation from the application code, and actually get some CRUD work done. Not unexpectedly, I hit a few issues along the way…

### Proxy Generation {#proxy-generation}

As a long-term [NHibernate][3] user, I habitually mark all members on my domain classes as virtual, since this is a requirement for entities to be replace at runtime by proxies. Remember that NHibernate is a port from the Java world, where all instance methods are virtual by default.

Now, this habit led to some unexpected behaviour when I attempted to use Entity Framework to persist the same domain objects, namely exception messages such as:

> The property ‘Foo’ on type ‘Bar_B6089AE40D178593955F1328A70EAA3D8F0F01DDE9F9FBD615F60A34F9178B94’ cannot be set because the collection is already set to an EntityCollection.

Clear as mud, eh? A little Googling eventually unearthed the following posts from other people experiencing this issue:

  * [Why is my Entity Framework Code First proxy collection null and why can’t I set it?][4]
  * [Code First adding to collections? How to use Code First with repositories? Advice me please][5]
  * [Code First EF4 with N-Tier.. I’m really stuck on this one issue][6]

This latter post on the MSDN forums includes the following explanation from one of the guys on the Entity Framework team:

> “If you make all your properties virtual then EF will generate proxy classes at runtime that derives from your POCO classed, these proxies allow EF to find out about changes in real-time rather than having to capture the original values of your object and then scan for changes when you save (this is obviously has performance and memory usage benefits but the difference will be negligible unless you have a large number of entities loaded into memory). These are known as ‘change tracking proxies’, if you make your navigation properties virtual then a proxy is still generated but it is much simpler and just includes some logic to perform lazy loading when you access a navigation property.

> Because your original code was generating change tracking proxies, EF was replacing your collection property with a special collection type to help it find out about changes. Because you try and set the collection back to a simple list in the constructor you are getting the exception.

> Unless you are seeing performance issues I would follow Terrence’s suggestion and just remove ‘virtual’ from your non-navigation properties.”

This feels a little bit strange, and I’m not convinced that we are really getting persistence ignorance if we experience differing behaviour depending on whether or not we have chosen to make all our members virtual. I haven’t invested much time looking into the benefits of these “Change-Tracking Proxies”, or how it is possible to utilise these without causing the “collection is already set to an EntityCollection” exception. I just did what the man said and removed the virtual keyword from most non-navigation properties.

### A Runtime Exception When Lazy-Loading {#a-runtime-exception-when-lazy-loading}

At one point I experienced an exception message along the lines of:

> “Entities in ‘CodeFirstContainer\_Sessions’ participate in the ‘Session\_Season’ relationship. 0 related ‘Session\_Season\_Target’ were found. 1 ‘Session\_Season\_Target’ is expected.”

This was caused by my navigation property (Session.Season) not having been set as virtual, so no proxy was being created.

Incidentally, it is worth highlighting that lazy-loading must occur within the scope of an open DbContext (i.e. within the Unit of Work). It is not reasonable to expect to transparently load the navigation property after the database connection has been closed (this is analogous to attempting to lazy-load in NHibernate after closing the Session).

### Cascades {#cascades}

In NHibernate, cascading saves/updates/deletes have to be specified manually on all foreign key relationships – the default behaviour is not to cascade any changes when committing changes, which often leads to newcomers experiencing an error message “not-null property references a null or transient value”.

Entity Framework takes a more convention-based approach and assumes that all saves and updates should cascade. So, if you save a shiny new Order with an associated Address and a handful of Lines, Entity Framework will determine that it should first insert the Address row, then the Order row, and then each Line row. Sweet. Updates similarly cascade. Assuming you are happy with this behaviour (which seems sensible), then all should be well.

Deletes, on the other hand, are a bit strange. Entity Framework will not take responsibility for cascading a delete in the database – it expects that you will achieve this by setting a cascading delete on the foreign key relationship in the RDBMS.

Having said this, if you delete a parent entity in Entity Framework, it _will_ attempt to issue delete statements for any child entities which have been loaded into the current DbContext, but it will not initialize any child entities which have not yet been loaded. This may lead to the RDBMS throwing foreign key constraint violation exceptions if a cascading delete has not been specified. For more details about how cascade delete “works” in Entity Framework, [see this blog post][7].

Personally, I think this behaviour is pretty shoddy, but there you have it! Forewarned is forearmed.

In light of this behaviour I had to make modifications to the database schema to set cascading deletes on all the appropriate foreign key relationships. For many line-of-business applications, deletes are actually pretty rare events, and in the short term I suspect this issue is more likely to be encountered when clearing down data in integration tests than in actual application use.

### Initializing Child Objects on Domain Entities {#initializing-child-objects-on-domain-entities}

I habitually add code to the constructors of domain entities to initialise child entities to sensible defaults – I find it helps to ensure that objects are always in a valid state, and reduces the likelihood of encountering an unhandled NullReferenceException. So, for example, I would usually have something like this:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

Unfortunately, when using this approach with Entity Framework, I found that when loading an existing Order which has an associated Address, the Order.Address object was always reset to its default.

Now, I realise that making calls to virtual members in a constructor is not really a good idea (heaven knows Resharper and Coderush have both nagged me about it often enough), but NHibernate never had a problem with  
this approach. Nevertheless, I tried to do things properly and replaced the automatic properties with backing fields….

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

But still no dice. I then tried putting initialization logic in the property’s getter….

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

But nothing worked. Every time I loaded an Order, the Order.Address object was reset back to its default instead of containing the data loaded from the database.

This is quite frustrating and as yet I haven’t been able to find a workaround, other than to abandon my plans to perform object initialization in the domain model and instead handle it in the service layer, with all the resultant null-checking code that will ensue.

While trying to find a solution, I did stumble across this comment from Rowan Miller that “More flexibility in how we interact with classes is a common ask for EF and our team is looking at how we can support this at the moment.”   Are we asking for flexibility? I thought we were just asking for the persistence ignorance that had long been promised.

Despite these issues, in three short days I had gone from knowing next to nothing about Entity Framework 4 Code first, to using it to perform almost all of the data access required by a small application. In the [fourth part of this series][8] I’ll consider some of the additional features and application requirements that I would expect an ORM to handle, and see how EF meets the challenge.

 [1]: https://blog.iannelson.uk/entity-framework-week-part-1-introduction-configuration-and-initialization/
 [2]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [3]: http://www.nhforge.org
 [4]: http://stackoverflow.com/questions/4069563/why-is-my-entity-framework-code-first-proxy-collection-null-and-why-cant-i-set-i
 [5]: http://stackoverflow.com/questions/3858922/code-first-adding-to-collections-how-to-use-code-first-with-repositories-advice
 [6]: http://social.msdn.microsoft.com/Forums/en/adonetefx/thread/99d8d4a1-5ab1-42dc-b9db-5087be02162d
 [7]: http://blogs.msdn.com/b/alexj/archive/2009/08/19/tip-33-how-cascade-delete-really-works-in-ef.aspx
 [8]: https://blog.iannelson.uk/entity-framework-week-part-4-features-and-further-investigations/