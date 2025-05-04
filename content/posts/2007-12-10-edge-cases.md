---
title: Edge Cases
date: 2007-12-10T14:12:00+00:00
url: /edge-cases/
categories:
  - Fun

---
Ten years of professional software development have given me a healthy awareness of edge cases – I’m always trying to code defensively, validate input, catch exceptions, use assertions, and of course pick holes in sloppy specifications (“ah, but what if…”).

I must learn that these skills should not always be applied to my personal life though, as exemplified by a conversation with The Wife yesterday:

> _Jocelyn (excitedly): “We’re going to have a 'Secret Santa' for all the babies in our antenatal group!”  
> Me: “Huh. How does that work then?”  
> Jocelyn: “Well, we each buy a gift for under £10, put them into a bag, and each pick one.”  
> Me: “What happens if you pick out the gift you bought?”  
> Jocelyn (less excitedly): “Well, you put it back and pick another.”  
> Me: “So, you have an even number of babies in the group?”  
> Jocelyn (testily): “There are seven.”  
> Me: “Then what happens if the last person picks their own gift?”  
> Jocelyn (deflated): “Ian…!  OK, so we won’t open any gifts until they’re all selected – happy now?”  


I was. In my mind this is like recursively calling an algorithm if a post-check fails. It’s an unusual approach, but it should work OK here.