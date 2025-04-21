---
title: 'Is My String Empty?  Some C# Performance Metrics'

date: 2004-07-30T10:07:00+00:00
url: /is-my-string-empty-some-c-performance-metrics/

categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

**Update (25/02/2006)** &#8211; Hey, we now have [String.IsNullOrEmpty][1], you know!

* * *

What&#8217;s the quickest way, in C#, to test whether a string is empty?&nbsp; This is a question which came to my mind yesterday. I&#8217;ve always been fond of:

<pre>&lt;cdode class="language-clike">if (myString==String.Empty)  &lt;/code></pre>

but it occured to me that this necessitates the creation and destruction of a second object (the empty string with which we&#8217;re comparing), so maybe it would be quicker to write:

<pre>&lt;cdode class="language-clike">if (myString.Length==0)  &lt;/code></pre>

And looking through some existing code I also found examples of:

<pre>&lt;cdode class="language-clike">if String.Equals(myString,String.Empty)  &lt;/code></pre>

I decided that an experiment was in order, so wrote a quick windows application to try each method in turn. I was also interested to see if there was a difference in performance where the result was true than when it was false.

Here are the results, with times in milliseconds for 50 million iterations:

<table cellspacing="2" cellpadding="2">
  <tr>
    <td>
      &nbsp;
    </td>
    
    <td align="right">
      true result
    </td>
    
    <td align="right">
      false result
    </td>
  </tr>
  
  <tr>
    <td>
      myString==String.Empty
    </td>
    
    <td align="right">
      1172
    </td>
    
    <td align="right">
      2484
    </td>
  </tr>
  
  <tr>
    <td>
      myString.Length==0
    </td>
    
    <td align="right">
      531
    </td>
    
    <td align="right">
      531
    </td>
  </tr>
  
  <tr>
    <td>
      String.Equals(myString,String.Empty)
    </td>
    
    <td align="right">
      611
    </td>
    
    <td align="right">
      1893
    </td>
  </tr>
</table>

&nbsp;

So there you have it. Experimental evidence that the fastest way to test for an empty string is to test whether it&#8217;s Length property is zero (and that this also takes exactly the same length of time irrespective of whether the result is true or false).. unless anyone knows of a quicker method? Of course, since we&#8217;re only saving ourselves around 50 nanoseconds per iteration against using the slowest method shown above, this is hardly going to result in a noticeable performance gain!!

<!--kg-card-end: html-->

 [1]: https://blog.iannelson.uk/string-isnullorempty/