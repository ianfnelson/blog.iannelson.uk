---
title: 'TFS: Using Alternative Diff/Merge Tools'

date: 2009-05-19T07:05:00+00:00
url: /tfs-alternative-diff-merge-tools/

categories:
  - Tech
tags:
  - TFS
  - Software

---
There are many things I love about Team Foundation Server, but the supplied diff/merge tool is not one of them. It is – how can I put this? – somewhat basic. Indeed, I’ve heard tell of people going out of their way to avoid merges purely because they find the process so clunky.

Here’s the good news – you can easily configure TFS to use a different, third-party, diff/merge tool, perhaps the one you’ve grown to know and love over many years of happy software development using other SCM products. Maybe you like [WinMerge][1], or love [TortoiseMerge][2]. Perhaps you’re like my friend [John][3] and swear by [SourceGear DiffMerge][4]. Or maybe, like me, you’re a [Beyond Compare][5] fanboy. No problem, they can all be used by TFS. Here’s how:

* Open up the Visual Studio options (**Tools** –> **Options**).
* Expand the **Source Control** –> **Visual Studio Team Foundation Server** section.
* Click the **Configure User Tools…** button:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/dm1_4.png)

* Click the **Add…** button to set up a new file extension operation:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/dm2_2.png)

* Set up a **Compare** operation to run against all files (extension of *:

![](https://blogstouks01.z33.web.core.windows.net/2023/08/dm3_3.png)

* Repeat the process to add a **Merge** operation to run against all file extensions.

At this point, you’re probably thinking “wooah, what do those argument parameters mean? How do I know what to enter?”. MSDN won’t help you out (“[type any arguments that your tool requires][6]” – thanks for that!).

Fortunately [James Manning][7] has posted [a blog article][8] which not only explains what the argument parameters mean, but also suggests recommended parameters for various popular tools, including those mentioned at the beginning of this post. Thanks, James!

Voila! **OK** your way back out of the dialog boxes, and your Compares and Merges will now be displayed using your favourite Diff/Merge tool. Feel your productivity and confidence soar!

 [1]: http://winmerge.org/
 [2]: http://tortoisesvn.tigris.org/TortoiseMerge.html
 [3]: http://www.johnsadventures.com
 [4]: http://www.sourcegear.com/diffmerge/downloads.html
 [5]: http://www.scootersoftware.com/
 [6]: http://msdn.microsoft.com/en-us/library/ms181446.aspx
 [7]: http://blogs.msdn.com/jmanning/default.aspx
 [8]: http://blogs.msdn.com/jmanning/articles/535573.aspx