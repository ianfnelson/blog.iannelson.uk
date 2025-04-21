---
title: The Best Wordle Starter Words

date: 2022-01-18T19:00:00+00:00
excerpt: "What are the best words to use as starting guesses when playing Josh Wardle's popular game Wordle? I've crunched the numbers."
url: /the-best-wordle-starter-words/
featured_image: https://blog.iannelson.uk/wp-content/uploads/2022/01/photo-1583334648584-6c2ba1fb41cd.jpg

categories:
  - Fun

---
Like (it would seem) most of the rest of humanity, the start of my 2022 has been immeasurably enhanced by starting each day playing [Josh Wardle&#8217;s][1] charming word game [Wordle][2]. Which got me wondering &#8211; what are the best starter words to play in the opening lines at Wordle? I have been habitually using &#8220;**ADIEU**&#8221; as my starter word, reasoning that it contains a large number of vowels. But is **D** a particularly common consonant? And should I be trying to get **O** in there rather than the less frequently used **U**? I decided to do some computer-aided analysis to find the answer.

_**SPOILER WARNING** &#8211; this blog post contains information that may lead you to play more optimal Wordle starter words than you otherwise would have done if left to your own imagination. If you consider that this may take the fun out of an enjoyable daily practice, then I suggest that you stop reading. Now._<figure class="wp-block-image">

<img decoding="async" src="https://blog.iannelson.uk/wp-content/uploads/2023/08/photo-1512799906445-d591d53082c0cropentropyampcstinysrgbampfitmaxampfmjpgampixidMnwxMTc3M3wwfDF8c2VhcmNofDR8fGNsb3NlZCUyMGV5ZXN8ZW58MHx8fHwxNjQyNTM4MzU2ampixlibrb-1.2.jpg" alt="blindness" /> <figcaption class="wp-element-caption">Photo by [Ryoji Iwata][3] / [Unsplash][4]</figcaption></figure> 

## Definition {#definition.wp-block-heading}

Still here? OK, first a definition. What do I consider to be a good Wordle starter word? What makes one starter word better than another?

I assert that the best Wordle starter words are those which are expected to result in the highest number of yellow (right letter, wrong spot) or green (right letter, right spot) tiles. Let&#8217;s call this E(Y|G). &nbsp;As a tie-breaker, where two words have the same value of E(Y|G), I consider the better word to be the one which is expected to result in the highest number of green tiles &#8211; let&#8217;s call this E(G).

I&#8217;ve seen alternative approaches posted on Twitter that rank guesses in different ways, such as one which was based on how many possible answers from the Wordle corpus are excluded by guessing them. But my brain doesn&#8217;t work that way round &#8211; I don&#8217;t have the full list of Wordle words in my head to sieve through, and instead seek the positive reinforcement of yellow and green tiles to use as the basis for my later guesses.

## Assumption {#assumption.wp-block-heading}

There are 12,972 valid words in the Wordle dictionary. For the purposes of this analysis, I&#8217;m going to assume that they all have an equal likelihood of being the Wordle answer on any given day. Clearly this is not true. I&#8217;ve only been playing Wordle for a couple of weeks but it&#8217;s immediately apparent that the winning words tend to be those in common everyday use. I doubt that the game would have its current levels of popularity were this not the case. My nine year old son loves playing Wordle every day, and this shared common bond is one of the things that makes Wordle so fun. There was quite some brouhaha on Twitter when the answer to Wordle 207 was the US English spelling of &#8220;**FAVOR**&#8220;, I can only imagine what an uproar there would be if the answer was ever something truly random like &#8220;**QAJAQ**&#8220;, &#8220;**XYLYL**&#8221; or &#8220;**HYPHY**&#8220;. But I digress. Whatever aspects of curation are taking place to select the daily Wordle, be it automated or human, I&#8217;m going to ignore it and assume that the Wordle is chosen randomly from the list of valid Wordle words.

## The Top 10 Best Wordle Starter Words {#the-top-10-best-wordle-starter-words.wp-block-heading}

This is your last chance to look away. Having iterated through all 168,272,784 pairs of guessed word and answer, here are the ten best Wordle starter words

<pre class="wp-block-preformatted">Rank   Word    E(Y|G)    E(G) 
1.     AEROS   1.91111   0.63360 
2.     SOARE   1.91111   0.55026 
3.     AROSE   1.91111   0.36294 
4.     REAIS   1.88629   0.64215 
5.     RAISE   1.88629   0.46099 
6.     SERAI   1.88629   0.44288 
7.     ARISE   1.88629   0.36741 
8.     AESIR   1.88629   0.34312 
9.     ALOES   1.84983   0.67175
10.    LARES   1.84968   0.79579</pre>

Therefore, if you want to turn over the highest number of yellow and green tiles on your first Wordle play, and favour seeing the green tiles, then &#8220;**AEROS**&#8221; is your best bet. By comparison my previous favourite of &#8220;**ADIEU**&#8221; has an E(Y|G) of 1.49229 and E(G) of 0.32886.

## The Best Words To Play Second {#the-best-words-to-play-second.wp-block-heading}

But what comes next? What words are best to play on the second line? It depends how you like to play the game. If you&#8217;re like my mother, or have &#8220;hard mode&#8221; turned on, then your second and subsequent guesses will be influenced by the hints received in response to your first guess.

On the other hand, if you&#8217;re like me, at this early stage you&#8217;ll want to continue exploring the full breadth of the alphabet to increase the probability of identifying additional letters in the answer. For example I have generally been following up my &#8220;**ADIEU**&#8221; starter with &#8220;**GHOST**&#8221; to finish off the vowels and include **T** and **S** in the mix.

With this in mind, I extended my analysis to determine the combined E(Y|G) and E(G) values for pairs of valid Wordle words. All of the best results came from pairing together words that cover 10 distinct letters. Perhaps that seems intuitive, but it wasn&#8217;t a foregone conclusion. There are many guesses containing repeated letters which have excellent prospects, especially those with pairs of **E** or **S**. &#8220;**EASER**&#8221; is the best of these with an E(Y|G) of 1.68039, and pleasingly even &#8220;**ARSES**&#8221; weighs in with an E(Y|G) of 1.66489.

Here are the ten best combinations of ten letters to cover with the first two guesses, with an example of two valid Wordle words covering those letters:

<pre class="wp-block-preformatted">Rank   Letters      Example Words   Combined E(Y|G) 
1.     AEILNORSTU   AEROS, UNLIT    3.06429 
2.     ADEILNORTS   ADITS, ENROL    3.05365 
3.     AEILONRSTY   AEROS, LINTY    3.03307 
4.     ADEILORSTU   ADIEU, ROTLS    3.02660 
5.     ACEILNORST   ACNES, LIROT    3.02451 
6.     AEILONPRST   AIRTS, PELON    3.02182 
7.     AIMERSTOLN   AIMER, STOLN    3.02051 
8.     AEHILNORST   AEONS, THIRL    3.00817 
9.     ADEILNORSU   ADORN, ILEUS    3.00763
10.    AEILORSTUY   AIERY, LOTUS    3.00601</pre>

By comparison, my previous favoured pairing of &#8220;**ADIEU**&#8221; and &#8220;**GHOST**&#8221; has an E(Y|G) of 2.7358. Switching to a combination of words that covers the letters AEILNORSTU such as &#8220;**AEROS**&#8221; and &#8220;**UNLIT**&#8221; should boost my expected number of hints from my first two guesses by 12%!

## The Best of the Best {#the-best-of-the-best.wp-block-heading}

But which two words to pick? There are no fewer than **300 combinations** of valid Wordle words which cover those best ten letters, all having a combined E(Y|G) of 3.06429. Again, I decided to use E(G) as a tie-breaker, which leads to the following ranking of pairs of starting words:

<pre class="wp-block-preformatted">Rank   Word 1   Word 1 E(Y|G)   Word 2   Word 2 E(Y|G)   Combined E(G) 
1.     TAILS    1.61903         ROUEN    1.44527         1.16454 
2.     TARNS    1.61849         LOUIE    1.44581         1.13818 
3.     LORES    1.74029         TUINA    1.32401         1.13146 
4.     RAILE    1.66875         TOUNS    1.39554         1.39554 
5.     TAINS    1.59382         ROULE    1.47047         1.12243 
6.     RAUNS    1.57246         TOILE    1.49183         1.12239 
7.     RAILE    1.66875         TONUS    1.39554         1.11549
8.     TOLES    1.67276         NAIRU    1.39153         1.11543 
9.     TAINS    1.59382         LOURE    1.47047         1.11443
10.    RANTS    1.61849         LOUIE    1.44581         1.11417</pre>

## Adieu, &#8220;ADIEU&#8221; {#adieu-adieu.wp-block-heading}

So there you have it. Having crunched the numbers, my new pair of Wordle starter words from tomorrow morning shall be &#8220;**TAILS**&#8221; followed by &#8220;**ROUEN**&#8220;. [Follow me on Twitter][5] to see how it works out for me. I have a suspicion that despite this analysis, my mother will still reach the answer in fewer guesses than me more often than not!

 [1]: https://www.powerlanguage.co.uk/
 [2]: https://www.powerlanguage.co.uk/wordle/
 [3]: https://unsplash.com/@ryoji__iwata?utm_source=ghost&utm_medium=referral&utm_campaign=api-credit
 [4]: https://unsplash.com/?utm_source=ghost&utm_medium=referral&utm_campaign=api-credit
 [5]: https://twitter.com/ianfnelson