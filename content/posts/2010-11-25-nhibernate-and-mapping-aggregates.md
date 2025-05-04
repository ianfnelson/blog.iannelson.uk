---
title: NHibernate and Mapping Aggregates

date: 2010-11-25T08:11:00+00:00
url: /nhibernate-and-mapping-aggregates/

categories:
  - Tech
tags:
  - NHibernate
  - .NET

---

A few days ago a friend emailed me the following question regarding NHibernate mappings for a solution he’s currently developing:

> &ldquo;I have an idea entity that has a collection of comment entities and I need to get the comment count for each idea. I made a massive mistake at the beginning by calling idea.Comments.Count (even worse, I did it in the view!), which due to the collection being lazy-loaded caused about 10 database calls so performance was sluggish even with second level cache. I was therefore wondering how you would do it – would you use HQL and use Comments.size or would you do something differently?&rdquo;

Now, I&rsquo;ve been pretty busy recently, so before I had opportunity to respond properly, he sent this follow-up:

> "After looking for a solution for getting a Comment count back for each Idea, I found using the Nhibernate Formula method does the job – just wanting to make sure I was on the right track in terms of performance etc. My mapping class is as follows:"
>
>

I considered this for a while, and sent the following suggestions:

> &ldquo;I’m glad to hear you resolved your SELECT N+1 problem but to be honest, I’m not a big fan of using formulas in NH mappings if at all possible, for the following reasons:
>
> 1. I try to minimize my use of strings (and especially SQL) so as to make refactorings easier, and lessen the potential for runtime exceptions.
> 2. The default NH behaviour will be to evaluate that formula every time an Idea entity is loaded, which might not be desirable and could negatively impact on performance when loading your idea entities. I’m not sure if the recently-added [Lazy Properties feature][1] of NH can be applied to these derived properties; if so then that could be used to negate this argument.
> 3. I try to avoid putting logic (however simple) in the OR mapping layer, as future developers are unlikely to expect to find it there! I like to reduce the element of surprise in my solutions, and put such logic in the domain layer. I think logic in the OR layer limits options going forward – for example if you subsequently decide all comments have to be moderated, does the CommentCount formula have to be modified to exclude comments awaiting moderation..?
>
> So, what would I do? Here are two options, depending on how often you’re using the CommentCount property:
>
> If you’re only using the CommentCount occasionally and only along with a subset of the other properties from Idea, then I would write a specific query returning a projection of the required properties, including this CommentCount aggregate.
>
> I’ve done this in the past where I had a requirement to populate a drop-down list with user names and the number of open work items assigned to each user, for example. I didn’t want or need to maintain an ActiveWorkItemCount property on the user object, I just wanted to do the calculation in one place (incidentally, LINQ made this a doddle).
>
> Conversely, if the CommentCount property is something you’re going to be referencing frequently, then I would denormalise the database and add a CommentCount field to the Idea table. This presumes that you’re in a position to enforce the constraint that new Comments are only added to Ideas through your application (and as you know from [my recent blog post][2], I am very fond of this kind of constraint!). This approach should give the best performance and flexibility, at the expense of irking normalisation fascists.
>
> Typically this would be done by creating AddComment and RemoveComment helper methods on the Idea entity, which can maintain a bidirectional relationship between Idea and Comment in addition to incrementing or decrementing CommentCount accordingly.
>
> This approach will give the best performance, and keeps the logic where it belongs (and where it can be easily extended and tested, as in my earlier hypothetical comment moderation example).
>
> For a good example of code to maintain bidirectional one-to-many class relationships with NHibernate, see pages 39-43 of [NHibernate 3.0 Cookbook][3].
>
> Hope this helps. As ever, it’s just my opinion, but these two techniques have worked well for me.&rdquo;

What do you think? Are there any other approaches worth considering?

 [1]: http://ayende.com/Blog/archive/2010/01/27/nhibernate-new-feature-lazy-properties.aspx
 [2]: https://blog.iannelson.uk/enterprise-integration-anti-patterns-1-the-shared-database/
 [3]: http://bit.ly/c9oPqi