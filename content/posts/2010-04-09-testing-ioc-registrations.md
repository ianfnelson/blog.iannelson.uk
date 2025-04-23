---
title: Testing IoC Registrations

date: 2010-04-09T14:04:00+00:00
url: /testing-ioc-registrations/

categories:
  - Tech

---
<!--kg-card-begin: html-->

When I first started writing automated unit tests for my code, I remember getting carried away writing lots of tiny little tests, each with a single Assert. It felt good initially to see all those green ticks, but rapidly became a maintenance headache, and I am now happier having fewer less-brittle tests that do more.

I think it’s great when tools like [AutoMapper][1] provide powerful methods like&#8230;



&#8230;allowing me to test large swathes of the system configuration with a single, stable test.

I wanted to write a similar test to check that all the necessary system dependencies for my MVC application could be resolved by the IoC container. Here’s what I came up with:



A few things to note:

  1. I’m configuring my container using the [GuyWire pattern described by Fabio Maulo][2].
  2. I’m using ControllerExtensions from the [MvcContrib project][3] to identify controllers.
  3. I’m accessing the IoC container via the [Common Service Locator][4].
  4. This only tests the dependencies that are referenced by dependency injection, and won’t pick up on any missing registrations that are only referenced via service locator (you’d have to write separate itty-bitty tests to check those registrations).

What do you think? How, if at all, do you test your IoC container registrations?

<!--kg-card-end: html-->

 [1]: http://automapper.codeplex.com/
 [2]: http://fabiomaulo.blogspot.com/2009/11/guywire.html
 [3]: http://mvccontrib.codeplex.com/Wikipage
 [4]: http://commonservicelocator.codeplex.com