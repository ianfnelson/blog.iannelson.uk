---
title: 'Enterprise Integration Anti-Patterns #2 – Shared Assemblies'

date: 2010-12-01T10:12:00+00:00
url: /enterprise-integration-anti-patterns-2-shared-assemblies/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2010/12/iStock_000004248715XSmall_3-1.jpg

categories:
  - Tech
tags:
  - Architecture

---
Having slain the beast that is [Shared Database][1], the next dragon to appear on my Enterprise Integration horizon is Shared Assemblies. That is, the suggestion that Application A can leverage the functionality of Application B by simply adding references to B’s DLLs. After all, this potential for reuse is why we put our code in reusable assemblies in the first place, isn’t it..?!

![](https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000012931845XSmall_3.jpg)

Well, no. Actually we usually break our application apart into assemblies to create a maintainable and testable architecture. An assembly is a coarse-grained unit of encapsulated functionality in that architecture; the fact that it is the smallest deployable unit in the .NET world is not necessarily an indication that we intend or desire our assemblies to be shared with other applications.

In my experience, sharing assemblies works only when they have been developed with this intention in mind. It’s feasible to share DLLs that contain discrete chunks of easily-encapsulated functionality that have no need for external dependencies (hasn’t every dev shop got a “common” or “utilities” library hanging around somewhere?!) but it’s quite another matter to start taking a wholesale dependency on the guts of another application.

So, before you try the shared assemblies approach to enterprise integration, here are a few things to consider:

## Is It Even Possible? 

Firstly, this approach makes the assumption that the application to be referenced has been developed such that all the logic to be invoked exists in the assemblies. If the application wasn’t originally developed with the intention of being shared in this way, there’s every possibility that some pertinent logic has instead been located in the front-end (e.g. the [“Magic Pushbutton”][2] anti-pattern that was so prevalent in ASP.NET Web Forms development), or even client-side scripts.

## Love Me, Love My Dependencies… 

All applications have dependencies of one kind or another. If you’re lucky, this will just be the .NET Framework, and if you’re especially lucky it will be the same version that is used by the consuming application.

More likely, the application being referenced will depend on a whole bunch of third-party DLLs, and now they’ve suddenly become your dependencies, too! If your dev shop is anything like the places I’ve worked, each application will depend on various different versions of the NHibernate and Castle stacks and their associated dependencies. Good luck managing all those references while retaining your sanity.

## Applications are more than just DLLs 

The average enterprise application is more than just a bunch of assemblies that can be referenced independently. They also tend to rely on configuration settings, external resources (e.g. databases), and a whole bunch of stuff triggered at application start-up time such as the configuration of an IoC container, logging, ORM, etc. The handling of authentication and authorization might also need rethinking before assembly sharing becomes a viable option.

## Maintaining the Combined Suite of Applications 

As I said in [my previous post on this topic][1], maintainability is a particular bugbear of mine as a developer, and sharing assemblies across multiple applications doesn’t help matters one iota.

Unless you work with unbearably large solutions containing every project in your suite of applications, it’s difficult to know the wider impact that modifications will have, and to avoid making breaking changes. For sure, it’s possible to run automated builds of all applications when shared code is changed (I blogged about one method of achieving this with the first version of Team Foundation Server some years ago before I came to the conclusion that this is A Bad Idea) but by then the hard work has been done, the code checked in and the damage done.

Arguably, sharing assemblies puts developers in an even stickier situation than sharing databases – at least with that anti-pattern the entanglement is limited to one particular layer of the architecture which can be largely ignored much of the time. But when assemblies are shared, the developers must always be considering whether their apparently innocent modifications will have an impact on some other application. Meaningful refactoring becomes impossible, and the software eventually falls into disrepair.

![](https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000004248715XSmall_3.jpg)

## In Conclusion…

When all is said and done, there are only two realistic patterns for sharing functionality between enterprise applications – remote procedure invocation and messaging. Both serve to decouple the applications, and both are easy to achieve with popular technologies on the .NET stack such as [WCF][3], [OpenRasta][4] and [MassTransit][5].

There’s an abundance of resources out there detailing how to create effective service-oriented architectures, the obvious canonical reference tome being Hohpe and Woolf’s [_Enterprise Integration Patterns_][6]. I also highly recommend Michael Nygard’s [_Release It!_][7] for an entertaining overview of some of the problems that can be encountered when you start taking dependencies on remote services, and useful patterns for ensuring your application remains responsive at all times.

My preferred technology stack for application integration remains WCF, and in a future blog post I’ll outline some tips I’ve learned through trial and error for developing and consuming effective and maintainable WCF services.

 [1]: https://blog.iannelson.uk/enterprise-integration-anti-patterns-1-the-shared-database/
 [2]: http://en.wikipedia.org/wiki/Magic_pushbutton
 [3]: http://msdn.microsoft.com/en-us/netframework/aa663324.aspx
 [4]: http://trac.caffeine-it.com/openrasta
 [5]: http://masstransit-project.com/
 [6]: http://amzn.to/gkOq3C
 [7]: http://amzn.to/h9NVFK