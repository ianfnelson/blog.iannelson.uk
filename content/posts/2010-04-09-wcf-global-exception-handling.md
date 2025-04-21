---
title: WCF – Global Exception Handling
author: ian
type: post
date: 2010-04-09T13:04:00+00:00
url: /wcf-global-exception-handling/
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
I’ve done a fair bit of WCF development recently (and amazingly I came out of it relatively unscathed, both psychologically and emotionally). Using Castle Windsor’s WCF Facility helped a great deal, but I still found myself writing a fair bit of infrastructure and plumbing code. I thought I’d blog some of these code snippets lest I forget, and on the offchance they might help others.

One of the things I wanted to achieve was to ensure that any unhandled exceptions that propagated to the top of the stack were logged. The following custom EndpointBehavior achieves that. I’m using Castle Logging Facility here, but you could of course swap out the logging code for whatever error handling code you require.

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

Here&#8217;s the relevant line from my Windsor configuration:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->