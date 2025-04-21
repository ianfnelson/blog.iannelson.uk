---
title: NHProf – NHibernate Profiler

date: 2009-05-19T17:05:00+00:00
url: /nhprof-nhibernate-profiler/
cover: 
  image: https://cdn.iannelson.uk/uploads/2009/05/nh1_2-1.png

categories:
  - Tech
tags:
  - tidy

---
The inimitable [Ayende Rahien][1] is close to releasing version 1.0 of his [NHibernate Profiler][2] tool, and it really is shaping up to be a rather lovely little addition to my developer toolbox.

In much the same way that we can use [SQL Server Profiler][3] to monitor database activity, and [ANTS Profiler][4] to monitor the performance and memory usage of .NET applications, NHProf profiles the activity of the data access layer ([NHibernate][5]), and even goes as far as providing helpful hints for potential improvements.

NHibernate is powerful object relational mapper, but has a (perhaps deserved) reputation for having a steep learning curve. One of its major benefits is that it abstracts away much of the drudgery of writing data access code from the developer, but as an unfortunate side effect of this it can make it easy to create inefficient data access layers.

NHProf aims to reduce this risk by providing:

“Cognitive application awareness.

Visual insight into the interaction between your database and application code.

Analysis and detection of common pitfalls when using NHibernate.”

Sounds good, doesn’t it? So what does that mean in practice?

Here’s a screenshot of the release candidate. Note that the Session Factory Statistics functionality is disabled in the current build.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh1_2.png" class="kg-image" alt loading="lazy" /> </figure> 

Each profiled NHibernate session can be selected individually from the pane in the top left, and from there we can drill down to see the details of each SQL statement executed against the database (formatted in nice readable manner), along with details of any parameters, and even an option of viewing the rows resulting from the statement.

The statements are interpreted, and suggestions and warnings are flagged as alerts, along with hyperlinks to online guidance explaining how the data access can be improved.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh2_2.png" class="kg-image" alt loading="lazy" /> </figure> 

A stack trace is also provided for each statement, allowing us to identify the code that caused the data access to occur. It’s possible to double-click on a row within this trace to jump straight to the code in Visual Studio.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh3_2.png" class="kg-image" alt loading="lazy" /> </figure> 

In addition to showing the SQL statements executed by each session, details of the entities loaded by each session are also given.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh4_2.png" class="kg-image" alt loading="lazy" /> </figure> 

…and there’s a summary of the NHibernate usage for each session.<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh5_2.png" class="kg-image" alt loading="lazy" /> </figure> 

As well as providing session-by-session detail of what’s happening, NHProf allows us to analyse the overall activity. Here, I’m looking at unique queries containing the string “study” (note that differing parameters don’t count towards “uniqueness”):<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh6_2.png" class="kg-image" alt loading="lazy" /> </figure> 

We can also obtain analysis by Method, Url (for web applications) and Overall Usage statistics:<figure class="kg-card kg-image-card">

<img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/nh7_2.png" class="kg-image" alt loading="lazy" /> </figure> 

In my opinion NHProf has the potential to become an essential tool when creating or maintaining a solution which leverages the power of NHibernate. In addition to highlighting performance and other issues, it is a great aid when learning about NHibernate, or when familiarising oneself with an inherited solution. Overall, it’s the next best thing to having Ayende sat by your side lending a guiding hand.

 [1]: http://www.ayende.com
 [2]: http://www.nhprof.com
 [3]: http://msdn.microsoft.com/en-us/library/ms181091.aspx
 [4]: http://www.red-gate.com/products/ants_performance_profiler/
 [5]: http://nhforge.org