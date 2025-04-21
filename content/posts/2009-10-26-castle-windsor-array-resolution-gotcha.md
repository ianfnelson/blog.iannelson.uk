---
title: Castle Windsor Array Resolution Gotcha

date: 2009-10-26T10:10:00+00:00
url: /castle-windsor-array-resolution-gotcha/

categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

The shiny new system which I’ve recently been developing makes heavy use of the Chain of Responsibility pattern, and as such a number of service classes take an array of objects in the constructor:



I’m using Castle Windsor for dependency management, so I’ve been fluently registering all instances of ILeadAllocator:



Easy, right? And yet at runtime Windsor surprised me by throwing this exception in my face:

> Castle.MicroKernel.Handlers.HandlerException: Can’t create component &#8216;Marshalls.Leads.ApplicationService.LeadAllocationService’ as it has dependencies to be satisfied.
> 
> Marshalls.Leads.ApplicationService.LeadAllocationService is waiting for the following dependencies:
> 
> Keys (components with specific keys)
> 
> &#8211; leadAllocators which was not registered.

Huh?! What gives? Well, a little Googling revealed [this post][1] from Castle founder Hamilton Verissimo explaining that by default the Castle MicroKernel expects me to define what should be included in the array. But he goes on to explain that the behaviour I desire can be achieved by registering a custom subresolver with the microkernel. That subresolver has since been included in the Castle Windsor distro, so in actual fact all I needed to do was add the following line of code when configuring my container:



So now, when new implementations of ILeadAllocator are added to the codebase, they are immediately available to the CofR pattern within the LeadAllocationService, with no additional work required by the developer. Hurrah!

<!--kg-card-end: html-->

 [1]: http://hammett.castleproject.org/?p=257