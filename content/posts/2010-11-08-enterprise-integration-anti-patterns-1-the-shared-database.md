---
title: 'Enterprise Integration Anti-Patterns #1 – The Shared Database'
author: ian
type: post
date: 2010-11-08T05:11:00+00:00
url: /enterprise-integration-anti-patterns-1-the-shared-database/
ct_author_pro_video_display_key:
  - post
ct_author_pro_fi_size_key:
  - default
ct_author_last_updated:
  - default
categories:
  - Tech

---
<!--kg-card-begin: html-->

So, I was in the office at a client site, walking back to my desk after grabbing a quick coffee, when a developer on a sister product to my current project grabbed me and asked (I paraphrase somewhat):

> “Hey, Ian – [my app] needs to retrieve [small piece of data] from [your app], so I’ve stuck a stored proc in [your database], OK?”

I felt quite violated. My poor app, what had it done to deserve this despicable treatment?

Before I start my rant about the downsides of directly accessing application databases in this way, let me first try to enumerate the benefits of such an approach. I can think of three:

  1. It’s a quick solution to develop (at least initially).
  2. The technical concepts involved are well understood by the vast majority of developers and other team members.
  3. The functionality is encapsulated in one place, i.e. the stored proc, which is at least preferable to allowing the execution of ad-hoc SQL.

But despite this being seen as a quick-win, I think allowing application databases to be shared in this way is almost always a bad idea in the medium to long term.

As a developer, one of my primary goals is to create systems that are easy to maintain and enhance, in anticipation of the inevitable future change requests that will put food on my children’s plates. As well as making life easier for yourself, this approach is also common courtesy to the programmers that maintain the system after you’ve left. As the saying goes, “always code as if the guy who ends up maintaining your code will be a violent psychopath who knows where you live” &#8211; I think that’s good advice to heed for all developers who have an interest in building their reputation in our small and incestuous industry.

When we begin down the slippery slope of forcing a single database to serve the needs of multiple disparate consuming systems, we make a rod for our own backs. Any planned changes to the database to meet new requirements in the primary application need to consider the needs of the parasitic applications that care little for your ability to respond to change as long as they continue working. In our particular scenario, it’s worth highlighting that “my” application is using NHibernate as an ORM layer, so until this invasion we have been able to perform database schema refactorings with relative impunity. No longer – now we have to consider and potentially maintain someone else’s stored procedure when making changes.

Sure, at the start it’s “just a stored proc”, and the maintenance overhead is relatively low. But like the proverbial broken window, allowing that first chink in your carefully-crafted layered application architecture sets a dangerous precedent. If it goes unchecked, it may be seen as a valid pattern to be emulated by future developers, until the database schema ossifies and becomes almost impossible to change as it struggles to meet the requirements of multiple consuming applications.

If you think I’m scaremongering or labouring a point here I would urge you to spend some time hanging out on the NHibernate and Fluent NHibernate mailing lists. It won’t be long before you see messages that describe complex and intractable mapping problems and mention the caveat “I’m not allowed to change the database”.

Aside from the maintainability issue (which is my major gripe), the end result of this quick-and-dirty approach also leads to a poorer-quality solution which may struggle to meet nonfunctional requirements. Direct database access from external applications is a crude, low-level solution to a common problem. All the hard work done in creating a layered architecture with DAOs, business logic layer etcetera is swept aside by some other cowboy app which says “screw all that, gimme the data”. Any considerations that may have been given to concerns such as caching and application-level security go out of the window. The potential for locks and even deadlocks on the shared database is increased.

If you have the smallest shred of dignity and self-respect on behalf of your application, then please &#8211; don’t let its nether regions be exposed to all and sundry.

<!--kg-card-end: html-->