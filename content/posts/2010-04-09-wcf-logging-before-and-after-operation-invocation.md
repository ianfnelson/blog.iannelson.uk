---
title: WCF – Logging Before and After Operation Invocation

date: 2010-04-09T13:04:00+00:00
url: /wcf-logging-before-and-after-operation-invocation/

categories:
  - Tech
tags:
  - .NET
  - WCF

---
Here’s another custom WCF EndpointBehavior I found useful recently.

Not content with [logging all unhandled errors][1], I wanted to output a DEBUG level log message before and after every operation invocation. As before, I’m using the Castle Windsor Logging Facility to handle my logging, but you can swap that out for your logger of choice if required.

Firstly, here’s the EndPointBehaviour itself. This adds a custom CallContextInitializer to every service operation:

{{< gist 51d9f1a223bc6984b905 WCFLog_1.cs >}}

Here’s the custom CallContextInitializer:

{{< gist 51d9f1a223bc6984b905 WCFLog_2.cs >}}

And the Windsor configuration is much the same as last time:

{{< gist 51d9f1a223bc6984b905 WCFLog_3.cs >}}

 [1]: https://blog.iannelson.uk/wcf-global-exception-handling/