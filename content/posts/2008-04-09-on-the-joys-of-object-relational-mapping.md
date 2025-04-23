---
title: On the Joys of Object-Relational Mapping

date: 2008-04-09T19:04:00+00:00
url: /on-the-joys-of-object-relational-mapping/

categories:
  - Tech

---
<!--kg-card-begin: html-->

My name is Ian Nelson. I’m a recovering <acronym title="Structured Query Language">SQL</acronym> addict. It’s been four weeks since my last stored procedure.

One of my reasons for [leaving my cosy permanent job and entering the scary cut-throat world of freelancing][1] was to get a broader exposure to different tools, technologies and methodologies, while remaining with my feet planted firmly in the .NET universe. So, when I got offered a position in a team who were using [Subversion][2], [Monorail][3], [Ext.JS][4], [NUnit][5], [Oracle][6] and [NHibernate][7], I jumped at the opportunity.

Of those technologies, it’s definitely NHibernate which has most dramatically changed my perspective on how enterprise solutions can (and should) be developed. For many years now, I’ve considered deep database (particularly SQL Server) skills to be one of my core proficiencies, and have merrily spent (wasted?) countless man hours writing dreary "plumbing" code, by the way of <acronym title="Create, Read, Update, Delete">CRUD</acronym> stored procedures and repetitive Data Access Layers in order to persist my <acronym title="Common Language Runtime">CLR</acronym> entities to the <acronym title="Relational Database Management System">RDBMS</acronym>.

Well, no longer, those days are over. I’ve seen the light and embraced the wonders of NHibernate. For those who are unfamiliar with it, NHibernate is an [Object-Relational Mapper][8], and is a port of a Java utility, Hibernate. The premise is beautifully simple – by decorating your objects with attributes or, more neatly, by creating <acronym title="eXtensible Markup Language">XML</acronym> mapping files, you define the mappings between your .NET domain objects and their persisted representation on the database. Then NHibernate handles all the grunt work of saving your objects to and from the database.

Digging deeper, I discovered that NHibernate has been developed in such a way as to make it easy to embrace best practices in database access techniques. Several years ago I read through [Fowler’s][9] seminal _[Patterns of Enterprise Application Architecture][10]_, and wondered how I would ever find time to develop solutions which made use of the cunning O-R behavioural patterns he described – [Lazy Load][11], [Unit of Work][12], [Identity Map][13], [Query Object][14], [Repository][15], etc. I utterly failed to pick up on this paragraph on page 171:

> _"Remember that you don’t have to build a full-featured database-mapping layer. It’s a complicated beast to build, and there are products available that do this for you."_

Products such as, yes, NHibernate. Or [Wilson ORM][16], or more recently, the [LINQ to SQL][17] offering introduced by Microsoft in the .NET 3.5 Framework.

I’m glad that I have a solid grounding in SQL, and I still believe that other skills related to RDBMSs are useful in the enterprise (i.e. database design, normalisation and index tuning), but I’m pleased that I can now bring myself to relax, stop worrying, and leave an ORM to take care of generating the repetitive CRUD statements required for persisting my domain objects.

So, what have I been doing with all this "free time" that I now have available to me during a hard day at the code face? Well, I’ve been trying to create systems which are more robust and well-designed by making a concerted effort to embrace Test-Driven Development (for real, this time!) But that’s a good topic for [a future post][18]&#8230;

A few useful NHibernate / ORM Resources:

  * [NHibernate][7]
  * [Wilson ORM][19]
  * [LINQ to SQL][17]
  * [NHibernate Best Practices with ASP.NET][20] – article by Billy McCafferty
  * My del.icio.us links tagged with [NHibernate][21] / [ORM][22] / [LINQ][23]
  * [Dot Net Rocks – the ORM Smackdown Show][24]
  * [NHibernate In Action][25]
  * [LINQ In Action][26]
  * [Ayende’s Blog][27]
  * [The NHibernate FAQ][28]
  * [Wikipedia – Object-Relational Mapping][8]

<!--kg-card-end: html-->

 [1]: https://blog.iannelson.uk/going-for-it/
 [2]: http://subversion.tigris.org/
 [3]: http://www.castleproject.org/MonoRail/
 [4]: http://extjs.com/
 [5]: http://www.nunit.org
 [6]: http://www.oracle.com/database/index.html
 [7]: http://www.nhibernate.org
 [8]: http://en.wikipedia.org/wiki/Object-relational_mapping
 [9]: http://www.martinfowler.com
 [10]: http://www.amazon.co.uk/gp/product/0321127420?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=0321127420
 [11]: http://martinfowler.com/eaaCatalog/lazyLoad.html
 [12]: http://martinfowler.com/eaaCatalog/unitOfWork.html
 [13]: http://martinfowler.com/eaaCatalog/identityMap.html
 [14]: http://martinfowler.com/eaaCatalog/queryObject.html
 [15]: http://martinfowler.com/eaaCatalog/repository.html
 [16]: http://www.ormapper.net/
 [17]: http://msdn2.microsoft.com/en-us/library/bb425822.aspx
 [18]: https://blog.iannelson.uk/12-reasons-why-i-love-unit-tests/
 [19]: http://www.ormapper.net
 [20]: http://www.codeproject.com/KB/architecture/NHibernateBestPractices.aspx
 [21]: http://del.icio.us/ianfnelson/nhibernate
 [22]: http://del.icio.us/ianfnelson/orm
 [23]: http://del.icio.us/ianfnelson/linq
 [24]: http://www.dotnetrocks.com/default.aspx?showNum=240
 [25]: http://www.amazon.co.uk/gp/product/1932394923?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=1932394923
 [26]: http://www.amazon.co.uk/gp/product/1933988169?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=1933988169
 [27]: http://www.ayende.com/
 [28]: http://blogs.hibernatingrhinos.com/nhibernate/Default.aspx