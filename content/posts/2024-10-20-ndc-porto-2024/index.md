---
title: NDC Porto 2024

date: 2024-10-20T22:09:29+00:00
excerpt: |
  |
    In October 2024 I had the pleasure of attending the NDC Porto 2024 conference for Software Developers. Here are my notes from that week, including details of my ten favourite conference sessions.
url: /ndc-porto-2024/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7606-scaled.jpeg

categories:
  - Tech
  - Travel
tags:
  - Conferences

---
I had the pleasure of spending ISO Week 42 in the beautiful Portuguese coastal city of Porto, attending the NDC Porto 2024 conference for software developers by [NDC Conferences][1].

It’s been a long time since I attended a multi-day conference – perhaps even as long ago as [Software Architect 2007][2] (where I first learned about Dependency Injection and IOC Containers) which makes me feel quite ancient. Having been a freelancer since 2008, it’s often difficult to justify taking time out to attend conferences, no matter how valuable they might be to one’s career in the longer term. The face cost of the conference ticket is usually dwarfed by the loss of contract income (real or perceived) whilst being unable to bill a client.

But circumstances conspired to make my attendance at NDC Porto possible this year. Firstly, I’m currently doing some exclusive and inside IR35 work for a client, which effectively results in me having some mandatory days off to play with for the first time in over 15 years. And secondly, I was lucky enough to win an all-access pass to any NDC Conference at a raffle held at the last [DDD North][3] event this March – so many thanks to the good folk at [Black Marble][4] for organising that event, and to [NDC][5] for offering the prize.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7645-1.jpeg)

I had never been to Porto before, so took the opportunity to spend the weekend prior to the conference doing the tourist thing. The October weather was fantastic for walking around the historic city centre, taking in the cathedral, Torre dos Clérigos, and views of the Duoro river. My goodness, but it’s hilly though!

From my journal that Sunday:

> “I realised that Porto doesn’t just appeal to my sense of sight. Of course the views are fantastic, but on a sunny Sunday like today there is also excellent music that carries far and wide from a range of talented buskers. Electric acoustic guitars and electric violins seemed to be the order of the day, with a mixture of classic and popular tunes. Porto also smells nice – people seem to have a variety of different fragrances that differ from those that I usually smell in Leeds. Of course there are great tastes in the form of the wines and seafood. And finally there are even things to touch – ceramic tiles, cork panels etc. Truly, this city is a feast for the senses.”

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7417.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7427.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7438.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7462.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7478.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7498.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7508.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7514.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7549.jpeg)

## Workshop – Designing Microservices

Before the conference proper began on Wednesday, there were nine two-day workshops to choose from. I opted to attend _Designing Microservices_ by [Sam Newman][15]. I had previously read Sam’s book _[Building Microservices][16]_, and have been using microservices of some variety or other on projects since 2018. While these have sometimes been successful, I have often had the niggling doubt that some implementations on which I have worked could more accurately be described as being Distributed Monoliths, and I was eager to spend some focused time understanding when the lure of microservices should be resisted, and to dig into implementation patterns, along with examining related topics such as whether to use multirepo or monorepo approaches for source control.

As with Sam’s book, while ostensibly about microservices, the workshop also covered a wide range of more general architectural and software development topics that could be equally applied to traditional monoliths. It also struck a good balance between technical topics and organisational ones – how to structure teams for success when delivering a microservice-based solution. I appreciated this holistic coverage, as well as the tacit admission that microservice architectures may often not be the correct solution for a given project.

The workshop was delivered at a good pace, neither labouring points unnecessarily, nor glossing over more thorny topics that were worthy of due consideration. There was a good mixture of slides, dialogue, and some collaborative activity in small groups.

My only minor disappointment with the two-day workshop was a sense that a small minority of the other attendees were insufficiently engaged – returning late to the workshop room from our plentiful breaks, and checking their phones frequently. I assume they were attending at the behest of their employer rather than of their own volition, but this behaviour seemed disrespectful to Sam and the other attendees. I tried to ignore it.

## My 10 Favourite Sessions

After the initial two days of workshops, the remaining three days were filled with over a hundred traditional one-hour sessions, with up to six sessions running concurrently. This led to sometimes difficult decisions about which sessions to attend. My strategy was generally to attend sessions covering higher-level broad-brush type topics, rather than those covering niche technologies which I could learn through reading online documentation. But even within these self-imposed guidelines, there was a wealth of material to choose from. I attended around twenty sessions – here are some thoughts on my favourite ten:

### Keynote: Tidy First? A Daily Exercise in Empirical Design by Kent Beck

The conference proper opened on Wednesday morning with a Keynote by Kent Beck, the creator of extreme programming, early proponent of Test-Driven Development, and one of the 17 original signatories to the Agile Manifesto. Like all the keynotes, this took place in the huge main expo hall of the conference. I can see the logistical logic behind this decision – notably that it is large enough to house all of the delegates, and ensures that the conference can kick off at 9am sharp, even if latecomers are still arriving. But on the downside there were no seats close to the stage area (I am 48 years old, the prospect of standing up for an hour didn’t appeal), whereas from the area with seats it was a struggle to hear Kent over the background chatter and espresso machines. I would learn from my mistakes and prop myself up on a table near the front for the following days’ keynotes.

My geriatric grumblings notwithstanding, from the portions I heard properly, this was a great talk, and I look forward to rewatching this on YouTube to fill in the gaps. Unlike every other session that I saw during the week, Kent did not have a traditional slide deck, but instead projected some freeform sketches to illustrate the concepts he discussed.

There was much talk about the perennial topics (and personal bugbears) of estimation, and the cost of software development, and how software designers can influence when money is spent and earned. The concept of optionality was introduced – if software can be changed, then the design does not matter. Features are easy to see, but options are difficult to see, yet this is why we invest in software. The cost of software is the cost of changing it, not the cost of building it. Some changes are surprisingly expensive, yet others are surprisingly cheap.

Some of my favourites quotes from the session (of which there were many, some of which would appear in the slides of other speakers later in the week):

- “Why can’t you estimate how long it will take to walk across a minefield?”
- “Software should grow like a tree grows.”
- “You can ignore the constraints, but the constraints are not going to ignore you.”
- “I am delighted when the next generation surpasses me.”

Kent wrapped up with a few words on this year’s hot topic of AI. He drew parallels with the development of highly efficient steam engines during the Industrial Revolution, and explained how this had actually led to an increase in the use of coal (the Jevon’s Paradox). He offered that the AIs are not coming for our jobs any time soon and that we are, in fact entering a new golden age for programming. This topic would crop up again throughout the conference.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7607.jpeg)

### Being Staff Plus by Ian Cooper

Having now notched up 27 years at the code face, I have recently been giving some considerations as to where to take my career in the coming years, without having to sell my soul to the devil and venture over to the dark side of management. This session from Ian Cooper on “Staff Plus” roles offered some great advice on the nature of senior technical leadership roles, and how to “move beyond code” while staying resolutely technical.

Ian offered a good balance of high-level strategic career advice married with a bunch of helpful tactical hints and tips for how to succeed (and demonstrate that success) in such roles, and I urge any other greybeards feeling frustrated with their careers to watch this presentation ([the version from NDC Oslo is online here][17]).

This was the first session that sent me scurrying to Amazon to buy some recommended books (it would not be the last!). By the time I got home to England on Saturday both _[T][18][he Staff Engineer’s Path: A Guide for Individual Contributors Navigating Growth and Change][19]_ by Tanya Reilly and _[Staff Engineer: Leadership Beyond the Management Track][20]_ by Will Larson would be waiting for me.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/Image-20-10-2024-at-16.36-5.jpeg)

### Definition Of Insanity – Timeouts, retries, and idempotency by Sam Newman

This session by Sam Newman focused on some of key techniques for developing resilient distributed systems: Timing out remote calls that do not complete in a timely fashion, Retrying unsuccessful calls, and how to achieve idempotency to ensure that calls can be retried safely without undesirable side-effects.

This topic is highly relevant to a distributed system that I am developing for my current client, so I listened intently and appreciated the detailed low-level advice. I was particularly interested in the observation that _if a retry of an idempotent request succeeds, we should send back the same semantic response that we would have sent had the original request succeeded_. Also new to me was the concept of a [Bloom Filter][21].

Improving the resilience of distributed systems has been an interest of mine since reading the first edition of _[Release It!][22]_ by Michael Nygard in 2009. I’m delighted to see that Sam is currently authoring [a new book on this topic][23], due for publication in 2025.

### Open Source, Open Mind: The Cost of Free Software by Dylan Beattie

A light-hearted talk to end the first day of the conference, this session by Dylan Beattie was a whistle-stop tour of the history of open source software, covering notable successes, failures and lawsuits, followed by some thoughts on where “free software” goes from here.

A recording of [an earlier version of this talk from NDC Oslo 2024 is available online][24], but Dylan had added extra material to the talk since then to cover the recent disputes between WordPress.com owners Automattic and WP Engine.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7630.jpeg)

### Keynote: Can you trust your (large language) model? by Jodie Burchell

Thursday’s keynote by data scientist Jodie Burchell talked about how the quality of Large Language Models (LLMs) such as ChatGPT has been measured, and highlighted structural deficiencies with both the benchmarks as well as the AI tooling themselves. I confess to not having devoted much time over the past year to understanding the “AI revolution”, so did not know what to expect from this talk, but I found it a fascinating and highly approachable explanation that has piqued my interest. My contemporary notes from this session read “Such a good talk. Chase down the slides, and sessions from [earlier][25] [NDCs][26]“.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/Image-20-10-2024-at-16.36-1024x768.jpeg)

### Orchestration vs. Choreography: The good, the bad, and the trade-offs by Laïla Bougriâ

Designing distributed systems regularly involves trying to decide between synchronous or asynchronous communication, and orchestration or choreography (and the combinations thereof). There are, of course, tradeoffs to make, but the design decisions are often made when considering only the happy path scenarios.

This excellent talk by Laïla Bougriâ took this complex nuanced subject, with all of its “it depends” messiness, and offered concrete guidance for when and how to implement each approach. One of my favourite sessions of the whole conference, and Laïla coped excellently with audio problems for the first third of the presentation.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/Image-20-10-2024-at-16.27-2-1024x768.jpeg)

### A Developer Goes to the Movies by Simon Painter

Thursday, the middle day of the conference proper, was a long one, but fortunately there were some great light-hearted talks later in the day to balance those that required more intense thinking.

I had previously enjoyed seeing Simon Painter give his talk “From Ancient Greeks to Modern Geeks: Basic Machine Learning Algorithms” at DDD North in Hull in March 2024. For this new talk, he brings together his twin passions of movies and coding by presenting a visual history of computing and software developers as seen by Hollywood.

I don’t seem to have made as many notes on this talk, preferring to relax and enjoy the show (though sadly without popcorn), but I do recall enjoying the segments on [WarGames][27], [The Net][28] and [Hackers][29] (which I really must watch again soon). It was also intriguing to learn that the distinction for the first person to have portrayed a computer hacker in a movie goes to none other than Benny Hill!

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7647.jpeg)

### How Simple Is “As Simple As Possible”? by Rendle

Rendle has been doing this programming lark for even longer than me. But unlike me (who merely grumbles about our industry through the medium of Instagram memes shared with equally bitter colleagues), Rendle is an ex-professional standup comic who takes the grumbling to a whole new level by holding up a (black) mirror to our industry in conference presentations such as this one.

The thing is, as the saying goes, _it’s funny because it’s true_. Rendle is on a mission to highlight how unnecessarily complex we have made most aspects of software design, development and deployment during his career, and proselytise for an easier, simpler and more productive life. Amen to that.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7650.jpeg)

### Keynote: Start Here: Mindset Shifts and Tools for Building Career Confidence in a Post-Pandemic Era by Denise Jacobs

For Friday’s final keynote of the conference, I took my now-customary standing spot up front near the stage… and then immediately regretted it as I noticed the pens and paper dotted around the tables. I realised with horror that this was going to be an interactive session, and considered retreating to the back of the room. I do not generally enjoy audience participation, have no “fun facts” on hand to share about myself, and abhor “icebreakers” at the start of meetings and workshops.

But, I told myself that I had come all this way to Porto with the intention of adopting a growth mindset and learning as much as possible, so ought to give it a go. I’m glad I did, as Denise’s talk became one of my favourite of the conference, and the audience participation exercises (which were not as scary as I had feared) helped to boost my confidence and further renew my interest in my career.

I ordered yet another book recommendation on the back of this talk – _[Chatter: The Voice in Our Head and How to Harness It][30]_ by Ethan Kross, but opted for Audible this time to reduce the number of Amazon packages that would be arriving at home in my absence.

![](https://blogstouks01.z33.web.core.windows.net/2024/10/Image-20-10-2024-at-16.25-4.jpeg)

### The Next Decade of Software Development by Richard Campbell

Richard Campbell is best known to me as the co-host of the [.NET Rocks!][31] podcast, but his interest and expertise in science, computing, and technology is far broader than that niche (he gave another talk at this conference on the topic of Nuclear Power).

This talk on the Next Decade of Software Development has been presented many times over the years and been regularly updated as new trends such as the Cloud emerge and gradually become mainstream. It reviews where we’ve been, examines the trend lines, and looks forward to which trends and technologies we will need to learn to remain relevant in our roles in the upcoming years. As with many of the other talks, this naturally touched on AI, and joined that consensus that we are entering a period where the LLMs will aid our software development work rather than directly threatening it. At a more prosaic level, Richard was also positive that .NET and Blazor are not going anywhere any time soon.

## Final Thoughts

I thoroughly enjoyed my time at NDC Porto. The conference is expertly organised by a team who have clearly been doing this for quite some time. The venue – [a former customshouse on the banks of the Duoro][32] – was airy and inspirational. The complementary food and drink was delicious and plentiful. The speakers were knowledgeable and friendly, making themselves available for questions outside of the sessions themselves. Generally I found my fellow attendees to be amiable and approachable, and appreciated mingling amongst the wide variety of nationalities present from across the European continent and further afield. I remain disheartened by the male skew in the gender balance of attendees at tech conferences, but it was pleasing to note how many (excellent) female speakers gave talks – I suspect and hope that NDC are doing all they reasonably can to improve diversity.

I return home to Yorkshire, and back to the code face, with a renewed enthusiasm for my chosen career and a rekindled excitement for technologies (both new and old – some of the talks by Anders Norås have made me nostalgic for my Amiga 500 and 1200!). Oh, and with an ever-growing pile of books to read!

![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7578.jpeg)
![](https://blogstouks01.z33.web.core.windows.net/2024/10/IMG_7673.png)

 [1]: https://ndcconferences.com/
 [2]: https://blog.iannelson.uk/software-architect-2007/
 [3]: https://www.dddnorth.co.uk
 [4]: https://blackmarble.com
 [5]: https://ndcconferences.com
 [15]: https://samnewman.io
 [16]: https://amzn.to/3UgfVME
 [17]: https://youtu.be/l-oCDQGH3EU?si=nAIK3UqvDUhQPZpl
 [18]: https://amzn.to/3YtNpcY
 [19]: https://amzn.to/3NxVNlu
 [20]: https://amzn.to/3NxWpHF
 [21]: https://en.wikipedia.org/wiki/Bloom_filter
 [22]: https://amzn.to/3C3Qh7m
 [23]: https://samnewman.io/books/building-resilient-distributed-systems/
 [24]: https://youtu.be/vzYqxo13I1U?si=eacYByQwreIj2O_U
 [25]: https://youtu.be/lLNJld729bc?si=x2ASipnm2PGcKt6d
 [26]: https://youtu.be/9EI_lqPUVEE?si=jR9HOaAHIPnc_qoD
 [27]: https://www.imdb.com/title/tt0086567/
 [28]: https://www.imdb.com/title/tt0113957
 [29]: https://www.imdb.com/title/tt0113243
 [30]: https://amzn.to/3BNS3JM
 [31]: https://www.dotnetrocks.com
 [32]: https://en.wikipedia.org/wiki/Porto_Convention_Centre