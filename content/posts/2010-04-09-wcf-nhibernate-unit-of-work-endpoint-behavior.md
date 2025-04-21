---
title: WCF – NHibernate Unit Of Work Endpoint Behavior
author: ian
type: post
date: 2010-04-09T13:04:00+00:00
url: /wcf-nhibernate-unit-of-work-endpoint-behavior/
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
OK, my last WCF-related code snippet of the day, I promise. This is quite similar to the last one. I required that the WCF service I was developing started a new NHibernate Session for each invocation, and closed it after invocation (i.e. session-per-request). I couldn’t rely on the ASP.NET session start and end events in global.asax as this particular WCF service was to respond to MSMQ messages rather than HTTP.

So, once again I found myself bashing out a custom EndpointBehavior to add a custom CallContextInitializer to every operation:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

And the Windsor configuration is much the same as before:

<!--kg-card-begin: html-->

<!--kg-card-end: html-->