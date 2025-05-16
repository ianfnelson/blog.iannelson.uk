---
title: Testing LINQ Queries

date: 2010-04-09T13:04:00+00:00
url: /testing-linq-queries/

categories:
  - Tech
tags:
  - Testing
  - .NET

---
I’ve been asked “How do you test LINQ queries?” a couple of times in the past few months, so I thought I’d blog my answer for the benefit of all you lovely people.

Firstly I should explain how I’ve been doing most of my data access in recent months. I find that the [Repository pattern][1], and particularly the [.NET implementation described here by Fabio Maulo][2] meets the vast majority of requirements I have in my applications, and I fall back on additionally using custom DAOs when required.

So, my service classes can ask the IoC container for instances of `IRepository<T>`, where `IRepository<T>` implements `IQueryable<T>`.

Now, in the best tradition of encapsulation, all but the most trivial of the queries I write against these repositories are defined in extension methods, for example:

{{< gist 0fd94841097a75fa9d58 TL1.cs >}}

Aside from the testability aspect (which I promise I’ll get onto in a second), this approach also helps keep us on the right side of the [Law of Demeter][3], as [Garry Shutler blogged about recently][4]. It also allows for method chaining, allowing us to enact multiple filters and other transformations in a single line of code:

{{< gist 0fd94841097a75fa9d58 TL2.cs >}}

But I digress. I was talking about how to test these LINQ queries. It’s easy really, the trick is knowing that `IEnumerable<T>` offers an [`AsQueryable()` method][5]. So, we can build up some dummy data in a `List<T>` before calling `AsQueryable()` to obtain an object against which the extension method can act. Dead simple. The creation of the test data can even be automated using the open source [NBuilder][6] tool.

One caveat – this is merely testing that your LINQ query does what you think it should do, it doesn’t test the behaviour of the underlying LINQ provider. If you’re using, say, the NHibernate LINQ 1.0 provider (which is great but not at all feature-complete) then you’ll also need to write some suitable integration tests, say by testing against the [Sqlite][7] database engine.

 [1]: http://martinfowler.com/eaaCatalog/repository.html
 [2]: http://fabiomaulo.blogspot.com/2009/09/repository-or-dao-repository.html
 [3]: http://en.wikipedia.org/wiki/Law_of_Demeter
 [4]: http://blog.robustsoftware.co.uk/2010/04/linq-and-law-of-demeter.html
 [5]: http://msdn.microsoft.com/en-us/library/bb908285(v=VS.90).aspx
 [6]: http://nbuilder.org/
 [7]: http://sqlite.org/