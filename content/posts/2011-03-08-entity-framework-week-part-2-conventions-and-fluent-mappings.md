---
title: 'Entity Framework Week Part 2: Conventions and Fluent Mappings'

date: 2011-03-08T09:03:00+00:00
url: /entity-framework-week-part-2-conventions-and-fluent-mappings/
series:
  - 'Entity Framework Week'
weight: 2
categories:
  - Tech
tags:
  - tidy

---
_This is the second in a series of five posts recounting my experiences using Entity Framework Code-First to replace ADO.NET and stored procedures in a client’s existing application. [The introductory post in the series is here][1]._

As mentioned in yesterday’s post, I was attempting to use [Entity Framework][2] Code-First CTP5 to map an existing domain model to an existing database schema. Fortunately the project was in its infancy and there was a high degree of cohesion between the two models. I therefore didn’t anticipate too many difficulties ahead – the occasional naming discrepancy to resolve, and table-per-hierarchy mappings that would need their discriminators specifying – nothing too complicated really. I hoped to make as few changes as possible to either the database schema or domain model.

Entity Framework Code-First uses a set of conventions to “discover” the mappings from domain objects to database. This is broadly analogous to James Gregory’s Fluent NHibernate [AutoMapping][3] functionality.

As with Fluent NHibernate, it is possible to add custom conventions, and to manually override mappings for specific properties which deviate from the conventions. It is also possible to remove existing conventions.

All of these modifications to the model mappings are affected by overriding the virtual OnModelCreating method in our concrete implementation of DbContext. I was initially worried about the sheer volume of code that might be included in this method, and was relieved to discover that mapping overrides related to particular entities can be separated out into the constructor of generic implementations of EntityTypeConfiguration, not unlike the generic ClassMap in Fluent NHibernate.

### Custom Conventions {#custom-conventions}

In the domain model I was working with, all entities were derived from an abstract base Entity class which defined an integer Id property. By contrast, the primary keys on the database tables were all prefixed with the name of the table/entity. Neither of these situations are ideal, but nor are they all that unusual, and I sought a way of “teaching” this convention to our custom EF context.

It took me some time to discover that custom conventions are even possible in CTP5, and I had initially resigned myself to manually overriding the names of each and every primary key property. It was only through stumbling upon [this post on the ADO.NET team blog][4] that I found what I was looking for. Note that this post does include the caveat “There are a number of rough edges and the API surface is likely to change”.

My first impression is that custom Entity Framework conventions could turn out to be far more powerful than those offered by Fluent NHibernate, but they are also trickier to develop, requiring an understanding of the valid options for the two generic parameters that IConfigurationConvention can take, and what actions should be taken by the custom convention.

Still, after a little trial and error I was able to write the custom primary key convention that I required:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

I was disappointed that I had to insert a guard clause to ignore this convention for the concrete subclasses of hierarchies that are mapped using table-per-hierarchy (i.e. ProductFeature and ProductInsert). Given time I would hope to find a generic way of achieving this convention that doesn’t require hardcoded references to specific Domain objects from within the convention definition.

Compare and contrast with the equivalent code for Fluent NHibernate:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

**Updated:**

Since I wrote the section above, the ADO.NET team have [announced details of the forthcoming Entity Framework 4.1 Release Candidate][5], which removes this ability add conventions:

> “This was a very painful decision but we have decided to remove the ability to add custom conventions for our first RC/RTW. It has become apparent we need to do some work to improve the usability of this feature and unfortunately we couldn’t find time in the schedule to do this and get quality up the required level. You will still be able to remove our default conventions in RC/RTW.”

For what it’s worth, I think this was the right decision to make. A lack of “pluggable” conventions is slightly disappointing, but it can easily be worked around by making the appropriate overrides with the fluent mappings. Better to hold off an nail an API that’s both powerful and usable than go too soon with something that’s liable to confuse and confound.

### Removal of Default Conventions {#removal-of-default-conventions}

Another nice feature described in the [Pluggable Conventions blog post][4] is the ability to remove some of the default conventions, which I immediately put to good use by disabling the default PluralizingTableNameConvention:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

_(I mean, for goodness sake, who in their right mind pluralizes table names anyway? Yes, it’s very impressive that this library knows that the plural of “goose” is “geese”, but it would be more beneficial if that were an extension method on System.String in the BCL rather than being buried in the bowels of System.Data.Entity.Design. Then perhaps the ADO.NET team could be left to get on with developing something more useful, like second-level caching? Sorry, rant over…)_

### Fluent Mapping API {#fluent-mapping-api}

Most manual tweaks to the model are fairly straightforward to perform, and there are a good set of examples in [this post on the ADO.NET team blog][6].

I did encounter some difficulty with the mapping of one-to-many relationships, which felt quite cumbersome to perform in comparison to the brevity of Fluent NHibernate’s API. Here’s how you’d rename a foreign key on a unidirectional one-to-many relationship in Fluent NHibernate:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

Whilst in Entity Framework code-first, the equivalent is:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

To be fair, I think part of this clumsiness arises because Entity Framework is allowing us to define both ends of a bidirectional relationship in a single place, whereas [NHibernate][7] requires us to define each end separately. It’s just unfortunate that in unidirectional situations like this example we end up with the WithMany().IsIndependent() noise in the middle of the syntax.

Having learned the odd syntax required to rename these one-to-many foreign keys, I then wasted an inordinate amount of time trying to make this actually work. Many of my waking hours were blighted by an InvalidOperationException (“Sequence contains more than one matching element”) originating from deep within the framework. A quick ferret aro  
und on Stack Overflow revealed that I was not the only person currently banging his or her head on this particular brick wall:

  * [EF Code First CTP5 – Using the name of the property as column name for foreign key][8]
  * [Entity Framework 4 CTP 5 Self Referencing Many-to-Many][9]
  * [Entity framework (CTP5, Fluent API). Rename column of navigation property][10]

Eventually [Diego Mijelshon figured out what was amiss][11]. It seems the mapping failure was due to the Id property being defined in a base class rather than on the concrete class being mapped. Whether this is intentional behaviour or a bug in the CTP5, I’m not sure, but I worked around this issue by modifying the domain model and ditching the hierarchy of base classes altogether, leaving the Id and other common properties defined only on interfaces. [Ayende would be pleased][12].

Two days into my adventure, and my database and domain model were happily mapped. In [part three][13] I’ll look at some of the issues I encountered at runtime, which necessitated further tweaks to the domain model and database.

 [1]: https://blog.iannelson.uk/entity-framework-week-part-1-introduction-configuration-and-initialization/
 [2]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [3]: http://wiki.fluentnhibernate.org/Auto_Mapping
 [4]: http://blogs.msdn.com/b/adonet/archive/2011/01/10/ef-feature-ctp5-pluggable-conventions.aspx
 [5]: http://blogs.msdn.com/b/adonet/archive/2011/03/02/ef-4-1-is-coming-dbcontext-api-amp-code-first-rtw.aspx
 [6]: http://blogs.msdn.com/b/adonet/archive/2010/12/14/ef-feature-ctp5-fluent-api-samples.aspx
 [7]: http://www.nhforge.org
 [8]: http://stackoverflow.com/questions/5008479/ef-code-first-ctp5-using-the-name-of-the-property-as-column-name-for-foreign-ke
 [9]: http://stackoverflow.com/questions/4981228/entity-framework-4-ctp-5-self-referencing-many-to-many
 [10]: http://stackoverflow.com/questions/4660908/entity-framework-ctp5-fluent-api-rename-column-of-navigation-property
 [11]: http://stackoverflow.com/questions/5008479/ef-code-first-ctp5-using-the-name-of-the-property-as-column-name-for-foreign-ke/5090600#5090600
 [12]: http://ayende.com/blog/archive/2011/02/21/code-review-guidelines-avoid-inheritance-for-properties.aspx
 [13]: https://blog.iannelson.uk/entity-framework-week-part-3-runtime-issues-encountered/