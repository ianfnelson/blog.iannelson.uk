---
title: ASP.NET Just Became a Legacy Platform

date: 2009-03-22T21:03:00+00:00
url: /asp-net-just-became-a-legacy-platform/
cover: 
  image: https://cdn.iannelson.uk/uploads/2009/03/iStock_000003255884XSmall_3-1.jpg

categories:
  - Tech

---
One of the least surprising but more significant announcements to come out of [Mix ‘09][1] last week was the general availability of [ASP.NET MVC 1.0][2]. The development process for this framework has been very transparent, with no fewer than eight previews, betas and release candidates made available over the past year or so.

Microsoft are being careful to tout ASP.NET MVC as being “an alternative, not a replacement, for ASP.NET Web Forms”, but just look at their list of some of its benefits:

  * Clear separation of concerns
  * Testability &#8211; support for Test-Driven Development
  * Fine-grained control over HTML and JavaScript
  * Intuitive URLs

Which begs the question – if you were kicking off development of a new web-based application on the Microsoft platform today, why would you even consider using Web Forms? Surely the choice now boils down to Silverlight or ASP.NET MVC? I fully expect that, by the time the summer Olympics come to London, Web Forms will be considered to be a legacy platform, with job adverts referring to it as “_Classic ASP.NET_”.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/iStock_000003255884XSmall_3.jpg" class="kg-image" alt loading="lazy" /> </figure> 

And that’s probably no bad thing. Sure, for those of us who lived through the static web, CGI forms and classic ASP, ASP.NET was a godsend, with its cunning state management techniques, custom controls, and page lifecycle events. But, even in the hands of decent developers, it does tend to promote a magic pushbutton anti-pattern, with untestable business logic frequently dumped in the code-behind. So, as a fanboy of OOP, TDD, and Separation of Concerns, this eventual release of ASP.NET MVC comes as a source of great pleasure to me, and means that I can look forward to many more years of enjoyably developing web apps on the MS platform.

But hang on a cotton-picking minute – what exactly is truly new, here? Haven’t we been able to do MVC development on the MS platform for years, using [Castle Monorail][3]? Well, yes we have &#8211; I had the pleasure of using it last summer when developing systems for [Child Maintenance Options][4]. And Monorail itself was inspired by [Ruby on Rails][5], and the J2EE platform has had [Apache Struts][6] for donkey’s years (I used it briefly in the summer of 2002 when developing systems for [Three][7]).

So, if we could do this stuff already, even on the ASP.NET platform, why does the release of ASP.NET MVC still matter so much?

The slightly depressing but inevitable truth is that it matters because it’s a product which has been developed by and will be fully supported by Microsoft. To many organisations, that’s reason enough to use it when they would have never in a month of Sundays considered using the likes of Monorail.

As a crude indicator of popularity, consider the questions posted on [Stack Overflow][8] to date. 1819 of them have been tagged “ASP.NET-MVC”, whilst a mere 22 have been tagged “Monorail” or “Castle-Monorail”.

The same can be seen of many other modern technologies used in the development of custom applications. Take [ORM][9] for example – [NHibernate][10] has been around for, what, around six years or so since it was originally ported from [Hibernate][11] (I seem to have [first mentioned it on this blog in 2004][12]). But the traction that [LINQ to SQL][13] and [Entity Framework][14] have garnered in their short existence has already almost outstripped the popularity of NHibernate by some metrics.

Entity Framework, while not to everyone’s taste, at least has the potential to offer something quite different and distinct from NHibernate. But the same can’t be said of some other recent examples of Microsoft’s ongoing [Embrace, Extend and Extinguish][15] policy – what does Visual Studio Unit Testing offer that [NUnit][16] didn’t? Why develop the [Unity Application Block][17] in a universe that already contains [Castle Windsor][18] and a plethora of other [IoC][19] containers? How long will it be before Microsoft write their own [mock object][20] framework? Surely they will eventually do so, to meet the demands of the large proportion of dev shops that simply won’t touch none-MS tooling.

Why this should be the case, I can’t really say, but as a freelance developer I’ve seen it with my own eyes – working with organisations with technical strategies that specify the use of Microsoft technologies wherever possible, and shun the adoption of open source or third-party solutions. I hear people say “we’ll wait for Entity Framework to mature, rather than trying NHibernate”, and I see the funny stares people give me when I meekly suggest that we use [xUnit.Net][21] or [Moq][22] on a project.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/iStock_000004857675XSmall_3.jpg" class="kg-image" alt loading="lazy" /> </figure> 

So, perhaps we can’t entirely blame Microsoft. True, their practices do sometimes feel to be anti-competitive and limiting of choice. But they are a business after all, and are merely meeting the demands of their customers.

And is it really in my best interests to complain about these practices? I am a freelance developer and Microsoft registered partner and have to be pragmatic about this. I am in business developing custom applications for the Microsoft platform, and in doing so I want to use 21st-century techniques such as ORM, the MVC pattern, unit testing, mocking, IoC, etc. If my clients are more likely to be receptive to those concepts if there exists a suitable Microsoft implementation, then so be it. But please, let me continue using NHibernate instead of Entity Framework…

ASP.NET RIP. Long live ASP.NET MVC.

 [1]: http://live.visitmix.com/
 [2]: http://www.asp.net/mvc/
 [3]: http://www.castleproject.org/MonoRail/
 [4]: http://www.cmoptions.org/
 [5]: http://api.rubyonrails.org/
 [6]: http://struts.apache.org/
 [7]: http://www.three.co.uk
 [8]: http://stackoverflow.com/
 [9]: http://en.wikipedia.org/wiki/Object-relational_mapping
 [10]: http://www.hibernate.org/343.html
 [11]: http://www.hibernate.org/
 [12]: https://blog.iannelson.uk/nhibernate/
 [13]: http://msdn.microsoft.com/en-us/library/bb386976.aspx
 [14]: http://msdn.microsoft.com/en-us/library/bb399572.aspx
 [15]: http://en.wikipedia.org/wiki/Embrace,_extend_and_extinguish
 [16]: http://www.nunit.org/index.php
 [17]: http://msdn.microsoft.com/en-us/library/cc468366.aspx
 [18]: http://www.castleproject.org/container/index.html
 [19]: http://en.wikipedia.org/wiki/Inversion_of_Control
 [20]: http://en.wikipedia.org/wiki/Mock_object
 [21]: http://www.codeplex.com/xunit
 [22]: http://code.google.com/p/moq/