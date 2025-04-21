---
title: A LINQ Gotcha – First Operator
author: ian
type: post
date: 2007-12-14T14:12:00+00:00
url: /a-linq-gotcha-first-operator/
ct_author_pro_video_display_key:
  - post
ct_author_pro_fi_size_key:
  - default
ct_author_last_updated:
  - default
categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

<p class="MsoNormal">
  So, I was using the <a  href="http://www.hookedonlinq.com/Default.aspx?Page=FirstOperator">First operator</a> to return the first item element in a sequence matching a predicate.
</p>

<p class="MsoNormal">
  I expected a null to be returned if the sequence did not contain any matching elements, but found (well, Scott found) that this actually throws an InvalidOperationException.
</p>

<p class="MsoNormal">
  Turns out I should have been using the <a  href="http://www.hookedonlinq.com/FirstOrDefaultOperator.ashx">FirstOrDefault</a> operator instead&#8230;
</p>

<!--kg-card-end: html-->