---
title: "Temperature Blanket – A Rare Opportunity for My Coding to Assist Jocelyn's Crafting"
author: ian
type: post
date: 2020-02-16T22:35:00+00:00
url: /temperature-blanket/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2020/02/IMG_20200216_190322.jpg
ct_author_pro_video_display_key:
  - post
ct_author_pro_fi_size_key:
  - default
ct_author_last_updated:
  - default
categories:
  - Family
  - Tech
tags:
  - tidy

---
As the resident geek in our family, it won&#8217;t surprise you to hear that I am occasionally approached by Jocelyn and our kids to provide tech support. Sadly, most of these queries are invariably of the &#8220;how do I print from my phone&#8221; or &#8220;the Sky box stopped working&#8221; ilk, and rarely trouble my software skills. So it came as a pleasant surprise when I recently encountered a genuine reason to use .NET, APIs and Docker in support of one of Jocelyn&#8217;s craft projects.

Jocelyn has embarked on crocheting a _Temperature Blanket_ throughout 2020. This will consist of 366 squares, one for each day of this leap year, in colours corresponding to the minimum, maximum and average temperatures that we experienced on that day.

And here was the rub &#8211; a notable absence of websites that provided these three daily data points for a location close to home. Some sites only had minimum and maximum, but no average. Others considered a &#8220;day&#8221; to run from, say, 4am to 4am, rather than midnight to midnight, which just isn&#8217;t in the spirit of the project. Still others offered the data points she needed, but not for any place close to home.<figure class="wp-block-image">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/IMG_20200216_190534.jpg" alt="The temperature-to-colour key for Jocelyn's 2020 temperature blanket" /> <figcaption class="wp-element-caption">I&#8217;m looking forward to some violet days</figcaption></figure> 

Here was my opportunity to help and earn some husbandly brownie points! I already had an account for the excellent [Dark Sky API][1], which offers forecast and historical weather data by latitude and longitude. Further, [Adam Weiss][2] has made available [dark-sky-core][3], a .NET Standard Nuget Package for accessing this API from .NET code. I fired up Rider, started a new console app, bashed out the following quick function, and proudly presented the desired figures to Mrs Nelson.

<!--kg-card-begin: html-->

<!--kg-card-end: html-->

Scope creep inevitably presented itself at this point, as a console application didn&#8217;t meet UX requirements.

_&#8220;That&#8217;s great Ian &#8211; now can you get it to email me the figures every day?&#8221;_

Hmm. I didn&#8217;t want to get into _that_, but I could do one better, and make this into a simple self-service dedicated website. I launched a new Rider instance and created a boilerplate ASP.NET website to show the desired temperatures for the preceding 28 days. I added a standard Dockerfile, built and pushed a container image, and deployed it to an Azure App Service Plan. The final touch was to configure a memorable subdomain and so it was that <http://blanket.iannelson.uk> was born.

The (rough and ready) source code for both the console application and web version can be found on GitHub:

<ul class="wp-block-list">
  <li>
    <a href="https://github.com/ianfnelson/ColourBlanket">https://github.com/ianfnelson/ColourBlanket</a>
  </li>
  <li>
    <a href="https://github.com/ianfnelson/ColourBlanketWeb">https://github.com/ianfnelson/ColourBlanketWeb</a>
  </li>
</ul>

Photos of Jocelyn&#8217;s other colourful creations (and the occasional photobomb from our Miniature Schnauzer) can be found [on her Instagram profile][4].

 [1]: https://darksky.net/dev
 [2]: https://www.adamweiss.me/
 [3]: https://github.com/amweiss/dark-sky-core
 [4]: https://www.instagram.com/jocelyngnelson/