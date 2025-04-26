---
title: Star Of The Week

date: 2014-05-08T20:30:11+00:00
url: /star-of-the-week/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2014/05/iStock_000033567536Small.jpg

categories:
  - Work
  - Tech

---
As a lowly _sellsword_ amongst the ensemble cast that make up the incestuous York/Leeds IT scene, I am not usually one to be influenced by the promise of titles and honours.

Time was, long ago, in my first graduate job, that I yearned for a promotion from “Solution Developer” to “Development Specialist”. Now I give little consideration to what I’m called, and sell my services on the basis of what I can _do_, and the value I can bring to a project and an organisation.

So, imagine my surprise when I recently returned to my desk at a client site to find the certificate below resting on my keyboard. It seems my highborn masters had seen fit to dub me (with tongue firmly in cheek, I presume), as their “Star of the Week”!

![Star Of The Week Certificate](https://blogstouks01.z33.web.core.windows.net/2023/08/StarOfTheWeek.jpg)

What had I done to deserve this honour?

The client had an existing solution to generate an XML feed summarising the information held within a database. Unfortunately this process was slow – it took around 45 seconds – and even though the output was aggressively cached, this was still causing a problem.

I actually enjoy occasionally tackling problems like this, where there is an existing solution that meets all functional requirements and my task is simply to improve some nonfunctional requirement – make it faster, make it more maintainable, make it scalable, update the technology stack, etc. The goal is much clearer when you have a reference solution to mimic than when starting with a blank page and having to tease out acceptance criteria from fickle humans!

Unsurprisingly, some baseline profiling revealed that the problems lay in the data access layer, and with the help of Hibernating Rhino’s [Entity Framework Profiler][1], I was able to determine that over 35,000 separate database calls were being issued to create a file of a few megabytes.

This was possible because the data access was performed through a series of helper classes that wrapped the EF context and exposed mapped models. While this simplified the data access for most use cases, and helped to encapsulate low-level validation, it was a hindrance for any kind of aggregation or reporting requirement. Essentially the problem boiled down to the _SELECT N+1_ problem on steroids, with a large portion of the object graph steadily loaded into memory.

Wrapping isn’t always a helpful approach&#8230;

![](https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000033567536Small.jpg)

The answer, having first defined some automated integration tests based on the existing solution, was to avoid using the helpful wrapper/mapper classes and instead write some bespoke EF queries against the underlying data context. I tried to strike a balance between making as few queries as possible without becoming unmaintainable or requiring too many joins. And each query, rather than returning the entire entity, instead projected only the required properties into some anonymous types. A little in-memory post-processing then turned these projections into the desired output format.

The end result? A process that originally made over 35,000 database queries and took 45 seconds was reduced to one that required just 7 queries and completed in around 0.45 seconds. Nice.

 [1]: http://www.hibernatingrhinos.com/products/efprof
