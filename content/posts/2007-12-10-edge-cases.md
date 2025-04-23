---
title: Edge Cases

date: 2007-12-10T14:12:00+00:00
url: /edge-cases/

categories:
  - Fun

---
Ten years of professional software development have given me a healthy awareness of edge cases – I’m always trying to code defensively, validate input, catch exceptions, use assertions, and of course pick holes in sloppy specifications (“ah, but what if&#8230;”).

I must learn that these skills should not always be applied to my personal life though, as exemplified by a conversation with The Wife yesterday:

* * *

_Jocelyn (excitedly): “We’re going to have a &#8216;Secret Santa’ for all the babies in our antenatal group!”_

_Me: “Huh. How does that work then?”_

_Jocelyn: “Well, we each buy a gift for under £10, put them into a bag, and each pick one.”_

_Me: “What happens if you pick out the gift you bought?”_

_Jocelyn (less excitedly): “Well, you put it back and pick another.”_

_Me: “So, you have an even number of babies in the group?”_

_Jocelyn (testily): “There are seven.”_

_Me: “Then what happens if the last person picks their own gift?”_

_Jocelyn (deflated): “Ian&#8230;!  OK, so we won’t open any gifts until they’re all selected – happy now?”_

* * *

I was. In my mind this is like recursively calling an algorithm if a post-check fails. It’s an unusual approach, but it should work OK here.