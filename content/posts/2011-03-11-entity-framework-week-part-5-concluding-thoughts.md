---
title: 'Entity Framework Week Part 5: Concluding Thoughts'

date: 2011-03-11T09:03:00+00:00
url: /entity-framework-week-part-5-concluding-thoughts/
series:
  - 'Entity Framework Week'
weight: 5
tags:
  - tidy

---
_This is the fifth in a series of five posts recounting my experiences using Entity Framework Code-First to replace ADO.NET and stored procedures in a client’s existing application. [The introductory post in the series is here][1]._

I am lucky to have had the opportunity to spend a time-boxed period playing with [Entity Framework][2] Code-First in a real-world scenario, and to get paid for the privilege! I now have a clearer understanding of how it has progressed during the last few years, what its strong points are, and where it still has shortcomings compared to the much more mature [NHibernate][3] framework.

### The Positives {#the-positives}

I have to say that after a week of getting through the pain barrier and the initial denial of working with an unfamiliar ORM, I have reached a level of understanding and acceptance with Entity Framework. It really isn’t all that bad (at least the Code-First flavour), and if you don’t stray too far from its rigid way of thinking it will help you to get a solution up and running quickly and reliably. It’s certainly a far preferable option than mucking about with ADO.NET and stored bloody procedures, that’s for sure.

The whole process of configuration and initialization is straightforward and pain-free, with the derived DbContext providing a out-of-the-box implementation of Unit of Work already to be referenced from your consuming code. Easy.

Querying the model is 99% unadulterated LINQ, with the occasional call to Include to perform some eager fetching – what could be simpler?

I’m also unashamedly impressed with how easily EF can be used to power [ASP.NET Dynamic Data][4] sites, and RESTful WCF Data Services. Nice.

### The Negatives {#the-negatives}

I found that the real pain of working with Entity Framework only surfaces when you wish to start tuning its behaviour in any way – you find that it’s a big black box with few extensibility points. It performs cunning tricks effortlessly, but wields its power in a largely indiscriminate manner. By comparison, NHibernate can achieve even greater things, but requires you to explicitly invoke these powers.

I am reminded of [a response Ayende gave][5] when asked why NH Futures was not the default behaviour – “NHibernate tries hard not to make too much magic”. I thought it sounded glib at the time, but having lived with EF for a while, I now understand why this is preferable.

Most of the NHibernate features that are missing from Entity Framework are related to performance – such as the ability to configure query batching, write batching, bulk operations, extra-lazy properties, and second-level caching. These are the features you’ll miss the most when you’re some way into a project, perhaps not until it’s in production and scalability issues arise.

I also feel the CTP5 of EF code-first is a little way off offering true support for persistence ignorance and POCO, having experienced a number of issues that required me to change my domain model, database schema, and application code.

### Additional Resources {#additional-resources}

Here are a few of the resources that I found particularly useful during my EF week:

  * [Programming Entity Framework, Second Edition][6]
  * [Dino Esposito – A Feature-Driven Comparison of EF and NH][7]
  * [ADO.NET Team Blog][8]
  * [Using DbContext in EF Feature CTP5 &#8211; a series of 12 blog posts][9]
  * [David Ebbo – Using Dynamic Data With EF Code First and NuGet][10]

 [1]: https://blog.iannelson.uk/entity-framework-week-part-1-introduction-configuration-and-initialization/
 [2]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [3]: http://www.nhforge.org
 [4]: http://www.asp.net/dynamicdata
 [5]: http://ayende.com/Blog/archive/2009/04/27/nhibernate-futures.aspx#30714
 [6]: http://amzn.to/1ffRzv4
 [7]: http://dotnetslackers.com/articles/ado_net/A-Feature-driven-Comparison-of-Entity-Framework-and-NHibernate-Multiple-Databases.aspx
 [8]: http://blogs.msdn.com/b/adonet/
 [9]: http://blogs.msdn.com/b/adonet/archive/2011/01/27/using-dbcontext-in-ef-feature-ctp5-part-1-introduction-and-model.aspx
 [10]: http://blog.davidebbo.com/2011/01/using-dynamic-data-with-ef-code-first.html