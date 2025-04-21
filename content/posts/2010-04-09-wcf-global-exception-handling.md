---
title: WCF – Global Exception Handling

date: 2010-04-09T13:04:00+00:00
url: /wcf-global-exception-handling/

categories:
  - Tech
tags:
  - tidy

---
I’ve done a fair bit of WCF development recently (and amazingly I came out of it relatively unscathed, both psychologically and emotionally). Using Castle Windsor’s WCF Facility helped a great deal, but I still found myself writing a fair bit of infrastructure and plumbing code. I thought I’d blog some of these code snippets lest I forget, and on the offchance they might help others.

One of the things I wanted to achieve was to ensure that any unhandled exceptions that propagated to the top of the stack were logged. The following custom EndpointBehavior achieves that. I’m using Castle Logging Facility here, but you could of course swap out the logging code for whatever error handling code you require.

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

Here&#8217;s the relevant line from my Windsor configuration:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->