---
title: 'Ted Underwood''s "Distant Horizons": Reviews and Replications'
layout: post
author: frank
comments: true
date: 2021-05-18
---

Ted Underwood's most recent book – 206 pages, published in February 2019 – was widely acclaimed and much discussed. Based on the assumption that digital methods and corpora show their strengths especially in diachronic observations over long periods of time, he has provided aspects of a digital literary historiography.

But this "computational monograph" – to quote Maciej Maryl – is not just something to read. Data and code have been published and can be replicated and questioned. This is not always easy and is not yet a living part of our practice in the Digital Humanities.

That's why this blogpost attempts to bring together the [**REPLICATIONS**](#replications-of-code-andor-data) made so far to put Underwood's technical setup to the test. Such efforts to verify scientific claims should be encouraged more and can be exemplary for similar undertakings in the future.

I'm also gathering all [**REVIEWS**](#reviews) of the book I found (as neither the publisher's website nor the author's personal page offers such an overview). If you have any additions, please lemmino (you can find me [on Twitter](https://twitter.com/umblaetterer)).

<figure style="text-align:center;">
  <img src="/images/underwood-distant-horizons-cover.jpg" alt="Underwood, Distant Horizons, cover" style="width:300px; border: 1px solid transparent; border-color: black;}" />
</figure>
<center><p style="font-size: 16px; line-height: 24px;"><b>Fig. 1.</b> Ted Underwood: <b>Distant Horizons. Digital Evidence and Literary Change.</b> Chicago and <br />London: The University of Chicago Press 2019. (<a href="https://doi.org/10.7208/chicago/9780226612973.001.0001">doi:10.7208/chicago/9780226612973.001.0001</a>).</p></center>

Underwood's book has a somewhat mediating character. The machine-learning methods used for the analyses are not bleeding edge, he mostly relies on regularised logistic regression on several thousand features. Underwood refutes the claim that machine learning models are always inscrutable black boxes. He spends a lot of time looking into these black boxes and interpreting the word frequencies and their distribution in order to craft narratives relevant to literary studies.

But we are still at the beginning, as Underwood makes clear: "Statistical models can help us understand the social forces shaping a long arc of literary change. But turning those models into fully satisfying stories **could take several more decades.**" (p. 109)

I originally wanted to write a review myself, but never found the time to finish it (and finally got discouraged late last year when I encountered Maciej Maryl's excellent and comprehensive review 😊). The following list of reviews I have compiled may serve to better sort through the rich discussions surrounding "Distant Horizons" and find good entry points.

## REVIEWS

* **Dan Sinykin**, [*Post45* (6 May 2019)](https://post45.org/2019/05/distant-reading-and-literary-knowledge/)
  * **Tess McNulty** [responds to his review, *Post45* (6 May 2019)](https://post45.org/2019/05/seeing-double-a-response-to-dan-sinykin/)
* **Mareike Schumacher**, [*lebelieberliterarisch.de* (25 Jul 2019)](https://lebelieberliterarisch.de/ted-underwoods-distant-horizons/) 🇩🇪 – followed by [a comment from Fotis Jannidis](https://lebelieberliterarisch.de/ted-underwoods-distant-horizons/#comment-580)
* **Laura Jiménez Ríos**, [*Revista de Humanidades Digitales*, Vol. 4 (2019), pp. 212–215](https://doi.org/10.5944/rhd.vol.4.2019.24217) 🇪🇸
* **Daniel Rosenberg**, [*Modern Philology*, Vol. 117, No. 3 (Feb 2020),  publ. online 22 Nov 2019](https://doi.org/10.1086/707111)
* **Katherine Bode**, [*Modern Language Quarterly*, Vol. 81, Issue 1 (1 Mar 2020), pp. 95–124](https://doi.org/10.1215/00267929-7933102
) ([preprint](https://katherinebode.files.wordpress.com/2019/10/mlq2019_preprint.pdf)) – a more critical take
* **Alison Booth**, [*Victorian Studies*, Vol. 62, No. 3 (Spring 2020), pp. 547–550](https://muse.jhu.edu/article/771272/summary) – also somewhat critical
* **Maciej Maryl**, [*JLTonline* (17 Oct 2020)](http://www.jltonline.de/index.php/reviews/article/view/1090/2504) – assigns a new genre to the book, calling it a "computational monograph"

## REPLICATIONS OF CODE AND/OR DATA

When Underwood submitted his book to the publisher, he published data and code in a ZIP package on Zenodo on 25 March 2018 ([doi:10.5281/zenodo.1207277](https://doi.org/10.5281/zenodo.1207277)). There's also a (slightly updated) [Git Hub repo](https://github.com/tedunderwood/horizon).

Portions of chapters 2, 3 and 4 are reprints of prior collaboratory work. This is also the reason why most of the listed replications could take place before the book even went to press.

* **Andrew Goldstone**, ["Of Literary Standards and Logistic Regression: A Reproduction", *andrewgoldstone.com*, 4 Jan 2016](https://www.andrewgoldstone.com/blog/2016/01/04/standards/)
  * **Sarah Allison** wrote a short piece reflecting on Goldstone's replication: ["Other people’s data: humanities edition", *Journal of Cultural Analytics*, Vol. 1, Issue 1 (18 Dec 2016)](https://doi.org/10.22148/001c.11822)
* **Jonathan Goodwin**, ["Darko Suvin’s Genres of Victorian SF Revisited", *jgoodwin.net*, 17 Oct 2016](www.jgoodwin.net/blog/more-suvin/)
* **Nan Z. Da**, ["The Computational Case against Computational Literary Studies", Vol. 45, No. 3 (Spring 2019)](https://doi.org/10.1086/702594) – among a total of 14 CLS papers, she also discusses Underwood's "The Life Cycle of Genres", which expanded into chapter 2 of "Distant Horizons"
  * followed by **Underwood**'s reaction in CI's response forum, [*critinq.wordpress.com*, 1 Apr 2019](https://critinq.wordpress.com/2019/04/01/computational-literary-studies-participant-forum-responses-8/)
  * and **Da**'s follow-up, ["Errors", *critinq.wordpress.com*, 2 Apr 2019](https://critinq.wordpress.com/2019/04/02/computational-literary-studies-participant-forum-responses-day-2/)
* **Ted Underwood**'s reply to Da, ["The Theoretical Divide Driving Debates about Computation", *Critical Inquiry*, Vol. 46, No. 4 (Summer 2020)](https://doi.org/10.1086/709229), which re-analyses material in chapter 2 using different methods
