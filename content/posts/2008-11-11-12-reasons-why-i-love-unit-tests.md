---
title: 12 Reasons Why I Love Unit Tests

date: 2008-11-11T22:11:00+00:00
url: /12-reasons-why-i-love-unit-tests/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2008/11/photo-1523976888287-7454b4df44f4.jpg

categories:
  - Work
  - Tech

---
<!--kg-card-begin: html-->

On my continuing journey through this thrilling world of professional software development, I frequently encounter teams who hold no truck with this crazy new-fangled concept of unit testing. Heck, truth be told, I sometimes come across teams who don’t use _source control_, but that’s by the bye.

In these situations, I try my best to lead by example, continuing to practise TDD on any new code that I cut, and insisting on covering with unit tests any pre-existing code which I have to modify. Sooner or later, this prompts someone to ask why I am doing this (often insinuating that I am wasting my time, and by implication the client’s money). At that point, flustered, I invariably struggle to remember or adequately articulate the many and various ways in which unit testing makes me a better developer. So, consider this blog post a personal aide-mémoire to help me the next time this occurs (as well as being a homage to [Jake Shillingford’s second-best song][1]).

**1. I know that my code works.**

Let’s get the obvious one out of the way first. If I take the time to write unit tests for my code, then I know that the code “works” (i.e. that it behaves as I intended, or hopefully as the specification requested). Any time I want to check that my code works, I can do so with a few clicks. The confidence and feeling of well-being that this brings can’t be underestimated. If you don’t have unit tests, how do you know that your code works?

**2. I know when I’m finished.**

As you’ll know if you’ve read my [post professing my undying love for Remember The Milk][2], I’m fond of organising my life through to-do lists. When I’m developing software, the unit tests that I create before developing the code act as my to-do list, help me focus on what it is that I’m trying to achieve, without getting distracted making unrelated changes to the codebase. When all the tests go green, I know I’m done and can move on to the next task.

**3. I can develop cleaner APIs.**

I’m not much of a UI developer; I spend much more of my time working in the middle tier, making class libraries, object models, WCF services and the like. When practicing TDD, I write tests to consume my code before I write the code itself. This forces me to think about things like method signatures and member visibility. Should that method really be public? Do I really need that “out” parameter? Will all those overloads get used? If I didn’t write tests for the middle tier in this way, I wouldn’t consider these questions in quite so much detail, and these issues wouldn’t come to light until I (or worse, someone else), began consuming my code for real.

**4. Testable code is well-designed code.**

This one came as an unexpected surprise to me after I had been writing unit tests for a while and forced myself to make the effort to test code which I initially felt was difficult to test.

It turns out that many of the techniques which can be used to make code more testable are the exact same techniques which make code better designed, understandable, flexible and maintainable.

Be honest, when you’re cutting code, how often do you consider things like Low Coupling, High Cohesion, and adhering to the Single Responsibility Principle? Probably not often, I’ll bet. I know I didn’t. But since I started asking myself “How can I make this code testable?” I’ve been delighted to realise that my code magically acquired these properties as a pleasant side effect. Similarly, using techniques like Dependency Injection and Inversion of Control along with Mocking Frameworks for the purposes of testability also serves to make the solution more open to change, and reduces dependencies during the development process (no longer do you hear “Gee boss, I’d love to get started writing the Foo class, but it depends on the Bar class, and Dave hasn’t finished writing that, what with the accident with the bus and all…”).

**5. I can refactor mercilessly and fearlessly.**

> “Nel-son!!”

I like refactoring. No, wait, scrub that – I _love_ refactoring. Some people get their kicks from gardening, well, I could spend many happy hours weeding a big tangled codebase. Now, in the past, this has gotten me into trouble, when the “improvements” I’ve rashly made have inadvertently caused bugs (sorry John, Sion, Scott and Colin!). Since adopting TDD however, I’ve been confident that my code is sufficiently covered by unit tests that I may refactor mercilessly, safe in the knowledge that the test suite will highlight any unintended side effects. This results in a winning combination of clean code and co-workers who don’t have an urge to throttle me.

**6. I Release Fewer Stupid Mistakes.**

> “Ah, yeah, silly me, I just copied-and-pasted a line in the DAL, and now all your customers are displaying as having the same forename and surname! Smith Smith, Brown Brown, ha ha!”

Perversely, some coders seem to wear their really dumb mistakes as a “badge of honour”, proof of their fallibility, a sign that they are human. It’s as if they are suggesting to their boss/client not to worry, that they _only_ make dumb mistakes on the easy code, but concentrate much harder when coding the tough algorithms. Honest, guv’.

I don’t buy this crap. Stupid mistakes are stupid mistakes, period. I think that dumb mistakes, uncaught at an early stage, waste the time of the test team, result in rework, and ultimately waste the client’s money. That’s nothing to laugh about. Covering even the simple, easy code with unit tests reduces the likelihood of these knucklehead bugs getting through, increasing my likelihood of a “right-first-time” reputation. And _that’s_ something to be proud of.

**7. Bugs don’t come back.**

> “But I’m _sure_ we fixed that bug months ago!”

Before I fix a bug, I write a failing test. That test then becomes a permanent fixture in the test suite, and therefore I can be confident that no “undead bug” will ever come back to haunt me. It’s a very simple concept, but it works. Bug reactivations imply loose development practices, and that’s not an implication I want to be made about my work. Kill the bug once, and keep it dead.

**8. It’s the fastest way to test my changes.**

Testing my changes through artificial unit tests is invariably quicker than testing the functionality by calling it through “real life” use of the overall system.

Suppose that I’m working on amended postage charge logic for an online retailer – I could test this by either:

a) Repeatedly manually walking through the application, adding a product to my basket, attempting to “check out”, and calculating whether the displayed postage charge is as I expect, or

b) Writing a unit test once to automate the testing of the new logic.

Gee, let me think about that for a while…

**9. I spend more time coding, less time in the debugger.**

Stop me if this conversation sound  
s at all familiar:

> “How was your day today, darling?”
> 
> “Ugh, don’t ask. I spent, like, _seven hours_ trying to track down a bug. I pulled out Reflector, and even started debugging into the .NET framework class library – I was convinced for a while there it was a problem in System.String. But it turned out I just had some Boolean logic the wrong way round.”
> 
> “That’s nice, dear. More mange tout?”

Visual Studio has excellent debugging tools, but still, I’d rather be spending my time cutting new code, thanks all the same. I’m sure the clients who pay my invoices feel much the same. Catching the bugs early, through effective unit testing, means that I spend far less time in the debugger.

**10. Writing documentation and sample code is boring.**

Visiting the dentist. Cleaning the bathroom. Writing documentation. All things which I’d rather put off until tomorrow, thank you very much.

If, on any given day, I have the choice between firing up Word and documenting my class library, or firing up Visual Studio and adding shiny new functionality to the same library, well, it’s no contest.

But here’s the neat thing – having taken the time to create a comprehensive suite of unit tests for my own, selfish purposes, it turns out that potential consumers of my library can benefit from them as a de facto set of usage examples and documentation. Yay!

**11. I can hand the code over to other people.**

> “Dave’s the only person who understands that code.”

Oh really? What happens when Dave is on holiday? Or quits to get a better-paid job? Or gets hit by a bus? That’s a bit of a risk for your project, surely.

Maybe you’re a Dave, and your unique knowledge of a particular system means that you only ever get to work on that one application. Shiny new projects come along, and get handed to your colleagues, because you’re too busy supporting the Legacy App From Hell, until you quit to get that better paid job, or walk in front of a bus in desperation.

If, on the other hand, you’ve covered the code in unit tests, then you have effectively documented the codebase, provided example usages, and made it near-impossible for any future developers to break existing functionality due to their ignorance of the system. They can try making a change, run the unit tests, and instantly find out whether their change works. This helps to make possible [Collective Code Ownership][3], a variety of work for all members of the team, and no risky dependencies on Dave and his jaywalking habits.

**12. I’m A Professional**

I’ll return to what I said in the opening sentence of this article – this is _professional_ software development. This isn’t just my hobby, or my day job. It’s my career, my business, my passion and the livelihood of myself and my family. I strive to improve and hopefully excel at it. All the research and my own experience suggests that practicing TDD results in fewer defects, saves time in the medium and long term, and is generally the approach to be expected of a professional. If you’re looking for a quick-fix from a cowboy contractor, go elsewhere and save yourself some money… in the short term 🙂

<!--kg-card-end: html-->

 [1]: http://uk.youtube.com/watch?v=DW1AHrTNBao
 [2]: https://blog.iannelson.uk/remember-the-milk/
 [3]: http://www.extremeprogramming.org/rules/collective.html