---
title: NDepend

date: 2009-02-04T15:02:00+00:00
url: /ndepend/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2009/02/iStock_000002131299XSmall_3-1.jpg

categories:
  - Tech
tags:
  - Software
  - .NET

---
OK, dear readers, today I’d like to talk about tools.

Software development isn’t really so different from traditional skilled crafts in that it is important to have an understanding of the tools available to help you create a quality products in the least amount of time possible.

For .NET developers, the Visual Studio IDE is usually just the starting point, and most of us will come to rely on some of the tools listed in Scott Hanselman’s famous [tools list][1]. Personally, I can’t imagine coding without first installing [Refactor Pro][2], editing text files in anything other than [TextPad][3], or working on a machine that doesn’t have Snag It installed.

## MRI For Your .NET Application

Another one of the tools that I reach for frequently, and the subject of this blog post, is **[NDepend][5]**, which performs rapid static analysis of a set of .NET assemblies and provides a deliciously visual interface for interpreting and understanding the results. Through the use of this tool, architects and developers can quickly spot problems or potential areas for improvements in a codebase. It’s essentially an MRI Scanner for your .NET code!

![](https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000004593967XSmall_2.jpg) 

## So.. What Does It Do?

I’ve briefly mentioned my use of NDepend before – for example I [blogged in December][6] about how I was able to use NDepend to resolve an MSB3247 compiler warning which a developer was experiencing. But there’s much more to it than just helping solve simple assembly reference problems. Some of my favourite features include:

An interactive **Dependency Graph**, giving a visual representation of the relationships between assemblies (both within your application, and any third-party and system dependencies). Here’s an example output from analysing the S#arp Architecture project:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/DependencyGraphSnapshot.png)

The **Dependency Matrix** cross-tabulates all the references between assemblies, allowing for drilling down to member level. Remember all those dictats you issued to the dev team in your coding standards, such as “don’t reference the data layer from the front-end”? Well, this is the window you’ll use for ensuring that the team are abiding by such rules. Usefully, cyclical references between namespaces are particularly highlighted.

![](https://blogstouks01.z33.web.core.windows.net/2023/08/NDependMatrix_2.png)

The **Metrics Window** is where I tend to spend most of my time, using the inbuilt CQL (Code Query Language) to identify areas of the codebase which are ripe for refactoring. This area of the tool is like FxCop on steroids.

![](https://blogstouks01.z33.web.core.windows.net/2023/08/NDependMetrics_2.png)

I’m also a big fan of the **Changes Explorer** functionality, which highlights at a glance the changes made between any two builds of an application. Also the ability to import **Code Coverage** files from NCover or Visual Studio Team System, to similarly highlight the areas of a solution which are adequately covered by [unit tests][8].

## Real-World Benefits

NDepend is useful when looking at your own code, but really comes into its own when you want to quickly grok a codebase developed by someone else. Here’s an example:

My current client have the IP rights to a bespoke .NET application which has been developed for them by a third party. They plan to bring the development of this application in house, and recently asked me to take a look through the source and feed back my thoughts on the architecture.

Initially, I made the mistake of doing this code review solely by looking at the code itself, through the IDE. I was impressed – the code was exceedingly clean, the solution well-structured, and everything looked very straightforward. The object model was mapped to the database using [NHibernate][9], which in turn was abstracted from the appliation code by a standard DAO pattern. So far so good, and I was about to email a thumbs-up.

But I smelled a rat – the code was almost too clean, and I couldn’t find the actual meat of the business logic. So, I whipped out NDepend (which I really should have done initially), ran an analysis, and realised that the cleanliness and simplicity of the middle tier was due to over two-thirds of the solution logic existing in the user interface layer! In fact 28% of the IL instructions from the entire solution were contained in the code-behind of just three web pages. It was a classic example of the [magic pushbutton anti-pattern][10], and I very nearly failed to spot it.

## TMI? 

If I had to identify a drawback to NDepend, it is the risk that much of the output information may be meaningless to the average .NET developer. Returning to my earlier medical analogies, an X-Ray or MRI Scan is useless in itself until it is viewed by a medical professional with the knowledge and experience to interpret the results.

![](https://blogstouks01.z33.web.core.windows.net/2023/08/iStock_000005830514XSmall_2-1.jpg)

This potential problem is somewhat alleviated by the explanatory videos, [Patrick’s extensive blogging][11], and indeed the range of predefined CQL queries which serve to interpret the results and highlight potential problems. Even so, I suspect NDepend is more likely to be found in the toolkit of the architect or lead developer rather than the hobbyist – especially given the EUR 299 price tag for a professional license.

## Final Thoughts

To summarise, NDepend provides a short-cut to quickly understanding a .NET codebase and identifying potential improvements. If the quality of your code is important to you, or you frequently have to review code developed by other people, then I think you’ll find NDepend to be indispensable.

_Disclaimer: Ian Nelson was provided with a complementary review copy of NDepend Professional version 2.0, and has subsequently paid for later editions of the software._

 [1]: http://www.hanselman.com/tools
 [2]: http://www.devexpress.com/refactor
 [3]: http://www.textpad.com
 [5]: http://www.ndepend.com
 [6]: https://blog.iannelson.uk/msb3247-dependent-assembly-conflicts/
 [8]: https://blog.iannelson.uk/12-reasons-why-i-love-unit-tests/
 [9]: https://blog.iannelson.uk/on-the-joys-of-object-relational-mapping/
 [10]: http://en.wikipedia.org/wiki/Magic_pushbutton
 [11]: http://codebetter.com/blogs/patricksmacchia/