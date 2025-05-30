---
title: An MVC Gotcha and the PRG Pattern

date: 2010-04-09T10:04:00+00:00
url: /an-mvc-gotcha-and-the-prg-pattern/

categories:
  - Tech
tags:
  - .NET

---
If you’ve recently moved across to ASP.NET MVC development following years of wrangling with the leaky abstraction that was WebForms, you may have encountered some seemingly curious behaviour when posting back to the same URL.

Suppose we have the following simple, contrived and utterly imagination-free model:

{{< gist d0e0260464145fde2dbc MVCG1.cs >}}

Here’s a view:

{{< gist d0e0260464145fde2dbc MVCG2.cshtml >}}

And here’s the controller:

{{< gist d0e0260464145fde2dbc MVCG2.cs >}}

Note that we have two separate Index actions – one for HTTP GET which instantiates and displays a new FooModel instance, and one for HTTP POST which modifies one of the properties on the posted FooModel instance before re-rendering the view.

We issue a GET against the relevant URI, and the view renders as we expect (in that both the textbox and the literal show the value 1):

![](https://blogstouks01.z33.web.core.windows.net/2023/08/Foo1_3.png)

But here’s the gotcha – look what happens when we hit the increment button to post back:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/Foo2_3.png)

Huh? What gives? The model has definitely been updated (as reflected in the literal which is now showing 2), but the textbox is still stubbornly displaying 1.

What’s happening is that the Html helpers for form fields (including hidden fields) take their values from the controller’s ModelState dictionary, which contains details of all the POSTed fields and any validation errors.

So how to achieve our desired behaviour? We could make a quick and dirty call to ModelState.Clear(), but that’s not such a good idea and might lead to undesirable results surrounding validation.

In fact, this gotcha is symptomatic of a deeper anti-pattern in evidence in this example, namely rendering views from POST actions. Consider what happens if the user refreshes their browser when viewing the POSTed view. Recognise these dialog boxes?

![](https://blogstouks01.z33.web.core.windows.net/2023/08/IE_3.png)
![](https://blogstouks01.z33.web.core.windows.net/2023/08/Chrome_3.png)
![](https://blogstouks01.z33.web.core.windows.net/2023/08/Firefox_4.png)

Pretty ugly, aren’t they? And you really don’t want to leave open the possibility of a user accidentally submitting duplicate transactions if at all possible.

Enter the [Post, Redirect, Get pattern][1]. Here, the POST action updates the model as before, but redirects to the GET action to perform the re-rendering of the view. Of course, you’ll need to persist the model somewhere in the meantime (e.g. session state). This pattern avoids the gotcha of a value from the ModelState being displayed instead of an updated figure, and ensures that your user will never see those ugly form resubmission dialog boxes, or submit duplicate transactions.

Here’s a quick reworking of the earlier controller to use this pattern. Note the introduction of a “New” action to handle the instantiation of a new Foo instance. This is crummy code fraught with potential uncaught NullReferenceExceptions, but you’ll get the gist, I’m sure.

{{< gist d0e0260464145fde2dbc MVCG4.cs >}}

And now we get the desired results on postback:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/Foo3_3.png)

If you’re using MVC, and returning ViewResults from POST actions, I would urge you to consider the potential side-effects of that approach, and standardise instead on a PRG pattern.

 [1]: http://en.wikipedia.org/wiki/Post/Redirect/Get