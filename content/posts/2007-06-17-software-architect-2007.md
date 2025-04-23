---
title: Software Architect 2007

date: 2007-06-17T18:06:00+00:00
url: /software-architect-2007/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2007/06/iStock_000003326440XSmall-1.jpg

categories:
  - Tech

---
Last week I had the pleasure of spending a few days in London attending the [Software Architect 2007][1] conference at the Barbican centre. It was a good conference, providing me with some useful and interesting new ideas and food for thought, whilst confirming that our team at [Marshalls][2] are generally going about things in &#8220;the right way&#8221;, which is nice.

Looking through my notes, the main themes that kept recurring within the different presentations that I attended were:

  * Avoid coupling at all costs. Use interfaces, contracts and facades to decouple components. Avoid directly referencing vendor’s class libraries or infrastructure libraries.
  * Appreciate the impact of small decisions which can eventually have a big impact on the overall architecture.
  * Devote more time and consideration to designing interfaces, contracts and public APIs (which are difficulty to change retrospectively), than private implementations which are relatively simple to change.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000003326440XSmall.jpg" class="kg-image" alt="Agility" loading="lazy" /> </figure> 

These issues kept coming up again and again &#8211; most notably in talks by Kevlin Henney on &#8220;The Selfish Object&#8221; and Ralf Westphal on &#8220;True Component Orientation&#8221;, but also to an extent in some of Dave Wheeler’s demonstration of how to use some of the Gang of Four design patterns in .NET. So, it amazed me that a number of my fellow delegates kept raising their hands and asking questions which invariably began &#8220;Yeah, but why can’t I just&#8230;&#8221;, followed by suggestions which effectively seemed to boil down to creating hardcoded, inflexible solutions! To say that this was supposedly a conference of architects, even relatively simple concepts such as Reflection, Polymorphism and Generics seemed to be lost on some people, who apparently would be more comfortable maintaining massive switch statements for the rest of eternity!

This is one of the issues I have with the XP rules &#8211; I don’t believe that [doing the simplest thing that could possibly work][3] is a good idea, at least not when creating public APIs and interfaces. Some forethought is necessary in order to architect loosely coupled solutions that will allow continued flexibility and agility when faced with inevitable change requests. I’m not arguing for the [premature development of functionality that may never be required][4], but interfaces, APIs, inheritance models and database models are a right royal pain to change at a later date and in my experience, upfront design in these areas pays dividends.

Oh, my other issue with the XP rules is the notion of [collective code ownership][5] &#8211; I’m not precious about my code (honest), but there are inevitably areas of specialism (in terms of technology and business knowledge) in which I seek to focus my energies, and other areas that I don’t care for, or wish to maintain. We can’t all understand everything about every system, and it’s foolish to pretend that this is the case. Allowing or requiring an entire team to be comfortable maintaining the whole codebase is likely to prohibit anybody learning very much about anything, and even with rigorously enforced coding standards and comprehensive unit tests can lead to an unfortunate swiss cheese / patchwork quilt effect. All IMHO, of course.

My favourite session of the conference was by [Ralf Westphal][6], who clearly and concisely (his English is better than that of many native speakers!) explained the benefits of using Contract First Development and a microkernel approach to remove component dependencies and development bottlenecks. It’s an approach that I can’t wait to try.

One of the other things that pleased me about the conference was the realisation that we at Marshalls are (especially for such a stable, old-economy company), way ahead of the pack in terms of technology &#8211; whilst other delegates I spoke with are still using earlier versions of .NET, or even still on VB6 / Win32 API, we continue to make appropriate use of the latest offerings from Redmond.

A few other observations from my days in London:

  * Trying to change from the Circle to Piccadilly lines at King’s Cross at rush hour involves crossing a packed concourse buzzing with hardened commuters that brought to mind that Zurich insurance TV advert which shows futuristic cars on traffic signal-free intersections narrowly avoiding collisions thanks to automated guidance systems!
  * Unlike at MSDN events (where all speakers use vanilla installations of Vista/XP and search Windows Live using IE7), there’s a great variety of hardware and software in popular use now &#8211; I witnessed presentations on Dell, Sony Vaio, and MacBook (running both OS X and Vista, through BootCamp), with some highly-configured operating systems, and every presenter used Safari or Firefox &#8211; no IE in sight. Didn’t see any Ubuntu, mind.
  * Section 20 of the [Architect’s Act 1997][7] prohibits the use of the &#8220;Software Architect&#8221; job title. Curiously, &#8220;Golf Course Architect&#8221; is fine.
  * In all respects, central London is about as far removed from the Isle of Mull (where I was a week previously) as it’s possible to imagine. Increasingly so, it really does come across as a kind of city state, a world city, with a cosmopolitan feeling quite unlike anywhere else in the UK.

 [1]: http://www.software-architect.co.uk
 [2]: http://www.marshalls.co.uk
 [3]: http://www.extremeprogramming.org/rules/simple.html
 [4]: http://www.extremeprogramming.org/rules/early.html
 [5]: http://www.extremeprogramming.org/rules/collective.html
 [6]: http://www.ralfw.de
 [7]: http://www.opsi.gov.uk/ACTS/acts1997/97022--f.htm#20