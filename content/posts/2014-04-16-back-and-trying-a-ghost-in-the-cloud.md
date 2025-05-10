---
title: 'I''m Back, and Trying a Ghost in the Cloud'

date: 2014-04-16T15:46:32+00:00
url: /back-and-trying-a-ghost-in-the-cloud
categories:
  - Tech

tags:
  - Blogging
  - Ghost

---

## Blogging Again

Right then, let's give this blogging lark another shot, shall we?

I've had some form of blog online since the summer of 1997 (back when they were called online journals or simply 'homepages'). For most of that time my web presence was a single unfocussed site containing posts about all manner of things - a mixture of diary style witterings, some technical content, beer reviews, over-excited commentary on shiny new web applications, unabashed ranting, photos of my kids and other assorted gallimaufry.

The increasing popularity of social media sites over the last decade means that most of those kind of outpourings are now more appropriately spouted on some combination of Facebook, Twitter, Google+ or LinkedIn, depending on the target audience. And to think I once wrote blog posts questioning the need for sites like Facebook and Twitter - use cases certainly emerge and change with mass adoption.
So, I reach the conclusion that I no longer have a requirement for a personal blog. Some of the better or more nostalgic posts may make eventually resurface elsewhere for posterity's sake, but I shouldn't hold your breath.

On the other hand, I do think that writing technical blog posts about my career as a software developer still has virtue. Finding the words to explain the technologies, methodologies, patterns and practices that I use on a daily basis has always been beneficial in solidifying my understanding of a given topic. The blog can act as a exocortex, an aide memoire of strategies that have succeeded (or not) on past projects. It's a wonderful feeling to Google for a problem that you're facing and find a post that you yourself have written in the past offering a solution. And hey, if the posts happen to help anyone else in the process, well that's just a bonus.

## What You Can Expect Here

Amazingly, I'm rapidly approaching 40 and yet still cutting code on a daily basis. I've been working as a professional software developer for 16 years, and contracting for the last six, so I've had opportunity to see a variety of technologies and methodologies, and how they're used in different industries and organisations. I hope to be able to share some of those insights and ruminate on what seems to work, and what doesn't.
Tech-stack-wise, I remain primarily a .NET and SQL Server developer, but I try to embrace open source options and road-test the alternatives whenever possible (what we used to call Alt.Net).

I'm also increasingly fascinated by the variety of database storage options that we have available these days - it feels like the hegemony of the relational database is finally drawing to an end - so I'll try to post about my experiences with alternative persistence mechanisms - "NoSQL", if you must.

I dare say I'll also be mentioning the better tech books that I read, user groups and conferences local to the York/Leeds area, and of course highlighting when I'm going to be available for new contract opportunities (recruiters take note!)

## Trying Ghost

I've always used my own websites as a handy proving ground to develop my own skills and understanding of various web technologies. It was through having a personal homepage in the 90s that I first learned HTML and JavaScript. I read David Siegel's Creating Killer Websites from cover to cover, and then had to unlearn all those bad habits in future years when CSS matured (single pixel invisible gif, anyone?)

Over the years I've hosted my site on blog platforms including .Text, Community Server, Graffiti CMS, Wordpress and Orchard. Those last two especially have grown particularly bloated and into big heavyweight CMS solutions that slowed me down and detracted from the joy of simply blogging.
So, this time round I've decided to try Ghost, the free open source blogging platform that ran a successful KickStarter campaign last year.

I quickly fell in love with Ghost because of its simplicity, cleanliness and speed. It has the features I need and isn't bogged down with stuff I don't. Logging into my old Wordpress sites used to cause me mental anguish as I saw all those little blobs telling me that I needed to update half a dozen plugins again. Ghost feels fresh and easy, and I don't mind the lack of plugins - it is causing me to rediscover how to do things for myself and understand how things work.

Also, Ghost is written in the node.js platform, which is high on my "must try" list of technologies. The idea of taking JavaScript, the lingua franca of the web, and using it on both the client and server, holds a lot of appeal.

## Azure

Back in the day, my early personal sites were hosted at a local ISP that didn't allow any dynamic server-side code. Then for a while I hosted from a thunderously noisy Dell PowerEdge 2300 in the spare room of my flat.

Times change. This time around I'm hosting the blog on an Azure Website. Kudu-powered automated deployment from a Git source control repository is an absolute joy to use. Make a change locally, git commit, git push - and boom! - Kudu does its thing.

Microsoft are wise to bundle generous Azure credit with every MSDN subscription, as the more developers get their hands on this powerful technology, the more they'll be clamouring for their clients and employers to utilise it.

Productivity-enhancing tools like this, along with the DevOps movement in general, pique my interest and I plan to blog more deeply about them in the near future. I feel that the software development industry is still light years behind our manufacturing counterparts in terms of adoption of efficiency-improving processes such as Lean and Kanban. Our levels of waste simply wouldn't be tolerated in other industries - this will change, and enabling technologies like Azure will make it happen.
