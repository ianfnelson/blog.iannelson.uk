---
title: Inheriting From BaseValidator to Make Custom Validation Controls

date: 2004-06-30T19:06:00+00:00
url: /inheriting-from-basevalidator-to-make-custom-validation-controls/

categories:
  - Tech
tags:
  - .NET

---

For months now, I’ve been desperate for a decent excuse to make a custom ASP.NET server control, so I was secretly pleased today when a CustomValidator originally coded for use on a single page was required elsewhere.

It’s surprisingly easy to do, although it took me a while to find a decent example online, which eventually came courtesy of the [4GuysFromRolla][1]. In my particular scenario, I needed to check that the text entered into a TextBox did not equal any of a selection of "banned" strings (which was available via a static property on another class).

Having added a new custom web control, deriving from BaseValidator, my first task was therefore to ensure that the control being validated really was a TextBox – this was done by overriding the `ControlPropertiesValid()` method:

{{< gist 9842442 ControlPropertiesValid.cs >}}

That done, I just had to override the `EvaluateIsValid()` method, which does the actual validation:

{{< gist 9842442 EvaluateIsValid.cs >}}

...and that was it. Job done, pretty much. OK, so I spent a while making a cute icon image too. But the coding was easy and straightforward – inheriting from BaseValidator meant that most of the work was already done for me. In no time at all I was able to drop this custom control onto the required pages and user controls.


 [1]: http://www.4guysfromrolla.com/webtech/tips/t040302-1.shtml