---
title: A LINQ Gotcha – First Operator

date: 2007-12-14T14:12:00+00:00
url: /a-linq-gotcha-first-operator/

categories:
  - Tech
tags:
  - .NET

---

So, I was using the `First` operator to return the first item element in a sequence matching a predicate.

I expected a null to be returned if the sequence did not contain any matching elements, but found (well, Scott found) that this actually throws an InvalidOperationException.

Turns out I should have been using the `FirstOrDefault` operator instead…