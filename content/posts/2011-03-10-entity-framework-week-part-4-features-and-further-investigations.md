---
title: 'Entity Framework Week Part 4: Features and Further Investigations'

date: 2011-03-10T09:03:00+00:00
url: /entity-framework-week-part-4-features-and-further-investigations/
series:
  - 'Entity Framework Week'
categories:
  - Tech

---
_This is the fourth in a series of five posts recounting my experiences using Entity Framework Code-First to replace ADO.NET and stored procedures in a client’s existing application. [The introductory post in the series is here][1]._

I didn’t want this series of posts to descend into a point-scoring [NHibernate][2]-versus-[Entity Framework][3] comparison, but…

I now have a basic proof-of-concept up and running, with my client’s nascent application now being powered by Entity Framework Code-First CTP5 rather than a hand-rolled DAL. So, I had some time to consider future functional and non-functional requirements that the team would be asked to develop and support, and investigate how EF would meet the challenge.

### Caching {#caching}

I was genuinely surprised to learn that Entity Framework still doesn’t include any out-of-the-box support for integrating second-level caching, for example to cache reference data. It seems there is a body of opinion stating that caching should not be the responsibility of the data access layer. I disagree, and I think this is one of the major benefits NHibernate still has over Entity Framework, with its multiple flexible and configurable second-level cache providers.

### Targeting Alternative Providers (SQLite) {#targeting-alternative-providers-sqlite-}

When working with NHibernate, I often target [SQLite][4] for fast integration tests against an in-memory database, rather than maintaining a testing version of the MSSQL/Oracle databases that my applications usually use for their bitbucket. I was pleased to see the discussions on the System.Data.SQLite page suggesting that this approach is possible with Entity Framework too, but I didn’t spend any time attempting to get this working.

### Auditing Functionality {#auditing-functionality}

Entity Framework does not appear to support the rich events and listeners model that is offered by NHibernate and frequently used to develop application auditing functionality. The recommended solution to achieve this scenario is to override the virtual SaveChanges method on DbContext and add validation and auditing logic there. For more details, see [page 261 of Programming Entity Framework][5].

### Bulk Operations {#bulk-operations}

I have not yet encountered any Entity Framework support for bulk update/delete operations akin to NHibernate’s [Executable DML][6] functionality. Such requirements are usually relatively rare, but it’s a shame to have to fall back to writing stored procedures for relatively simple operations which can be described in terms of the domain model.

### Query Batching {#query-batching}

There does not appear to be any way to do query batching in Entity Framework, as per [NHibernate Futures][7]. Multiple queries result in multiple network trips to the database, sadly. Similarly, there’s no support for write batching and batched collection loads.

### Concurrency and Versioning {#concurrency-and-versioning}

Entity framework supports optimistic concurrency. [Chapter 23 of Programming Entity Framework][8] explains in detail how this can be configured and utilised by your application. Entity Framework also supports rowversion fields for concurrency checks.

### Extra-Lazy Properties {#extra-lazy-properties}

Unlike NHibernate, Entity Framework currently has no notion of “extra-lazy” properties. Requesting the Count of a child collection (e.g. Order.Lines.Count) will therefore trigger the loading of all entities (Lines) in the child collection. Not nice. Yes, we can work around this by making the appropriate count query at a higher level but it’s much nicer to be able to traverse the domain model relationships and let persistence ignorance work it’s magic.

### Integration with the Wider .NET Stack {#integration-with-the-wider-net-stack}

To my mind, one of the key selling points of Entity Framework over NHibernate is its out-of-the-box integration with other areas of the .NET stack – notably the ability to power [ASP.NET Dynamic Data][9] sites (which are great for simple pages to maintain reference data) and [WCF Data Services][10].

### Query Techniques {#query-techniques}

NHibernate offers a world of choice when it comes to methods for querying the model: HQL, Criteria, QueryOver, LINQ, Named Queries, etc. These each offer a plethora of possible options and tweaks including query caching, batching and futures. By comparison, Entity Framework offers a comprehensive LINQ provider (with decent extensions to specify eager-loading of child entities), or Entity SQL. And that’s your lot.

By the end of my fourth day, I had a working proof-of-concept using Entity Framework Code First to power my client’s application, and I had a good idea of how suitable it was to meet future requirements lurking in the product backlog.

In the [fifth and final part of this series of posts][11], I’ll write some concluding thoughts on my overall experiences spending a week with Entity Framework.

 [1]: https://blog.iannelson.uk/entity-framework-week-part-1-introduction-configuration-and-initialization/
 [2]: http://www.nhforge.org
 [3]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [4]: http://www.sqlite.org
 [5]: http://my.safaribooksonline.com/book/software-engineering-and-development/9780596807276/working-with-object-services/261
 [6]: http://ayende.com/blog/archive/2009/05/28/nhibernate-ndash-executable-dml.aspx
 [7]: http://ayende.com/blog/archive/2009/04/27/nhibernate-futures.aspx
 [8]: http://my.safaribooksonline.com/book/software-engineering-and-development/9780596807276/planning-for-concurrency-problems/659
 [9]: http://www.asp.net/dynamicdata
 [10]: http://msdn.microsoft.com/en-us/data/bb931106
 [11]: https://blog.iannelson.uk/entity-framework-week-part-5-concluding-thoughts/