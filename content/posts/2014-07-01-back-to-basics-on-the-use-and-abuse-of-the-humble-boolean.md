---
title: 'Back To Basics: On The Use And Abuse Of The Humble Boolean'
author: ian
type: post
date: 2014-07-01T20:54:00+00:00
url: /back-to-basics-on-the-use-and-abuse-of-the-humble-boolean/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2014/07/iStock_000016008439Small.jpg
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

> &#8220;We who cut mere stones must always be envisioning cathedrals&#8221;
> 
> &#8212; Stonecutter&#8217;s creed

Consider for a moment, if you will, the humble Boolean. Taking only two possible values, it is the most basic of all the data types we programmers use, and its existence is fundamental to all the code we write. At the end of the day, when all is said and done, everything we do is just a big bunch of ones and zeroes.

I assert that this warm familiarity often causes us to make use of booleans when we really shouldn&#8217;t. In particular, I want to call out two specific uses of the boolean which I now consider to be anti-patterns and avoid wherever possible:

## Antipattern 1 &#8211; Methods that take boolean flag parameters {#antipattern-1-methods-that-take-boolean-flag-parameters}

We spend more time reading and interpreting code than we spend actually writing it. That line of code you&#8217;re absent-mindedly knocking out today will probably be read dozens of times by your colleagues and future developers. It behoves you to make your intentions as clear as possible at every opportunity. Ambiguity in code is a truly terrible thing. Don&#8217;t impede understanding of your intentions by using boolean parameters that at worst force the reader to navigate to the definition of the method being invoked, or at best require them to hover their mouse over the bool parameter to glimpse some intellisense insight.

An example &#8211; let&#8217;s take a look at a line of code which uses the NHibernate hbm2ddl tool to export the database schema:

<pre><code class="language-clike">new SchemaExport(cfg).Execute(false, true, false);</code></pre>

Quick &#8211; what do those trio of booleans do? It&#8217;s not remotely obvious and we are forced to consult the docs. How much nicer it would be if the API developers had opted instead to use a flags enumeration, similar to the RegexOptions enumeration in the System.Text.RegularExpressions namespace:

<pre><code class="language-clike">var regex = new Regex(@"^file://", RegexOptions.Compiled | RegexOptions.IgnoreCase);</code></pre>

More often, I encounter boolean parameters in the wild where a developer has been charged with enhancing an existing method to behave slightly differently in some particular circumstance, leading to method calls along the lines of:

<pre><code class="language-clike">var user = CreateUser(email, password, true);</code></pre>

What does the final parameter do? Again we have to rely on intellisense or navigating to the source. It&#8217;s too easy to add the boolean parameter and slow down everyone who follows in our wake. We should take the time to implement the correct solution, whether that be as simple as a separate method with a more specific name, or a polymorphic family of suitably-named classes that implement the same interface. This kind of boolean parameter, quick as it is to add, not only slows us down but is often symptomatic of a deeper flaw in the class design.

Don&#8217;t even get me started on the optional parameters introduced in C# 4.0. It&#8217;s all too easy to invoke methods without noticing the existence of optional parameters with surprising defaults which can cause unexpected consequences. A sprinkling of syntactic sugar that can act as a catalyst for code decay.

> &#8220;Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, loudly proclaiming that this function does more than one thing. It does one thing if the flag is true and another if the flag is false!&#8221;
> 
> &#8212; Robert C. Martin, [Clean Code][1]

As with many design principles, the visibility of the method is key in how problematic this code smell becomes. A boolean parameter on a private method, while a potential candidate for refactoring at a suitable time, is not the end of the world. But a boolean parameter on a public method, perhaps a member on a public interface, is a more pressing problem. Think very carefully before adding a boolean parameter to a method on a public API or other service boundary.

## Antipattern 2 &#8211; Methods that (unnecessarily) return booleans {#antipattern-2-methods-that-unnecessarily-return-booleans}

OK, so I&#8217;ve explained that I don&#8217;t much like methods that take boolean parameters. What about methods that return them?

Well, I am an advocate of [Command-Query Separation][2]. Generally, if a method returns a bool I&#8217;m going to assume that it&#8217;s free of side effects and is answering a query, like this:

<pre><code class="language-clike">bool canOrder = CanPlaceOrder(customer, order);</code></pre>

Conversely, when methods actually _do_ stuff (i.e. commands), I wouldn&#8217;t expect them to return anything at all, least of all a boolean.

OK, a couple of notable exceptions to this rule. I can just about cope with create/update methods returning an instance of the entity that has been saved, thus:

<pre><code class="language-clike">var user = CreateUser(email, password);</code></pre>

and I admit to having a soft spot for the TryParse pattern where we expect the happy path to succeed on most occasions:

<pre><code class="language-clike">if (int.TryParse(value, out accountId)) { ... }</code></pre>

but booleans returned from methods that perform commands? Well that&#8217;s just pointless and confusing. Consider the method signature:

<pre><code class="language-clike">public bool CreateUser(string email, string password)</code></pre>

Why return a bool? What does it mean? That the method call was successful? Then why bother mentioning it?  
If there is a problem of some kind (say, a user already exists with the specified email address), then throw a suitable exception with the necessary detail that I can choose to catch, log or allow to bubble up as I see fit. By returning a boolean, consumers of the method now need to both catch exceptions _and_ inspect the return value (and what action would be appropriate anyway when faced with a context-free &#8220;false&#8221; return value?)

Command methods that return booleans feel like insecure children who need to boast of their every achievement. **It&#8217;s OK to return void.** Nobody will think any the less of you for simply doing what was asked and keeping quiet. Unix commands have been silently going about their business for years, and I feel that is an ethos that we developers should try to emulate. The era of the contrived return value that has to be dissected for meaning is long gone. Doing what was asked if possible, else throwing an appropriate exception is the twenty-first century way.

<!--kg-card-end: html-->

 [1]: http://amzn.to/1lPJsXv
 [2]: http://en.wikipedia.org/wiki/Command%E2%80%93query_separation