---
title: 'Entity Framework Week Part 1: Introduction, Configuration and Initialization'

date: 2011-03-07T09:03:00+00:00
url: /entity-framework-week-part-1-introduction-configuration-and-initialization/
series:
  - 'Entity Framework Week'
categories:
  - Tech

---
In February 2011 I found myself doing some contract development work in a team that was still doing data access using raw ADO.NET and stored procedures. Being the [NHibernate][1] fanboy that I am, I naturally attempted to persuade them of the benefits of moving over to NH, even going so far as to develop (in my own time) an NH-powered version of their application.

My efforts were _partially_ successful. The team were sold on the idea of using an ORM, but wanted me to develop a second proof of concept using Microsoft ADO.NET [Entity Framework][2] rather than NHibernate. This prompted much mirth amongst my FaceBook friends.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/FB_3.png" class="kg-image" alt loading="lazy" /> </figure> 

I decided to throw myself into the task, and use this opportunity to spend some time getting to grips with Entity Framework in a real-life scenario for a couple of weeks. I figured that in the best-case scenario, I would learn to love EF even more than NH, and bolster my CV. Worst case, I’d hate it but would be moving on to a new contract shortly anyway, so wouldn’t have to live with it for too long. And of course I was getting paid for the experience either way, so what’s not to like?!

A couple of friends rightly suggested that I ought to blog about my experiences, so here we go.

This series of five blog posts details the thoughts and experiences I encountered during my week-long adventure with Entity Framework. It isn’t an EF walkthrough, nor is it a comprehensive EF-vs-NH feature comparison (the web is littered with those).

  1. [Introduction, Configuration and Initialization][3]
  2. [Conventions and Fluent Mappings][4]
  3. [Runtime Issues Encountered][5]
  4. [Features and Further Investigations][6]
  5. [Concluding Thoughts][7]

### Choosing Code-First {#choosing-code-first}

When last I had a quick play with Entity Framework in the summer of 2008, it was very IDE and database-driven – the development process entailed dragging tables onto a designer surface which generated partial classes to represent objects, etc. Yuk! The lack of support for a domain-driven, persistence-ignorant approach was a real turn-off for me, prompting me to add my name to the list of signatories on the infamous [ADO.NET Entity Framework Vote of No Confidence][8].

It was therefore a relief to discover that Entity Framework now supports a “Code-First” development paradigm, whereby EF can be used like a traditional ORM to fluently map an existing domain model to an existing database. At the time, this was still available only as a Community Technology Preview ([CTP5][9]), but given my remit was to introduce EF to an existing solution, it was a no-brainer to choose this option for the proof of concept, even though this would potentially leave me exposed to bugs and breaking API changes.

### Configuration {#configuration}

Configuring Entity Framework seemed a lot easier than the equivalent procedure with NHibernate, filled as it is with esoteric options which can often be somewhat perplexing to NH newbies. With EF, the walkthroughs told me that essentially, all I needed to do was create a subclass of DbContext and Bob would be my mother’s brother. They were right. If anything, it was all too easy, and I wondered how and where I would get the option to configure details such as the second-level cache provider and ADO batch size.

I made use of a constructor overload on DbContext which takes a string parameter called nameOrConnectionString. Initially I attempted to pass into this parameter a connection string obtained from the app.config file using System.Configuration.ConfigurationManager, but this led to error messages along the lines of

> “Unable to determine the provider name for connection of type ‘System.Data.SqlClient.SqlConnection’”

It seems that the connection strings used by Entity Framework are not the common or garden connection strings that we know and love, but instead special EF connection strings. Fortunately, a simple remedy to this issue was to instead just pass the connection string _name_ into the exact same parameter. [See this forum post for more details][10].

### Database Initializer Strategies {#database-initializer-strategies}

[Entity Profiler][11] revealed that Entity Framework was unsuccessfully attempting to access a nonexistent database table called dbo.EdmMetadata. A little light Googling revealed that this is used by Entity Framework to store (perhaps unsurprisingly) metadata about the Entity Data Model. Why does it do this? Presumably so that it can decide at application start up whether code changes to the model require it to automagically make associated changes to the database schema. Some Summer 2010 blog posts from Scotts [Guthrie][12] and [Hanselman][13] show off the ability of Entity Framework to automatically create and update databases in response to model changes.

Now, this is all very clever and might be fine for hobbyist websites, integration tests and those quintessential “Look – no code!” TechEd presentations, but in an enterprise scenario it’s liable to cause acute apoplexy in DBAs.

Fortunately we can opt to suppress this crazy behaviour altogether by passing a null strategy into DbDatabase.SetInitializer, thus:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

That was day one over – I was officially up and running in the brave new (to me) world of Entity Framework. In [part two of this series][4] I’ll take a look at the mapping tweaks I had to make to successfully map our existing domain model to our existing database.

 [1]: http://www.nhforge.org
 [2]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [3]: https://blog.iannelson.uk/entity-framework-week-part-1-introduction-configuration-and-initialization/
 [4]: https://blog.iannelson.uk/entity-framework-week-part-2-conventions-and-fluent-mappings/
 [5]: https://blog.iannelson.uk/entity-framework-week-part-3-runtime-issues-encountered/
 [6]: https://blog.iannelson.uk/entity-framework-week-part-4-features-and-further-investigations/
 [7]: https://blog.iannelson.uk/entity-framework-week-part-5-concluding-thoughts/
 [8]: http://efvote.wufoo.com/forms/ado-net-entity-framework-vote-of-no-confidence/
 [9]: http://www.microsoft.com/downloads/en/details.aspx?FamilyID=35adb688-f8a7-4d28-86b1-b6235385389d
 [10]: http://social.msdn.microsoft.com/Forums/eu/adonetefx/thread/8d18825d-7e44-4c7f-9e7d-1e73479fe0e7
 [11]: http://efprof.com
 [12]: http://weblogs.asp.net/scottgu/archive/2010/07/16/code-first-development-with-entity-framework-4.aspx
 [13]: http://www.hanselman.com/blog/SimpleCodeFirstWithEntityFramework4MagicUnicornFeatureCTP4.aspx