---
title: "When the System Doesn't Work, You Become It: Scanned Notes from My Daughter's Hospital Bedside"
date: 2025-05-26T13:00:00+01:00
url: /when-the-system-doesnt-work-you-become-it
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2025/05/IMG_9731_720.jpeg

categories:
  - Family
  - Tech
  - Society
tags:
  - Healthcare
  - Integration
  - Systems

---

In the early hours of Sunday morning, my daughter [Isla](http://blog.iannelson.uk/isla-grace-nelson) was admitted to hospital with tonsilitis so severe she could no longer swallow. As a parent, it was a worrying time. As a tech lead working on national health infrastructure, it was quietly illuminating.

I'm currently helping to build the National Screening Platform for NHS England — a set of systems designed to make the flow of patient data smoother, more interoperable, and ultimately more useful, hopefully leading to cost savings and better health outcomes for the country's citizens. But this weekend, I wasn't a developer or a technical architect. I was just a sleep-deprived dad, waiting anxiously by a bedside.

As an aside, I noticed something strange happening in my own thinking during this experience. Before admission to hospital, I was desperately hoping that the doctors would take Isla's condition seriously — that they'd see what we saw, and agree that she needed hospital care. But once she was admitted, I almost immediately began yearning for the opposite: that a doctor would say she was now well enough to go home again.

I've decided that this emotional shift deserves a name, and so I give you:

> **The Admission Paradox**
>
> _The psychological shift in parents or caregivers who, prior to a hospital admission, hope clinicians will take their child's illness seriously enough to admit them – but, once admitted, begin immediately hoping the child is well enough to be discharged._

It's the whiplash of parental vigilance. And it's made worse when the systems around you don't seem to be helping.

## "Has she got a social worker?"

We've been asked the same questions repeatedly this weekend. Different departments, different nurses, sometimes working within 50 metres of each other. Always kind and diligent, but always with a fresh paper form, to be filled in by hand with a biro. Name, date of birth, allergies, medications, safeguarding flags, etcetera.

On multiple occasions we were asked whether Isla had a social worker. We said no, truthfully. But I found myself wondering: _what if we hadn't been?_ Was there a cross-check, a shared record, a single source of truth? It felt like each clinician was building their own little silo of context.

At another point a nurse in the emergency department said, "I'll just scan your notes", which I assume meant feeding handwritten pages into a scanner and uploading them into a system as PDFs. Would they be OCR'd and searchable? I doubted it. They're certainly not structured data. They're digital in the same way a photocopy is digital.

## A Flicker of the Future

Not all of the weekend was like this. At some points I could glimpse systems integration at work. A&E reception needed only Isla's surname and date of birth to pull up some basic records — presumably via a [PDS](https://digital.nhs.uk/services/personal-demographics-service) lookup. A Pharmacy First journey earlier on Saturday, before Isla's condition worsened, seemed similarly joined-up.

## And Then, the Private Sector

By comparison, on Saturday afternoon, just hours before Isla's hospitalisation, I had a regular eye test at Specsavers. The optometrist had notes from a visit I'd made to an eye clinic in 2012, so was aware that my high pressure readings were just due to having unusually thick corneas, and no sign for concern. Then he brought up a digital scan of my retina from ten years ago and overlaid it with this year's image to show me that a mole on the back of my eye hadn't changed shape.

A private provider, operating at national retail scale, able to retrieve a decade-old scan, align it with new data, and present the comparison to me in realtime. It was seamless, personal, and context-rich. I suppose it helps that I have been attending the same chain for years.

Meanwhile, at the hospital that evening, I felt like I was Isla's integration layer — repeating myself patiently at every handover, carrying information in my head or in iCloud, unable to be certain that anything I'd said to one nurse would necessarily be available to the next.

## The View from Both Sides

My day job right now is to build systems that improve some of this — liberating data from decades-old siloed systems, integrating it with other data sources, and empowering citizens to gain visibility of their own healthcare data through the [NHS App](https://www.nhsapp.service.nhs.uk/). We're trying to build not just a single product, but a foundational platform for the future.

But this weekend, sitting in a wipe-clean chair next to a sick child, I'm not thinking about event contracts, database schemas or validation rules. I'm thinking _Why are Jocelyn and I the only ones who know this stuff? Why does no one else have the full picture?_

## Why This Matters

This isn't a complaint about the people. The NHS staff we have encountered this weekend were great — overworked, underpaid, and unfailingly kind and patient. But the systems that they're working with are often out of step with the levels of care they're trying to deliver. As a result, patients and families often have to make up the difference.

We're not short of good intentions. But we are short of shared data models. Of interoperability. Of pragmatic, patient-facing tools that put context and data where they're needed. And we're falling behind providers who _can_ offer that, because they've invested in modern infrastructure and are incentivised to improve user experience.

I know the NHS can do this. I've been delighted to see pockets where it already is. But the unevenness, especially the fallback to using paper, is striking, and lived experience makes it harder to ignore.

There's an indignity in having to repeat yourself during a crisis. A sense that, while you're trying to stay calm and advocate for your child in the middle of the night, you're also acting as the courier for a dataset that should already be connected.

But it also renews my belief in the work we're doing. Because when the system works, you barely notice it. And when it doesn't, **you become it**.