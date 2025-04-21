---
title: MVC – Where To Put Business Logic?

date: 2010-11-03T12:11:00+00:00
url: /mvc-where-to-put-business-logic/

categories:
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

I just had an email from a friend asking where business logic should go when using MVC &#8211; the controller or the model.

I thought I&#8217;d share my reply:

> I think asking whether the business logic should go in the Model or the Controller is a false dichotomy. There are different kinds of business logic, and there&#8217;s also the possibility of putting it somewhere else entirely.
> 
> Much business logic does indeed belong in the model, particularly stuff like encapsulating calculations and projections, adding meaning to raw data properties, and ensuring domain objects are maintained in a valid state. I see this as the traditional side of OO design &#8211; encapsulating logic and restricting accessibility.
> 
> Then at a higher level we have logic which deals with interactions between objects, which are essentially transactions and generally map to business use cases. I contend that this kind of logic belongs in a separate "service" layer. The interfaces in that service layer can then be referenced by the controllers, which are rendered super-skinny and free of any complex "business logic". The same service layer classes can be invoked from other front ends &#8211; Web Forms, Win Forms, WCF services, console apps, etc.
> 
> As a further aside, I&#8217;d recommend use of a view model or DTOs wherever possible rather than exposing the domain model objects up to the views / forms / console / service contracts etc. This encapsulates the domain model and increases the maintainability of the domain model.

What do you think?

<!--kg-card-end: html-->