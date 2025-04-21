---
title: Castle Windsor Lifestyle Gotcha

date: 2009-10-19T05:10:00+00:00
url: /castle-windsor-lifestyle-gotcha/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2009/10/iStock_000000942732XSmall_2-1.jpg

categories:
  - Tech
tags:
  - tidy

---
I always knew my lifestyle choices would come back to bite me some day…<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/iStock_000000942732XSmall_2.jpg" class="kg-image" alt loading="lazy" /> </figure> 

I’ve been making heavy use of the [Castle Windsor][1] container to handle dependency and configuration management in the shiny new system that I’m currently developing. For the most part it’s been an absolute blast, allowing me to easily create a loosely-coupled system architecture and focus my efforts on what the system should be achieving for the client, rather than worrying about how it all hangs together.

But recently I encountered a bit of a gotcha which made me think that perhaps I should spend some more time understanding exactly what Windsor is doing in the background.

See, it turns out that the default lifestyle for components registered with Windsor is Singleton. So, every time I asked Windsor for an IFooRepository, it supplied me with _exactly the same concrete instance of FooRepository_. Which would have been fine if it weren’t for the fact that FooRepository happened to indirectly hold a private reference to a thread-afine NHibernate session context. Ouchy.

The system I’m developing is a WCF service, and I’m using a Unit of Work pattern to open an NH session before the operation is invoked, and close it afterwards. To make this work, I simply needed to make sure that FooRepository (and any Castle-fulfilled component which has an IFooRepository dependency) has a transient lifestyle. Indeed, on further reflection, for most of the systems I develop, the transient lifestyles should be my default choice, and I do wonder why the Windsor developers chose to make singleton the default.

Davy Brion has more info on this topic in this blog post – [Windsor and Component Instance Lifetimes][2].

So, moral of the story – understand how your IoC container is fulfilling your requests, and be prepared to specify non-default behaviours if necessary. Convention over configuration is only a benefit if you’re happy with the conventions.

 [1]: http://www.castleproject.org/container/index.html
 [2]: http://davybrion.com/blog/2008/05/windsor-and-component-instance-lifetimes/