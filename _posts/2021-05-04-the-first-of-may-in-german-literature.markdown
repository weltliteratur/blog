---
title: The First of May in German Literature
layout: post
author: frank
comments: true
date: 2021-05-04
---

<center>[ <b>tl;dr:</b> This blogpost introduces a small dataset comprising 249 mentions
<br />of the "1st of May" extracted from a corpus of German-language fiction. ]</center>

Last Friday, German radio station Bayern 2 asked me for an interview about our research on **the role of the month of May in literature** (and about the practice of Digital Humanities in general, for that matter). The announcement is **[here](https://web.archive.org/web/20210618231138/https://www.br.de/radio/bayern2/programmkalender/ausstrahlung-2460628.html)** – unfortunately, they didn't put the interview online, but if anyone wants to listen to it, I can send them an mp3 copy.

I took this opportunity to revisit my earlier research on date extractions from literature, which I started with Jannik Strötgen right after we met at his poster at the 2013 Herrenhausen Conference ["(Digital) Humanities Revisited"](https://web.archive.org/web/20221201065112/https://www.volkswagenstiftung.de/en/events/event-reports/documentation-herrenhausen-conference-digital-humanities-revisited). Although our work was mostly finished by 2015, we occasionally returned to this topic due to public interest, and it was always great to come back to it since we could never exhaust all the possibilities our research data offered us because we quickly got busy with other things.

The journalists at Bayern 2 probably learned about our research through an [article I wrote for Die Literarische Welt](https://archive.org/download/als-einst-am-ersten-mai-2019-05-04/als-einst-am-ersten-mai-2019-05-04.pdf) two years ago:

<figure style="text-align:center;">
  <img src="/images/first-of-may/als-einst-am-ersten-mai-2019-05-04.png" alt="newspaper article" style="width:350px; border: 3px solid transparent; border-color: coral;" />
</figure>
<center><b>Fig. 1.</b> “Als einst am 1. Mai die Welt begann” (publ. <a href="https://archive.org/download/als-einst-am-ersten-mai-2019-05-04/als-einst-am-ersten-mai-2019-05-04.pdf">4 May 2019</a>).</center>

This article draws on the main results of our study originally presented at the [DHd2015 (in Graz)](https://doi.org/10.5281/zenodo.4623384) and [DH2015 (in Sydney)](https://dbs.ifi.uni-heidelberg.de/files/Team/jannik/publications/fischer-stroetgen_temporal-expressions-in-literary-corpora_dh2015_final_2015-03-01.pdf) conferences.

An interesting by-product of our work was the "TIWOLI" app ("Today in World Literature") with iOS and Android versions ([which we introduced in this blog in 2016](/Introducing-TIWOLI/)). And, of course, there's [the TIWOLI Twitter bot](https://twitter.com/tiwolichirp), run by our colleagues at University of Cologne.

In 2017, we finally managed to release the corpus on which our research is based, the **"Corpus of German-Language Fiction (txt)"** ([doi:10.6084/m9.figshare.4524680](https://doi.org/10.6084/m9.figshare.4524680)). The corpus contains 2,735 German-language prose works (mainly novels and short stories) by 549 authors, ranging from about 1510 to the 1940s (the bulk of the texts dates from 1840–1930). [On a sidenote, our corpus was also used by Severin Simmler [to fine-tune a German BERT model to adapt it to the literary domain](https://huggingface.co/severinsimmler/literary-german-bert).]

To extract the mentioned month names and concrete days, we used Jannik's cutting-edge [HeidelTime](https://github.com/HeidelTime/heideltime) engine. As you can see in the flower-ringed histogram featured on the newspaper page, the month of May is by far the most frequently mentioned month in the corpus. In addition, the 1st of May is, also by far, the most frequently mentioned day of the year, with 249 mentions in the corpus.

Here is an overview with the frequency of all days as we extracted them from the corpus ('1' means 0–9 occurrences, '2' means 10–19 occurrences, etc., '+' means 90 or more occurrences):

<figure style="text-align:center;">
  <img src="/images/first-of-may/heatmap-all-days.png" alt="heatmap" style="width:550px; border: none;" />
</figure>
<center><b>Fig. 2.</b> Green fields: days mentioned 50+ times in the corpus <br />(slide taken from <a href="https://dbs.ifi.uni-heidelberg.de/files/Team/jannik/dhd2015-fischer-stroetgen-deutsche-literatur-slides.pdf#page=21">our DHd2015 slideset</a>).</center>

HeidelTime can extract various forms of dates, so here it has managed to extract "1. Mai", "1. May" as well as "erste" / "ersten Mai". Some example sentences:

* "Ich telephonierte Montag nachmittag (also am <u>1. Mai</u>) dem Witschi nach Gerzenstein, er möge mich in meinem Bureau aufsuchen." (Glauser: [Wachtmeister Studer](https://www.projekt-gutenberg.org/glauser/studer/chap15.html))
* “[…]; den <u>1. May</u> 1772 reiseten wir aus Gondar ab." (Knigge: [Benjamin Noldmanns Geschichte der Aufklärung in Abyssinien](https://www.projekt-gutenberg.org/knigge/noldmann/noldm120.html))
* "Du sollst doch auch wissen, daß heute der <u>erste Mai</u> ist, du Einsiedler!" (Dahn: [Ernst und Frank](https://www.projekt-gutenberg.org/dahn/herzen/chap003.html))
* "Am <u>ersten Mai</u> anno domini 1835 war zu Haimbach ein großes Frühstück." (Stifter: [Feldblumen](https://www.projekt-gutenberg.org/stifter/feldblum/feldb032.html))

Now we've always wanted to dig a little deeper into our dataset to go beyond mere quantification, and we've demonstrated this idea by qualifying all mentions of the 10th of August:

<figure style="text-align:center;">
  <img src="/images/first-of-may/pie-chart-10th-of-august.png" alt="pie chart" style="width:460px; border: none;" />
</figure>
<center><b>Fig. 3.</b> Semantics of the 10th of August in our corpus <br />(slide with German labelling taken from <a href="https://dbs.ifi.uni-heidelberg.de/files/Team/jannik/dhd2015-fischer-stroetgen-deutsche-literatur-slides.pdf#page=22">our DHd2015 slideset</a>).</center>

About three quarters of the mentions were plot-related (i.e., something happened on a 10th of August, including date references in epistolary novels and fictitious diary entries). But more than 20% were non-plot-related date mentions, instead a reference to the 10th of August 1792, a decisive event of the French Revolution, when armed revolutionaries stormed the Tuileries Palace in Paris. This date is a constant reference point in our corpus of German fiction and makes for a high number of non-plot-related date mentions.

For our focal date, the 1st of May, this problem is even more complex. Many feasts and customs are associated with this date, such as Walpurgis Night and the Maypole Dance, and since 1889 also International Workers' Day. All these meanings can overlap when a 1st of May is mentioned and it is very difficult to decide whether a mention of the day refers to a plot-related event or not.

To start somewhere, however, let us first measure the precision of the 249 mentions counted and say something about the reliability of the data we generated and evaluated at the time. There are only 2 false positives, the rest is a problem of corpus composition. It is meant to be a corpus with works of fiction (hence the name), but some non-fiction works have slipped in (as already detailed [in the corpus description on Figshare](https://doi.org/10.6084/m9.figshare.4524680)). Some mentions are duplicates, and one work (by Strindberg) made it into the corpus of German originals, although it is a translation). Here's an overview:

<figure style="text-align:center;">
  <img src="/images/first-of-may/pie-chart-1st-of-may.png" alt="theatre on Mars, poster, small version" style="width:450px; border: none;" />
</figure>
<center><b>Fig. 4.</b> Precision of ‘1st of May’ mentions extracted from our corpus: <br />correctly extracted from fiction: 226 – from non-fiction: 11 – <br />duplicates: 8 – false positive: 2 – from translations: 1.</center>

Although we cannot say anything about recall in our exploratory study, the precision of HeidelTime is really good. We knew that before, of course, but never really detailed this. So this blogpost confirms the special role that May plays in German prose literature, even if the means we used at the time are far from being able to provide an exhaustive answer to the questions of "when literature takes place". But it was a start.

You can explore our findings yourself in an enhanced subset of our data, which we never formally published before. So here is a list of 1st of Mays mentioned in German fiction (in the 'timex value' column, HeidelTime automatically tried to assign years from the surrounding context of a mentioned date, which was not always successful, but we left this column in, even though we never used this data). The file format is CSV:

<center>🌿 <a href="/data/sentences-containing-first-of-may.csv"><b>sentences-containing-first-of-may.csv</b></a> 🌱</center>
