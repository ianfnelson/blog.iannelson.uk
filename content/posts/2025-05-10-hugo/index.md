---
title: 'From WordPress to Hugo: A Return to Simpler Times'

date: 2025-05-10T22:44:00+01:00
url: /hugo

categories:
  - Tech

tags:
  - Blogging
  - Hugo
  - WordPress
  - Simplicity

---

![](https://blogstouks01.z33.web.core.windows.net/2025/05/Kenzie.png)

I know, I know, you've [heard](https://blog.iannelson.uk/back-and-trying-a-ghost-in-the-cloud/) all this [before](https://blog.iannelson.uk/here-we-go-again). Once again Ian is migrating his blog from one platform to another. And yes, it's true that I have spent more of my life converting my blog posts between different platforms and markup languages than I ever have actually writing the damn blog posts in the first place.

There's a certain pleasing symmetry to it. I began my blogging life in the late 1990s with nothing more than some hand-rolled HTML, a text editor, and a dial-up connection. Over the years I have moved my content over to various platforms: .Text, Community Server, WordPress (twice!), GraffitiCMS, Ghost, and now I find myself almost back where I began.

Not with hand-coded HTML, no, but with something close: [Hugo](https://gohugo.io/), the static site generator. A modern tool with old-world sensibilities. Fast, minimal, fiercely text-based. The kind of thing that makes you feel rather chuffed with yourself for avoiding a CMS and database.

## The Nudge

This time around the change wasn't purely for the fun of trying out a new platform, and it wasn't purely nostalgic. Like many tech migrations, it has been prompted by a small but decisive shift in nonfunctional requirements. I have recently closed my limited company after 17 years, and with that closure I lost my Microsoft Partner benefits, which had included $100/month in Azure credits. That, in turn, meant that I could no longer justify the modest but non-zero cost of keeping a Linux VM running 24/7 just to serve up WordPress.

And truth be told, I don't miss it. Keeping a server and WordPress patched felt increasingly out of proportion to the task of publishing the occasional blog post. In general I find that as I hurtle towards my fifties I have a new-found desire for [simplicity](https://blog.iannelson.uk/tags/simplicity) in my life, and seek to reduce the complexity of my [Algorithms To Live By](https://amzn.to/4ddpW5A).

So I shut it all down.

## Simpler Times, Static Pages

I now generate my blog using Hugo, deployed automatically via [GitHub Actions](https://github.com/features/actions) to an [Azure Static Web App](https://azure.microsoft.com/en-us/products/app-service/static) (on the free tier, naturally). The site regenerates in a blink, uploads itself automatically on every commit, and serves HTML with a kind of quiet efficiency that makes you wonder why you ever needed a MySQL database in the first place.

All my content lives in Markdown. No block editors, no HTML, no custom CSS. Just words and headings and the occasional image. Oh alright, and I have used a couple of Hugo shortcodes for embedding Youtube videos and [Gists](https://gist.github.com). It's all versioned in GitHub, and I write my posts in VSCode, just as nature intended.

![](https://blogstouks01.z33.web.core.windows.net/2025/05/VSCode.png)

The migration itself wasn't too painful — helped hugely by this [WordPress to Hugo Exporter](https://github.com/SchumacherFM/wordpress-to-hugo-exporter), followed by a bunch of regex-driven find and replace, and some bespoke tidying (which was actually quite soothing). I've now got a lean set of posts going back years, shorn of legacy cruft and published with a feather-light footprint.

## The Theme and the Mood

I'm using the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, which strikes a good balance between clarity and flexibility. I haven't done much in the way of customisation — nor do I particularly want to. That's kind of the point. Simplifying my life. The whole exercise is about reducing friction: to be able to write, publish, and think out loud without needing a ten-step deployment pipeline, a detour into CSS (not my strong suit), or being beholden to whatever WordPress was doing to my words.

## But Will It Stick?

The real question, of course, is whether this move to yet another platform will rekindle my blogging habit. I hope so. There's something appealing about the quiet permanence of a static site: no dashboards, no "distraction layer", just me and my words. I'm also at a point in my life where my kids need less of my time, and I've amassed quite a few war stories from life in the world of enterprise software development which I feel able to share.

I've come full circle, but this time the tools are better, and the reasons clearer. If you're thinking of [simplifying](https://blog.iannelson.uk/tags/simplicity) your online life, or just fancy a fresh start for your blog, I'd recommended giving Hugo a look.

