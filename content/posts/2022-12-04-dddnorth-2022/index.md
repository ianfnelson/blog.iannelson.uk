---
title: DDDNorth 2022

date: 2022-12-04T15:48:39+00:00
excerpt: "Notes from attending five sessions at this year's DDDNorth conference, at the University of Hull."
url: /dddnorth-2022/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2022/12/IMG_5627-1.jpg

categories:
  - Tech
tags:
  - Conferences

---
 

Yesterday morning I arose unusually early for a Saturday and drove eastwards to attend this year’s [DDDNorth][1] at the University of Hull. These free, community-driven events held at the weekend offer an invaluable opportunity to learn from peers in the industry in a relaxed environment.

Five concurrent sessions in each timeslot means that tough decisions often have to be made about which to attend! In acknowledgement of my maturing years (I’ve been reading up on [optimal stopping][2]) and the niche that I have carved out for myself, I chose to stick to those sessions that focused on backend and distributed architecture and development.

My choice for the first session of the day was an overview of **.NET Minimal APIs** by Microsoft MVP Kevin Smith ([@kev_bite][3]). Restful APIs on the Microsoft .NET platform frequently form a key part of the systems that I design and develop, so it’s vital to stay abreast of the latest techniques for implementing these. Kev’s session was really useful to me as it concisely demonstrated the approaches available in .NET Core 7 Minimal APIs, freeing me of the need to discover what’s new via reading documentation or other means. I particularly appreciated seeing demonstrations of approaches for the automated testing of APIs, and some of the post-session Q&A about how best to structure real-world enterprise .NET APIs was insightful.

![Kevin Smith is presenting in a lecture theatre](https://blogstouks01.z33.web.core.windows.net/2023/08/image.jpeg)
Kevin Smith demos how to test .NET Minimal APIs

I’ve blogged before about the [Inherent Negativity of Computer Programmers][4], and it’s fair to say that this pessimism hasn’t changed as my career has progressed! As an architect of distributed systems, knowledge of techniques for handling unavailable or poorly-performing dependencies are an essential part of my day-to-day toolset. Andy Clark’s ([@techychap][5]) entertaining session “**When Microservices Go Bad**” covered a variety of strategies such as caching, retries, timeouts, circuit breakers, bulkheads and rate limiting. For each of these, he showed how they can be achieved using the excellent open source library [Polly][6]. I’ve been using some of Polly’s features on my current project (I’ve been a long-time fan of [Circuit Breaker][7] since I first learned of it from reading Michael Nygard’s _[Release It!][8]_ book), but this session opened my eyes to the full gamut of how Polly could help protect the systems I design. Hat-tip to Andy for the live demos in this session, and for contending with the multi-monitor weirdness.

The third session was my favourite of the day. “**Don’t Put Your Messages In A Bottle: Implement Messaging Patterns**” saw [Azure Service Bus][9] Senior Program Manager Eldert Grootenboer ([@egrootenboer][10]) provide a whistle-stop overview of fourteen (fourteen!) separate messaging patterns. The Circuit Breaker pattern made another appearance, as did some patterns which were new to me such as Sequential Convoy and Transactional Outbox. I’ve been getting by with simply using Azure Storage Queues for most of my queueing requirements in recent years, but this presentation reminded me of the richer techniques that are possible with Service Bus. This hour-long session flew by and left me wanting more. Time to dust off my copy of [Hohpe and Woolf’s Enterprise Integration Patterns][11] and brush up ahead of my next distributed architecture challenge.

“**Software Architecture: In Search of the Fourth Chord**” by straight-speaking Paul Michaels ([@paul_michaels][12]) was a more laid-back session which covered many of the common problems and trade-offs faced by Software Architects. Paul rightly highlighted that the architect is likely the only person on a project who cares about the full range of functional and nonfunctional characteristics of a system. But I’m not sure that his throwaway comment “no-one ever says &#8216;can you make the system scale?'” is strictly true – I think this can depend on the project and sector. For example, a large part of my working life during the pandemic has involved ensuring that the NHS App and associated systems can scale to meet spikes in traffic, and here scalability and universal access are often of higher importance than, say, a richer feature set.

The session concluded by suggesting that, much as Status Quo have been able to have a successful musical career with a limited number of chords, so the average Software Architect can get a long way in their chosen career through judicious application of the Message Broker, Event Sourcing and CQRS patterns.

The final session I attended was “**SOA Lessons Learnt (or, Microservices Done Better)**“, where Sean Farmar ([@farmar][13]) gave an entertaining and often opinionated run through his  experiences developing and architecting distributed systems since the 1990s. The general premise was that while technologies and fashions may change over the years, the key thing is to avoid coupling at all costs – a theme which I remember noting from my attendance at [Software Architect 2007][14] fifteen years ago. It was also nice to be reminded of Peter Deutsch’s [Fallacies of Distributed Computing][15], which are even more relevant today than they were in the mid-90s.

Finally, before the dark and rainy drive home, it was time for goodbyes and the traditional prize draw. I’m delighted to report that I had the good fortune to win a [GitHub][16]-branded scarf which I shall wear with pride to protect my nesh self against the inclement Yorkshire winter that lies ahead.

Many thanks to all who presented, organised and sponsored this year’s DDDNorth. As ever, it was an enjoyable and productive way to spend a Saturday.

![A handsome forty-something software engineer models his new GitHub-branded scarf](https://blogstouks01.z33.web.core.windows.net/2023/08/image-1-scaled.jpeg)
Sporting my lovely new GitHub scarf

 [1]: https://dddnorth.co.uk/
 [2]: https://en.wikipedia.org/wiki/Optimal_stopping
 [3]: https://twitter.com/kev_bite
 [4]: https://blog.iannelson.uk/on-the-inherent-negativity-of-computer-programmers/
 [5]: https://twitter.com/TechyChap
 [6]: https://github.com/App-vNext/Polly
 [7]: https://blog.iannelson.uk/a-circuit-breaker-which-trips-on-frequency-of-failures/
 [8]: https://amzn.to/3VwRvwP
 [9]: https://azure.microsoft.com/en-gb/products/service-bus
 [10]: https://twitter.com/egrootenboer
 [11]: https://amzn.to/3Uu78Ee
 [12]: https://twitter.com/paul_michaels
 [13]: https://twitter.com/farmar
 [14]: https://blog.iannelson.uk/software-architect-2007/
 [15]: https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
 [16]: https://github.com/