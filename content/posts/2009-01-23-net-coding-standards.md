---
title: .NET Coding Standards

date: 2009-01-23T15:01:00+00:00
url: /net-coding-standards/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2009/01/iStock_000004478097XSmall_2-1.jpg

categories:
  - Books
  - Tech

---
Sometimes, when you join a new team as a .NET developer, the team lead proudly points you in the direction of a Word document or wiki page detailing the team’s house coding standards.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000004478097XSmall_2.jpg" class="kg-image" alt loading="lazy" /> </figure> 

In my experience, these documents are invariably:

  * Incomplete.
  * Subjective.
  * Not enforced.
  * Largely copied from the interweb.
  * Obsessed with the trivial (e.g. whitespace) while failing to mention the genuinely useful (e.g. boxing/unboxing, avoiding use of deprecated classes, Dispose pattern, etc).

I know this because I’ve been involved in creating such documents in the past 🙂

Don’t get me wrong, I’m all in favour of creating clean code, and promoting standards within a team. I just find that most in-house style guides fail to achieve this, for the reasons listed above.

So, as I was walking through the city today, I started having a little debate with myself. “OK then, smarty-pants. What’s your alternative? What would your in-house coding standards guidelines look like?”

I think it can be summarised by four simple points, listed in order of importance:

**1. Don’t Ignore Compiler Warnings**

You might think this would be an obvious one, but I’ve lost count of the number of times I’ve retrieved a solution from source control, compiled it, and been presented with a list of compiler warnings. Most of the time, there’s no excuse for this. If the _compiler_ smells a rat in your code, then you’ve got a problem, be it variables that are used without being initialized, unused variables, unreachable code, or whatever. It’s sloppy code, and it’s easily avoided, so don’t leave it for the next guy to clean up. I am, if you hadn’t guessed, a big fan of setting the “treat compiler warnings as errors” flag in a project’s build properties.

**2. Follow the Framework Design Guidelines**

The [Framework Design Guidelines][1] is another one of those books whose name doesn’t do it justice. The sagely guidance it contains is appropriate not only to Microsofties developing the FCL itself, but to anyone writing any .NET code. Don’t let your developers near a copy of Visual Studio until they’ve provided a sworn affidavit confirming that they’ve read this book! 🙂

All of the guidelines are concisely boiled down into Do, Consider, Avoid, and Do Not recommendations, and you would do well to adhere to these. Getting a few copies of this book for your team is a much more effective and cost-effective approach than trying to develop your own coding standards.

**3. Run FxCop**

Having read and digested the Framework Design Guidelines, you need an easy way to enforce them. This is best achieved by running [FxCop][1] against your code (now integrated into some of the Visual Studio SKUs as a “Code Analysis” option).

Depending on the target audience for your solution, you may consider it reasonable to ignore some of the localization recommendations (i.e. when developing in-house line of business applications with limited geographical reach). But generally, if FxCop flags a warning in your code, I believe you would be well advised to correct the problem. Doing this helps to avoid a wide range of performance, security and design issues, in addition to enforcing consistent source code conventions.

**4. Run StyleCop**

Finally, if you simply must achieve that uniform source code appearance that the whitespace Nazis in every team strive for, consider requiring that your devs run their code through [StyleCop][2] before checking in. It may initially be a bit annoying, and for sure some of the recommendations are highly subjective, but there’s no arguing that it does enforce a standard style, with a strong focus on increasing readability and reducing ambiguity.

**And After That&#8230;?**

Following the four points above should result in the low-level codebase produced by a team being readable, of high quality, in a common style, and free of many common “gotchas”. It doesn’t validate the higher-level architectural considerations, but in my opinion that is outside the scope of such a document, and could best be achieved through the use of a tool such as [NDepend][3]. But that’s a topic for another post&#8230;

 [1]: http://www.amazon.co.uk/gp/product/0321545613?ie=UTF8&tag=ianesbl-21&linkCode=as2&camp=1634&creative=19450&creativeASIN=0321545613
 [2]: http://code.msdn.microsoft.com/sourceanalysis
 [3]: https://blog.iannelson.uk/ndepend/