---
title: 'Inside Microsoft SQL Server 2005: The Storage Engine'

date: 2008-01-05T21:01:00+00:00
url: /inside-microsoft-sql-server-2005-the-storage-engine/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2008/01/mssqlstorageengine_4-1.jpg

categories:
  - Tech
tags:
  - tidy

---
During 2007, I unexpectedly achieved a long-held ambition by increasing the number of books I regularly read (as opposed to merely buying, then leaving them to languish on the bookcase!). I read plenty of techie books of course, but also made use of local libraries and devoured plenty of books on other subjects, and even found time for some fiction. I think having a young baby in the house was partially responsible for this achievement &#8211; not much else to do of an evening any more!

Some books were great and will remain on my shelves for years to come. Plenty others were quickly returned to the libraries, or resold on Amazon Marketplace. Either way, I figure that it might be a nice addition to the old blog if I take the time to say a few words about some of them, so let’s start with the book I’ve finished most recently.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/mssqlstorageengine_4.jpg" class="kg-image" alt loading="lazy" /> </figure> 

_Inside Microsoft SQL Server 2005: The Storage Engine_ by Kalen Delaney is one in a series of four books from MS Press, the other three having subtitles of _[T-SQL Programming][1], [T-SQL Querying][2],_ and _[Query Tuning and Optimization][3]_. I suspect that _The Storage Engine_ is the most deep and esoteric of the four volumes, offering an insight into the architecture and inner workings of SQL Server that isn’t matched even by my old favourite _[SQL Server 2005 Unleashed][4]._

By no stretch of the imagination could this be considered an introduction to SQL Server, and frequently I found myself skipping forward a few pages at a time, reasoning to myself that &#8220;there is no reason why I will ever need to know this!&#8221; &#8211; indeed, plenty of the first half of the book on topics such as architecture, configuration, files, logging, and recovery, would be of more use to DBAs and sysadmins rather than developers such as myself &#8211; not that it isn’t nice to have an appreciation of these topics though.

From a developer perspective, it is the second half where this book really springs to life, with three great chapters on Tables, Indexes, and Locking & Concurrency. These are 235 pages of pure gold, offering to the willing reader a really _deep_ understanding of what is really going on under the hood, and how exactly MSSQL goes about implementing your requests. It certainly blew apart some of my incorrect assumptions about internal table structures, and has given me a better understanding of the internal structures of clustered and nonclustered indexes.

SQL Server is one of the most widely used products in Microsoft’s server range, and in my opinion also one of the most widely abused. Anyone who has worked in this industry for any length of time has inevitably witnessed some awful database designs (no primary keys? no foreign keys? no indexes? every column a varchar(50)? you know the kind of thing!), but we can all learn to improve our database designs, and the level of understanding offered by Kalen’s book should help in the quest for perfection.

As long as my career keeps its technical focus, and I’m using SQL Server 2005, then this one is a keeper, and I’ve already ordered Kalen’s other book in the series, _[Query Tuning and Optimization][3]_.

 [1]: http://www.amazon.co.uk/gp/product/0735621977?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=0735621977
 [2]: http://www.amazon.co.uk/gp/product/0735623139?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=0735623139
 [3]: http://www.amazon.co.uk/gp/product/0735621969?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=6738&creativeASIN=0735621969
 [4]: https://blog.iannelson.uk/sql-2005-unleashed/