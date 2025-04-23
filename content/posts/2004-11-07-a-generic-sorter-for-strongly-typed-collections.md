---
title: A Generic Sorter For Strongly-Typed Collections

date: 2004-11-07T21:11:00+00:00
url: /a-generic-sorter-for-strongly-typed-collections/

categories:
  - Tech

---
<!--kg-card-begin: html-->

Late last night I was doing some development work on a website for our investment club. I had a strongly-typed collection of "Stock" objects, and wanted to be able to sort them on any parameter (StockName, SharePrice, Volume, MarketCap, etc..) in either descending or ascending order. I didn’t want to have to write a separate comparer for each property. Reflection to the rescue! Below is a GenericSorter class, the use of which allows for the development of a Sort() method on the collection taking as a parameter the name of the property on which to sort. Smart.



Bob’s your uncle.

**Update** [2006-02-27]: The above class is no match for some [much more fully-featured code][1] that was anonymously sent to me earlier this month which allows for sorting on multiple properties to arbitrary depth within the domain object model, using a simple SQL-like syntax. [Check it out&#8230;][1]

<!--kg-card-end: html-->

 [1]: https://blog.iannelson.uk/universal-comparer-for-net/