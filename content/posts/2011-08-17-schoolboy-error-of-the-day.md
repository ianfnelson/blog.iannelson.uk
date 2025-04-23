---
title: Schoolboy Error Of The Day
date: 2011-08-17T08:08:00+00:00
url: /schoolboy-error-of-the-day/
categories:
  - Tech

---

This dumb mistake just cost me an hour spelunking around in the debugger:

`var status = source.Substring(source.LastIndexOf("/" + 1));`

(where source is e.g. “<http://foo.com/status/all-is-good>“)

Fortunately the ramifications were picked up in the acceptance tests, but the root cause wasn’t at all obvious from such a high level.

Lesson for the day – code is never too trivial to warrant unit testing.
