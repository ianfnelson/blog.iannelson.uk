---
title: ASP.NET 2.0 – one month on

date: 2005-12-10T19:12:00+00:00
url: /asp-net-2-0-one-month-on/

categories:
  - Tech
tags:
  - tidy

---
It&#8217;s over a month now since Visual Studio 2005 officially RTM&#8217;d, and during that time I&#8217;ve been fortunate enough to have been using it for the majority of my time on most working days. One of the things we&#8217;re trying to achieve is the integration of several distinct internal corporate web applications into a bespoke portal system, with single sign-on, common authorization model, common look and feel, etc. There&#8217;s been quite a heavy R&D / proof-of-concept aspect to the workload so far, as we try out different ways of achieving this, and grow familiar with the new technologies available to us in ASP.NET 2.0.

I thought I&#8217;d share with you a few of the links that have been of most help to me over the past month or so:

  * [Scott Guthrie&#8217;s Blog][1]. If you develop ASP.NET applications, this is the one site, above all others, to which you should subscribe. Every single one of Scott&#8217;s posts provides extremely useful tips and tricks &#8211; such as [Tips For Nested Master Pages and Design Time][2], [How to Change the Default Browser][3] (not obvious, is it?). More importantly, it&#8217;s here that you&#8217;ll first learn about VS2005 add-ons such as [Web Deployment Projects][4] and the forthcoming new [Web Project Model][5].
  * [Serializing a KeyedCollection][6]. It doesn&#8217;t work, but it&#8217;s not your fault &#8211; it&#8217;s a bug in the .NET Framework. Had I found this page earlier I would have saved myself multiple hours of frustration.
  * Another serialization problem that foxed me for a while &#8211; I had a custom Principal object in a locally referenced assembly. Every time I tried to set my Context.User to an instance of this, I got a SerializationException with a &#8220;Type is not resolved..&#8221; message. Huh?  More Googling threw up [this post][7] [Google Groups] from Nov 29 explaining the issue and giving some workarounds.
  * [Dan Wahlin &#8211; Sharing Master Pages across IIS Applications][8]. This is \*exactly\* what we&#8217;ve been trying to do &#8211; Dan&#8217;s post gave us a real leg-up.
  * [David Ebbo &#8211; Turning an ascx user control into a redistributable server control][9]. Sounds like a neat trick, although I haven&#8217;t had cause to try it yet.
  * [Rich Strahl &#8211; Understanding Page Inheritance in ASP.NET 2.0][10]. If you&#8217;ve got into the habit of dynamically loading user controls into your pages in ASP.NET 1.1, and were planning on doing the same going forward, then you should check out Rick&#8217;s article first. Things aren&#8217;t quite as straightforward as they used to be&#8230;
  * [MSDN: Building ASP.NET 2.0 Web Sites using Web Standards][11]. Don&#8217;t scoff, it&#8217;s an important topic!  I&#8217;ve been waiting for valid (X)HTML output from Visual Studio for a long time, I&#8217;m glad to see MS are finally taking standards (and Accessibility) seriously.
  * [MSDN: GridView Examples][12]. [Scott Mitchell&#8217;s][13] huge (122 page) article explaining how to do anything (well, almost) with the GridView control. Talking of which, you could do worse than also subscribe to Marcie Robillard&#8217;s new site, [GridViewGirl][14].

Also, two books which have really helped me get up to speed:

  * [Professional .NET Generics][15] &#8211; a Wrox book (not a huge one, thankfully) on this useful new (to .NET) programming feature.
  * [ASP.NET 2.0 &#8211; A Developer&#8217;s Notebook][16]. One of those books from the O&#8217;Reilly &#8220;notebook&#8221; series that aims to get you up to speed quickly on new features. It works.

 [1]: http://weblogs.asp.net/scottgu/
 [2]: http://weblogs.asp.net/scottgu/archive/2005/11/11/430382.aspx
 [3]: http://weblogs.asp.net/scottgu/archive/2005/11/18/430943.aspx
 [4]: http://weblogs.asp.net/scottgu/archive/2005/11/06/429723.aspx
 [5]: http://weblogs.asp.net/scottgu/archive/2005/12/07/432630.aspx
 [6]: http://pluralsight.com/blogs/craig/archive/2005/10/19/15696.aspx
 [7]: http://tinyurl.com/7tp97
 [8]: http://weblogs.asp.net/dwahlin/archive/2005/11/16/430779.aspx
 [9]: http://blogs.msdn.com/davidebb/archive/2005/10/30/487160.aspx
 [10]: http://west-wind.com/weblog/posts/3016.aspx
 [11]: http://msdn.microsoft.com/asp.net/reference/design/default.aspx?pull=/library/en-us/dnaspp/html/aspnetusstan.asp
 [12]: http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnaspp/html/GridViewEx.asp
 [13]: http://www.scottonwriting.net/sowBlog/
 [14]: http://www.gridviewgirl.com/GridViewGirl/
 [15]: http://www.amazon.co.uk/exec/obidos/ASIN/0764559885
 [16]: http://www.amazon.co.uk/exec/obidos/ASIN/0596008120