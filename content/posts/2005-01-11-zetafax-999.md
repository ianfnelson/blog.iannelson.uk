---
title: 999999999..
date: 2005-01-11T23:01:00+00:00
url: /zetafax-999/

categories:
  - Fun
  - Tech
tags:
  - Bugs

---
Never underestimate the stupidity of users—or the benefits of a little field validation.

One of the web-based systems I’ve been developing allows users to enter a customer’s fax number and automatically fax confirmation details (using Zetafax). It’s been working pretty well—until we discovered a flaw today. One user, tired of obtaining valid fax details from customers, had been entering a string of nines and then actually attempting to send the fax to this number.

We first learned of this issue today, when West Yorkshire Police asked us to stop trying to send faxes to the emergency services!