---
title: 'Vossian Antonomasia in "The New York Times" (New Paper Out!)'
layout: post
author: [frank]
comments: true
date: 2019-02-19
---

We've been collecting and studying **Vossian antonomasia** (VA, or, vossanto) for about a decade now. This stylistic device, named after Dutch humanist [Gerardus Vossius](https://en.wikipedia.org/wiki/Gerardus_Vossius), occurs when someone is called ["the Jay Leno of Tel Aviv"](https://www.nytimes.com/2006/12/31/movies/31farb.html) or ["the Marilyn Monroe of the Arab world"](https://www.nytimes.com/1999/09/22/arts/tahia-carioca-79-dies-a-renowned-belly-dancer.html) etc. etc.

We just published a new paper about this phenomenon …

* Frank Fischer; Robert Jäschke: **‘The Michael Jordan of greatness’—Extracting Vossian antonomasia from two decades of The New York Times, 1987–2007.** *Digital Scholarship in the Humanities.* 2019. (DOI:10.1093/llc/fqy087) (Preprint tba)

… plus a website with our code and some more interesting results for you to explore:

* https://vossanto.weltliteratur.net/

But let's rewind a bit. Some years ago we published a [hand-picked list](https://www.umblaetterer.de/datenzentrum/vossianische-antonomasien.html) with our favourite VA expressions from 2009 to 2014 (mainly from German-language media) and published what we thought would be our [final article on the subject](https://www.umblaetterer.de/wp-content/uploads/2014/12/vossanto_fas.png) in *Frankfurter Allgemeine Sonntagszeitung* in December 2014.

There is a lot of research out there on all types of antonomasia, even on Vossian antonomasia (or 'metaphorical antonomasia', or 'paragons'). But when we started looking, we didn't come across any convincing automatic approach regarding the bulk extraction of VA. All papers we found had hand-picked examples and took it from there. Of course, there are the type of websites like ["The Michael Jordan of..."](https://graphics.wsj.com/michael-jordan-of/), which collected 1,505 *Michael Jordans of something*. As interesting as that is, from an extraction point of view it is trivial.

## Vossian Antonomasia, Next Level

So before long we were back in the game and started hacking. We wanted to find a way to extract all occurrences of Vossian antonomasia from larger newspaper corpora (that is, as many as possible), not only based on usual suspects like Michael Jordan (for what it's worth, our research has confirmed on much more reliable grounds that he's the ruler of the Vossian world). So anyway, we wanted to find unexpected examples, and our first idea was to fetch some newspaper corpora, do some POS tagging and NER and then try to match the pattern "the [name] of". We worked with two full-text corpora, the *New York Times* 1987–2007 and German weekly *Die Zeit* 1995–2011. We [presented](https://lehkost.github.io/slides/2017-bern/) this work at DHd2017 in Bern, but were not really content with the results. Especially NER let us down big time. But it was a start.

A couple of months later we had the idea that took our research to a new level. Thanks to a research scholarship granted to me by the [Information School at the University of Sheffield](https://www.sheffield.ac.uk/is), Robert and I were able to spend two weeks hacking together in May, 2017. And then, probably during one of our lunches at the [Red Deer](http://www.red-deer-sheffield.co.uk/) (Vegetarian Haggis ftw!), we came to talk about **Wikidata** and then it occurred to us that it could help us out of our NER concerns. Here are the two things we brought together:

1. We want to extract paragons, that is, well-known, infamous people. People that would definitely have a Wikipedia entry in some language, or else they wouldn't be well-known enough to serve as source for Vossian antonomasia.

2. Wikidata inherits these famous people from all the different Wikipedia language versions and has all kinds of facts about them in a well-structured format, including nicknames and alternative spelling of names (which we would need).

Please note that this solution was really carved out for our specific research question, because Wikidata arguably holds exactly those named entities that we would need. Yet it probably wouldn't be the best choice for other NER purposes.

The rest was pretty simple. It was now enough to use a regular expression to extract the general pattern "the … of", and then we would match the part in-between against our persons database. And that's what we did. The corpus at hand was the [*New York Times* one](https://catalog.ldc.upenn.edu/LDC2008T19), and whenever we initiated another extraction process (which always took some minutes), we would pay a visit to the Red Deer to have just another ginger beer.

## Results

Vossian antonomasia is a rare phenomenon. Annotating a gold set of 500 randomly selected articles might not throw you even one result. So, hile we cannot provide numbers for recall due to the lack of a gold standard, we can provide our precision scores, because we could personally check extraction results. Altogether we managed to extract **2,646 VA expressions** from 20 years of the *New York Times* (1987–2007).

The paper features our most notable results, but we also provide some more things to explore on the project website:

* [Some More Statistics](https://vossanto.weltliteratur.net/theof/humans/statistics.html)
* [Complete List of Extracted VA](https://vossanto.weltliteratur.net/theof/humans/vossantos.html)

Michael Jordan is the boss of it all, as is shown in the [table with the top-40 source entities](https://vossanto.weltliteratur.net/theof/humans/statistics.html#top-40-va-sources) for Vossian antonomasia we extracted. But Jordan is closely followed by [Rodney Dangerfield](https://en.wikipedia.org/wiki/Rodney_Dangerfield), a US-American comedian infamous for the sentence "I don't get no respect". I think that being the runner-up in Vossian Olympics actually might earn him some respect after all.

We also generated a gallery of those 40 people by pulling their principal images from Wikidata ([Property:P18](https://www.wikidata.org/wiki/Property:P18)):

<figure>
  <img src="/images/gallery-top-39-sources-vossian-antonomasia.jpg" alt="Top-39 sources for Vossian antonomiasa in the NYT 1987–2007" style="width:1200px;" />
</figure>
<center>*Btw, if you did the counting you'll only find 39 images. One of the entities does not have an image in Wikidata.)*</center>

## Next Steps

Our research continues. We're generally fine-graining our method because there are things we missed. And although "the … of" is arguably the most frequent pattern, we didn't check other patterns yet, like "a … of", or the type where the VA source is preceded by a national adjective, as in "the Vietnamese Mozart" or "the German Donald Rumsfeld". We're on it. And we're open for collaborations with other scholars. Because one other thing we wanna do in the future is to broaden our research to corpora in other languages than English with richer morphology, which will add a layer of complexity.

Oh, if you find interesting Vossian antonomasia, please ping me on Twitter ([@umblaetterer](https://twitter.com/umblaetterer)) if you like.
