---
title: NHibernate

date: 2004-09-03T19:09:00+00:00
url: /nhibernate/

categories:
  - Tech
tags:
  - NHibernate
  - .NET

---
There’s _so_ much good open-source .Net development going on these days – .Text, nGallery, nUnit, etc – it’s a really interesting time to be a developer. My colleague Colin just drew my attention to [nHibernate][1], an object persistence library for relational databases. [TheServerSide.net][2] has an excellent article summarising its use. Having just finished a long project where a large amount of time was spent writing “plumbing” code to persist objects to and from a SQL Server database, I’m finding the idea of using an O/R mapper such as this very appealing the next time round. Just as incorporating the [MS DAAB block][3] into solutions has reduced the amount of data access code required, I’m hopeful that embracing frameworks such as nHibernate will leave us with more time to spend focusing on addressing the business needs and less on re-solving technical issues.

If anyone has had experience of using nHibernate or similar O/R mapper in an enterprise .NET project, I’d be interesting in hearing your opinions. Would you use it again? Did it genuinely help to abstract away the object persistence/retrieval mechanisms from the domain model, or is it just one more layer to worry about and keep up to date? Let me know.

 [1]: http://sourceforge.net/projects/nhibernate
 [2]: http://www.theserverside.net/articles/showarticle.tss?id=NHibernate
 [3]: http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnbda/html/daab-rm.asp