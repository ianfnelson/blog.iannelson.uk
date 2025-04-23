---
title: Edge Cases

date: 2007-12-10T14:12:00+00:00
url: /edge-cases/

categories:
  - Fun

---
Ten years of professional software development have given me a healthy awareness of edge cases &#8211; I’m always trying to code defensively, validate input, catch exceptions, use assertions, and of course pick holes in sloppy specifications (&#8220;ah, but what if&#8230;&#8221;).

I must learn that these skills should not always be applied to my personal life though, as exemplified by a conversation with The Wife yesterday:

* * *

_Jocelyn (excitedly): &#8220;We’re going to have a &#8216;Secret Santa’ for all the babies in our antenatal group!&#8221;_

_Me: &#8220;Huh. How does that work then?&#8221;_

_Jocelyn: &#8220;Well, we each buy a gift for under £10, put them into a bag, and each pick one.&#8221;_

_Me: &#8220;What happens if you pick out the gift you bought?&#8221;_

_Jocelyn (less excitedly): &#8220;Well, you put it back and pick another.&#8221;_

_Me: &#8220;So, you have an even number of babies in the group?&#8221;_

_Jocelyn (testily): &#8220;There are seven.&#8221;_

_Me: &#8220;Then what happens if the last person picks their own gift?&#8221;_

_Jocelyn (deflated): &#8220;Ian&#8230;!  OK, so we won’t open any gifts until they’re all selected &#8211; happy now?&#8221;_

* * *

I was. In my mind this is like recursively calling an algorithm if a post-check fails. It’s an unusual approach, but it should work OK here.