---
title: Who Reigns Supreme? Parsing Our WhatsApp Chat for Wordle Glory

date: 2024-12-31T15:42:39+00:00
excerpt: 'Discover how I used C# to parse our family WhatsApp chat and crown our 2024 Wordle Champion!'
url: /who-reigns-supreme-parsing-our-whatsapp-chat-for-wordle-glory/
cover: 
  image: https://blogstouks01.z33.web.core.windows.net/2024/12/0277568D-75C1-4425-8F5B-48DD1EFE2A7E.jpeg

categories:
  - Family
  - Fun

---
Back in 2022, in a bid to outwit my mother in our daily Wordle battles, I wrote some C# code to explore optimal starting guesses. [You can read about that experiment&nbsp;here][1].

Fast forward two years, and my Wordle addiction is alive and well. The daily challenge remains as compelling as ever, but it’s the family WhatsApp group – where scores are shared, victories boasted, and failures commiserated – that adds an extra layer of fun.

As 2024 winds down, I decided to dust off my coding skills and whip up a quick C# console application. The goal? To parse an export of our WhatsApp chat, gather all the shared Wordle scores, and find out if my strategies have paid off this year. Spoiler alert: they haven’t.

If you’ve got a similar Wordle-centric group chat with family or friends and fancy crowning your own Wordle Champion of the Year, the source code is available on GitHub:&nbsp;[WordleParser][2].

## How It Works 

The application takes a single argument: the path to an exported chat text file. It parses the file using a [regular expression][3] to extract anything resembling a Wordle score. [Duplicate scores are weeded out][4], and the [average family score for each calendar day is logged][5]. For those unfortunate days when a puzzle remains unsolved, the application [assigns a ‘seven’][6] to reflect the failure.

The app then aggregates scores into calendar [months][7] and [years][8], [calculating each family member’s stats for the chosen date range][9]. Participants are ranked based on their mean difference from the average family score per day.

For example, if three family members scored a 4, but one managed a dazzling 2, the day’s average would be 3.5. The three “fours” would each have a daily difference of +0.5, while the lucky “two” would boast a difference of -1.5.

## The Results 

So, who triumphed in the Nelson family Wordle-off this year? Did my painstaking analysis from 2022 finally give me the edge?

Reader, it did not.

Despite my best efforts, I only just managed to sneak into second place. Predictably, my mother reigned supreme, crushing us all with an average score of&nbsp;**4.055**&nbsp;and a mean difference from the family average of&nbsp;**-0.128**. This consistency made her our undisputed&nbsp;**Wordle Family Champion of 2024**.<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" width="1024" height="1024" src="https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1.jpeg" alt="" class="wp-image-10309" srcset="https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1.jpeg 1024w, https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1-300x300.jpeg 300w, https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1-150x150.jpeg 150w, https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1-768x768.jpeg 768w, https://blogstouks01.z33.web.core.windows.net/2024/12/7DD41AB4-B664-4276-B1A1-3E9EA0F0DFB7-1-600x600.jpeg 600w" sizes="auto, (max-width: 1024px) 100vw, 1024px" /> <figcaption class="wp-element-caption">_Image generated using OpenAI’s DALL·E tool._</figcaption></figure>

 [1]: https://blog.iannelson.uk/the-best-wordle-starter-words/
 [2]: https://github.com/ianfnelson/WordleParser
 [3]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L46
 [4]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L27
 [5]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L32
 [6]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L59
 [7]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L17
 [8]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L11
 [9]: https://github.com/ianfnelson/WordleParser/blob/main/WordleParser/WordleParser.cs#L76