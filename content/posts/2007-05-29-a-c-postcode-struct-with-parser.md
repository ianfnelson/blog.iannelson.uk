---
title: 'A C# Postcode Struct with Parser'

date: 2007-05-29T12:05:00+00:00
url: /a-c-postcode-struct-with-parser/
cover: 
  image: https://cdn.iannelson.uk/uploads/2007/05/iStock_000003192621XSmall-1.jpg

categories:
  - Tech
tags:
  - tidy

---
<figure class="kg-card kg-image-card"><img decoding="async" src="https://cdn.iannelson.uk/uploads/2023/08/iStock_000003192621XSmall.jpg" class="kg-image" alt loading="lazy" /></figure> 

As [discussed recently][1], I’ve been trying to knock together a class struct to represent a UK postcode, provide a means of parsing a string as _potentially_ being a valid postcode (or optionally just an outer code), and split that postcode into &#8220;outer&#8221; and &#8220;inner&#8221; code.

I say _potentially_ because, as you’ll know if you’ve looked into this topic at all, it’s impossible to validate whether a string truly does represent a postcode without querying the (copyrighted and expensive-to-license) Postcode Address File.  As a result, my solution is not very stringent &#8211; it is possible to persuade it to successfully parse an invalid postcode, but hopefully there should be no occasions when a valid postcode is rejected.

The code validates strings by checking for compliance with the standards defined in [BS7666][2], followed by checking for BFPO postcodes, and finally for a handful of notable exceptions (e.g. Girobank).  If you know of any valid postcodes that are rejected by this routine, do let me know.

Oh, and incidentally, this was the first time I’ve used Visual Studio Orcas in anger to develop anything meatier than a Hello World.  Although I wasn’t exactly pushing the technological envelope, I found the IDE to be pretty fast and stable, considering it’s a beta 1.

Source available on GitHub at <https://github.com/ianfnelson/Postcode>

 [1]: https://blog.iannelson.uk/postcode-validation/
 [2]: http://www.govtalk.gov.uk/gdsc/html/frames/PostCode.htm