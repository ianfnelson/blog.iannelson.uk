---
title: Postcode Validation

date: 2007-05-23T13:05:00+00:00
url: /postcode-validation/

categories:
  - Fun
  - Tech
tags:
  - tidy

---
<!--kg-card-begin: html-->

Wikipedia cracks me up sometimes. I’m sat here at my desk, trying to knock together some C# code to quickly validate an entered string as being a UK postcode. Naturally I turned to this [Wikipedia article][1] for assistance, where I find this quip:

> _"Automatic validation of postcodes on the basis of pattern feasibility is therefore almost impossible to design, and the system contains no self-validating feature such as a check digit. **Completely accurate validation is only possible by attempting to deliver mail to the address, and verifying with the recipient.**"_

I think that’s what is known as a [long-running transaction][2]!!

**Update** &#8211; the C# code that I wrote to handle this issue is available [here][3].

<!--kg-card-end: html-->

 [1]: http://en.wikipedia.org/wiki/UK_postcodes
 [2]: http://en.wikipedia.org/wiki/Long_running_transaction
 [3]: https://blog.iannelson.uk/a-c-postcode-struct-with-parser/