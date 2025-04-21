---
title: A Circuit Breaker Which Trips On Frequency Of Failures
author: ian
type: post
date: 2009-10-28T11:10:00+00:00
url: /a-circuit-breaker-which-trips-on-frequency-of-failures/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2009/10/iStock_000010551634XSmall_3-1.jpg
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
[@Jez][1] [tweeted][2] last night:<figure class="kg-card kg-embed-card"> 

<blockquote class="twitter-tweet">
  <p lang="en" dir="ltr">
    <a href="https://twitter.com/ianfnelson?ref_src=twsrc%5Etfw">@ianfnelson</a> admit it: you use Castle Windsor primarily to highlight and lampoon Google's poor selection of adwords?!
  </p>
  
  <p>
    &mdash; 𝚂𝚑𝚘𝚘𝚝𝚒𝚗𝚐 𝚂𝚌𝚒𝚕𝚕𝚢 (@shootingscilly) <a href="https://twitter.com/shootingscilly/status/5186129382?ref_src=twsrc%5Etfw">October 26, 2009</a>
  </p>
</blockquote>

</figure> 

Funny, but not true. I am enamoured with the [Castle Windsor][3] project because its power makes it fairly simple for me to develop loosely-coupled systems which are easily maintained and tested. The wide range of Facilities and Contrib projects also integrate nicely with the other parts of my current development stack (NHibernate, WCF, WF, log4net).

Whilst there is a lot of material on the web about the Dependency Injection capabilities of Windsor, the Aspect-Oriented Programming (AOP) features don’t seem to get as much exposure, so I thought I’d quickly blog about one way in which I’ve been making use of those in the system I’m currently developing.

Earlier this year [Davy Brion][4] posted [an excellent C# implementation][5] of the Circuit Breaker pattern described in Michael Nygard’s equally excellent book _[Release It! Design and Deploy Production-Ready Software][6]_.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/iStock_000010551634XSmall_3.jpg" class="kg-image" alt loading="lazy" /> </figure> 

For the uninitiated, this pattern advocates protecting your system from issues affecting any remote service on which it depends by wrapping your calls to that service with a circuit breaker component. This component notes any failed service invocations, until some threshold is reached, causing the circuit to trip. Subsequent attempted service invocations then “fail fast”, throwing a custom exception rather than passing the method call on to the remote service. This benefits your system, as it prevents you from tying up valuable threads creating expensive remote service calls which may be slow to timeout. And it benefits the remote system as you avoid piling further pressure on a service which is already down or unresponsive.

For more details of this pattern, and some entertaining war stories of situations in which they would have proved useful, I encourage you to read [Michael Nygard’s book][6].

Now, I like Davy’s implementation of this pattern a lot, particularly since it is implemented as an interceptor for Castle Windsor, which as mentioned I’m already making heavy use of in my current projects. But my only concern is that it is configured to trip after the number of failed invocations reaches a specific figure, _irrespective of how long it takes to reach that threshold_. I want an implementation which is able to sense the difference between infrequent exceptions over a prolonged period, and a sudden flurry of exceptions – the latter causing the circuit breaker to trip.

To achieve this I’ve tweaked Davy’s implementation slightly by adding an extra parameter to the constructor specifying the historical period over which to total the number of exceptions. That is, you can configure it such that a certain number of failures _within the preceding y minutes_ causes the circuit breaker to trip.

My forked version can be found on GitHub at <https://github.com/ianfnelson/CircuitBreaker>.

I look forward to seeing what adverts Google sees fit to stick at the bottom of this post… 🙂

 [1]: http://twitter.com/jeremypearson
 [2]: http://twitter.com/jeremypearson/statuses/5186129382
 [3]: http://www.castleproject.org/container/index.html
 [4]: http://davybrion.com
 [5]: http://davybrion.com/blog/2009/07/protecting-your-application-from-remote-problems/
 [6]: http://www.amazon.co.uk/gp/product/0978739213?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=19450&creativeASIN=0978739213