---
title: WCF – NHibernate Unit Of Work Endpoint Behavior

date: 2010-04-09T13:04:00+00:00
url: /wcf-nhibernate-unit-of-work-endpoint-behavior/

categories:
  - Tech
tags:
  - .NET
  - WCF
  - NHibernate

---
OK, my last WCF-related code snippet of the day, I promise. This is quite similar to the last one. I required that the WCF service I was developing started a new NHibernate Session for each invocation, and closed it after invocation (i.e. session-per-request). I couldn’t rely on the ASP.NET session start and end events in global.asax as this particular WCF service was to respond to MSMQ messages rather than HTTP.

So, once again I found myself bashing out a custom `EndpointBehavior` to add a custom `CallContextInitializer` to every operation:

{{< gist 2f0f9300f5157c320dbd WCFNH_1.cs >}}

{{< gist 2f0f9300f5157c320dbd WCFNH_2.cs >}}

And the Windsor configuration is much the same as before:

{{< gist 2f0f9300f5157c320dbd WCFNH_3.cs >}}
