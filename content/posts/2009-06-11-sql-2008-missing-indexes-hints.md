---
title: SQL 2008 – Missing Indexes Hints

date: 2009-06-11T12:06:00+00:00
url: /sql-2008-missing-indexes-hints/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2009/06/amc1_2-1.png

categories:
  - Tech

---
Improvements to the Execution Plan UI in SQL Server Management Studio 2008 sure do make it a doddle to improve query execution time.

A client just reported that a particular stored procedure kept timing out.

Viewing the Estimated Execution Plan for this query displayed a nice green message advising of a potentially missing index which could improve performance by >95%:<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/amc1_2.png" class="kg-image" alt loading="lazy" /> </figure> 

Right-clicking and selecting “Missing Index Details” then brings up a new query window containing the index creation DDL (I had changed the index name by the time I grabbed this capture):<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/amc2_2.png" class="kg-image" alt loading="lazy" /> </figure> 

Dead easy. Repeating the process identified a second index which could further improve performance by >80%.

Of course, you still need to bear in mind other queries which access the table, and the effects on inserts/updates of creating additional indexes, but even so, this really helps the workflow.

The suggested indexes functionality was actually available in SSMS 2005 too, but the results were buried away in the XML version of the execution plan, and obscure properties windows, rather than being so in your face.