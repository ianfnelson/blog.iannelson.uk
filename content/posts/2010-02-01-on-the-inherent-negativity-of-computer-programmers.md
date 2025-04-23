---
title: On the Inherent Negativity of Computer Programmers

date: 2010-02-01T20:02:00+00:00
url: /on-the-inherent-negativity-of-computer-programmers/

categories:
  - Fun
  - Tech

---
A couple of weeks ago, early one morning, my friend and fellow coder Scott asked a curious question:

> “Do you think that programming computers for a living gives you a negative outlook on life?”

Now, Scott is unfortunately responsible for administering occasional TLC to a codebase that I cut as long ago as 2004, so I assumed he was referring to this and was about to raise some complaints about my hand-rolled query object criteria framework or other coding horror. I steeled myself to defend my work as he continued to explain:

> “Well, when coding we have to consider all the potential edge cases and exceptions – what happens if our methods get dodgy inputs etcetera. And it’s spilling over into my real life. We’re moving house at the moment, and I just find myself worrying about what happens if the buyers pull out, if we can’t get the mortgage, if the survey reveals problems… I’m really negative about the whole process.”

At the time I smiled and put this down to the notoriously tortuous British house-buying process, but the more I think about it, the more I think Scott might be onto something.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/310411215_3dd7f5cd07_m_1__3.jpg" class="kg-image" alt="Pissed Off Ian, by John Conners" loading="lazy" title="Pissed Off Ian, by John Conners" /> </figure> 

My wife and I are currently plotting a well-deserved summer vacation in sunnier climes, which theoretically should be an enjoyable task, right? But I can’t simply enjoy it and focus on the “sunny-day scenario”. My mind is full of edge cases (“What if we can’t fit all our stuff in the car?”), unhandled exceptions (“Will we get our passports in time?”), compatibility issues (“will our choice of dates suit my clients?”), unwise over-reliance on dependent components (“Will the airline have any child seats available?”) and of course user errors (“Suppose we book the wrong dates?!”). No focusing on the happy path for this codemonkey.

The more I think about it, the more I see that Scott has a point. Professional software development forces us to anticipate invalid input, stupid users, hackers,  insufficient hardware, unreachable remote services, and whether our software can pass [the Turkey test][1]. We consider SQL injection, cross-site scripting, buffer overflows, and countless other common [threats and exploits][2]. Not to mention worrying about what happens when other devs get their grubby mitts on our codebase, or when the client inevitably unleashes some game-changing requirements late in the lifecycle. We’re all about expecting the worse, coding [defensively][3], and decoupling ourselves from dependencies. The ever-present potential for high-profile failures caused by something as simple as an inverted boolean comparison, combined with the likelihood of critique and criticism from our fellow coders, DBAs, auditors and sysadmins is enough to turn most devs into a nervous wreck before they’ve so much as initialised a variable. That reminds me, I must check that my Professional Indemnity insurance policy is up to date.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/sb_2.png" class="kg-image" alt="sb" loading="lazy" title="sb" /> </figure> 

So, anecdotal evidence and my own experience suggests to me that Border’s First Law is a truism. Programming Computers Can Cause Negativity, Cynicism and Pessimism.

Are these necessarily negative traits to have, or can such enforced forethought and consideration of potential issues be a benefit in “real life”, away from the screen? I suspect as with many things, the answer is that there is some balance to be had. So – getting to the airport on time is A Good Thing. Spending a fortnight’s vacation panicking on the offchance that the flight operator goes bust is, probabilistically, a bit silly.

I’m not sure where I’m going with this, or what the answer is, except perhaps to be a little more aware of this mindset and try to adopt a little restrain when applying programming principles to “real-life” conversations. Life, alas, is not a well-defined algorithm, and God knows it doesn’t come complete with a full suite of regression tests.

PS – You know, I just remembered that I [blogged about this topic before][4]!

 [1]: http://www.moserware.com/2008/02/does-your-code-pass-turkey-test.html
 [2]: http://en.wikipedia.org/wiki/Category:Computer_security_exploits
 [3]: http://en.wikipedia.org/wiki/Defensive_programming
 [4]: https://blog.iannelson.uk/edge-cases/