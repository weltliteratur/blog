---
title: 'Network Modelling "The Last Days of Mankind"'
layout: post
author: frank
comments: true
date: 2020-05-07
---

Last level. Final boss. Arguably the longest play ever written: **"The Last Days of Mankind"**, brought to light between 1915 and 1922 by your favourite Austrian crank: writer and journalist **[Karl Kraus](https://en.wikipedia.org/wiki/Karl_Kraus_(writer))** (1874–1936).

More than 600 pages in the German original, five acts, prologue and epilogue, 220 scenes altogether documenting the apocalypse of World War I. A first complete translation to English was published [at Yale University Press](https://yalebooks.yale.edu/book/9780300207675/last-days-mankind) in 2015 (done by Fred Bridgham and Edward Timms).

As Kraus notes in the preface:

> "The performance of this drama, which would take some 10 evenings in terrestrial time, is intended for a theatre on Mars. Theatre-goers on planet earth would find it unendurable."

Now what did we do? Dialogues in the play are distributed among a total of **925 speaking instances** (individual characters, voices, groups, choirs). We extracted the social network graph (based on co-occurrences of characters per scene) from [the TEI version](https://dracor.org/api/corpora/ger/play/kraus-die-letzten-tage-der-menschheit/tei) of the play. And then we took Kraus at his word and projected the network graph onto planet Mars. Resulting in our poster contribution for [DHd2020](https://dhd2020.de/) held in Paderborn in early March (one of the last conferences before coronavirus lockdown):

<figure style="text-align:center;">
  <img src="/images/theatre-on-mars-poster-small.jpg" alt="theatre on Mars, poster, small version" style="width:463px;" />
</figure>
<center><b>Fig. 1.</b> "Visit to the Mars Theatre." (DOI:<a href="https://doi.org/10.6084/m9.figshare.11917902">10.6084/m9.figshare.11917902</a>)</center>

Our visit to the Mars theatre won us [the Best Poster Award](https://dig-hum.de/dhd-awards), which we were very happy about. Feel free to download the [hi-res version](https://doi.org/10.6084/m9.figshare.11917902) from Figshare (beware, it's heavy). There's also a lenghty [Twitter thread](https://twitter.com/umblaetterer/status/1235556225128886277) about our work (in German).

Some properties of the network:

* Number of nodes: 925
* Number of edges: 12.425
* Network density: 0,029 (very low in comparison to other plays)
* Number of independent clusters: 120
* Clustering coefficient: 0,976 (extremely high, corresponds to the value of other station dramas)

If you want to toy around with the network data yourself, you can download it in CSV, GEXF and GraphML format [from **DraCor**](https://dracor.org/ger/kraus-die-letzten-tage-der-menschheit).
