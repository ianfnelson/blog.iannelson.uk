---
title: Universal Comparer for .NET

date: 2006-02-27T22:02:00+00:00
url: /universal-comparer-for-net/

categories:
  - Tech
tags:
  - .NET

---

Back in November 2004, I had the idea of making a "[Generic Sorter for Strongly-Typed Collections][1]", by harnessing the mighty power of reflection. Well, earlier this month somebody anonymously emailed me some code that takes this to a whole different level, enabling sorting on multiple properties and to arbitrary depths within the domain model hierarchy, all by taking a single SQL-like parameter. It’s really very clever indeed, and I’m going to use this method in the future – thanks, anonymous code fairy!

Oh, while I’m at it, I decided to rename the class, as the use of "Generic" could be confusing now we have the generic language feature in .NET 2.0. Also, this class doesn’t actually do the sorting, it just implements IComparer to do the comparing. So, with the help of a thesaurus, I settled on "UniversalComparer"!

{{< gist 9861758 >}}

 [1]: https://blog.iannelson.uk/a-generic-sorter-for-strongly-typed-collections/