---
title: Schoolboy Error Of The Day

date: 2011-08-17T08:08:00+00:00
url: /schoolboy-error-of-the-day/

categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

This dumb mistake just cost me an hour spelunking around in the debugger:

<pre><code class="language-clike">var status = source.Substring(source.LastIndexOf("/" + 1));  </code></pre>

(where source is e.g. &#8220;<http://foo.com/status/all-is-good>&#8220;)

Fortunately the ramifications were picked up in the acceptance tests, but the root cause wasn’t at all obvious from such a high level.

Lesson for the day &#8211; code is never too trivial to warrant unit testing.

<!--kg-card-end: html-->