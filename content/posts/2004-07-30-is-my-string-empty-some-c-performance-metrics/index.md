---
title: 'Is My String Empty?  Some C# Performance Metrics'

date: 2004-07-30T10:07:00+00:00
url: /is-my-string-empty-some-c-performance-metrics/

categories:
  - Tech
tags:
  - .NET

---

**Update (25/02/2006)** – Hey, we now have [String.IsNullOrEmpty][1], you know!

---

What’s the quickest way, in C#, to test whether a string is empty? This is a question which came to my mind yesterday. I’ve always been fond of:

`if (myString==String.Empty)`

but it occured to me that this necessitates the creation and destruction of a second object (the empty string with which we’re comparing), so maybe it would be quicker to write:

`if (myString.Length==0)`

And looking through some existing code I also found examples of:

`if String.Equals(myString,String.Empty)`

I decided that an experiment was in order, so wrote a quick windows application to try each method in turn. I was also interested to see if there was a difference in performance where the result was true than when it was false.

Here are the results, with times in milliseconds for 50 million iterations:

| |true result|false result|
|-|-|-|
|`myString==String.Empty`|1172|2484|
|`myString.Length==0`|531|531|
|`String.Equals(myString,String.Empty)`|611|1893|


So there you have it. Experimental evidence that the fastest way to test for an empty string is to test whether it’s Length property is zero (and that this also takes exactly the same length of time irrespective of whether the result is true or false).. unless anyone knows of a quicker method? Of course, since we’re only saving ourselves around 50 nanoseconds per iteration against using the slowest method shown above, this is hardly going to result in a noticeable performance gain!!


 [1]: https://blog.iannelson.uk/string-isnullorempty/