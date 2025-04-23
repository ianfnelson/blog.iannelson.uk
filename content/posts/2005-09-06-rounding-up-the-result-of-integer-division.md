---
title: Rounding Up The Result of Integer Division

date: 2005-09-06T11:09:00+00:00
url: /rounding-up-the-result-of-integer-division/

categories:
  - Tech
tags:
  - tidy

---
Here’s a damn useful piece of information which should be in the armoury of every modern codemonkey:

> In Java, if it is required to round up the result of dividing `m` by `n` (where `m` and `n` are integers), one should compute `(m+n-1)/n`

Source: [Number Conversion, Roland Backhouse, 2001](http://www.cs.nott.ac.uk/%7Ercb/G51MPC/slides/NumberLogic.pdf)

I’ve used this deliciously elegant result in production J2EE code in the past, but it’s equally valid in C#, _as long as you can make the additional assertion that m/n is positive_. This is because whilst Java treats integer division by rounding to zero, [C# merely truncates the result][1] (in an unchecked context). In my experience, the most frequentuse for this result is the deft answering of questions such as &#8220;if I have x items in my dataset and I display y per page, how many pages do I have in total?&#8221;, where it is obviously safe to make the assertion of a positive result.

 [1]: http://msdn2.microsoft.com/library/6a71f45d%28en-us,vs.80%29.aspx