---
title: Performance of Loops on Collections

date: 2008-11-28T12:11:00+00:00
url: /performance-of-loops-on-collections/

categories:
  - Tech
tags:
  - tidy

---
[Interesting article][1] from [Patrick Smacchia][2] (the [NDepend][3] guy) in which he runs some benchmarks on the cost of looping in different ways over different constructs and comes to the conclusion that:

> “looping on array using for is **5 times cheaper** than looping on List<T> using foreach (which I believe, is what we all do)”

Well worth a read, although I suspect that in my solutions the bottlenecks will remain the out-of-process calls, i.e. database access and web service calls. Still, a 5x gain is not to be sniffed at.

[Patrick Smacchia – An easy and efficient way to improve .NET code performance][1].

 [1]: http://codebetter.com/blogs/patricksmacchia/archive/2008/11/19/an-easy-and-efficient-way-to-improve-net-code-performances.aspx
 [2]: http://codebetter.com/blogs/patricksmacchia
 [3]: http://www.ndepend.com