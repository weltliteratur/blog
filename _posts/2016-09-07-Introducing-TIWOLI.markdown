---
title: Introducing TIWOLI ("Today in World Literature"), a Calendar App of Fictional Events
layout: post
author: [frank, jannik]
comments: true
date: 2016-09-07
---

(This could become a whole new series: **Fancy by-products of Digital Humanities research projects…**)

Why don't we jump right into it and name five famous days in world literature:

- The day of James Joyce's "Ulysses"? (Of course, [Bloomsday](https://en.wikipedia.org/wiki/Bloomsday), [Lá Bloom](https://ga.wikipedia.org/wiki/L%C3%A1_Bloom), June 16!)

That is an easy start, but the world beyond this über-day of world literature is trickier. Most people will know about the fictional events we're going to itemise, but won't typically have the exact dates in mind. Let's check:

- On which day did Robinson Crusoe set foot on his island? (September 30) On which day did he eventually return to England, after 35 years of absence? (June 11)
- When is the deadline for Phileas Fogg's travel around the world in eighty days? (December 21)
- What's Tristram Shandy's birthday? (November 5) – Funny enough, there still seem to be [people drinking to Tristram Shandy's health](http://edwardiansisterhood.blogspot.de/2009/11/hill-times.html).
- When did Goethe's "Young Werther" commit suicide? (December 21)
- On what day did Charlie visit the Chocolate Factory? (February 1) – Especially interesting to note here that [in the 1971 movie](https://en.wikipedia.org/wiki/Willy_Wonka_%26_the_Chocolate_Factory), the golden ticket refers to "the first day of October" for whatever reason.

So this is the subject of our blogpost, **(in)famous days in world-literary fiction**.

How did this come about? At the DH2015 conference in Sydney, we delivered a talk called "When does (German) literature take place?" ([slides](http://dbs.ifi.uni-heidelberg.de/fileadmin/Team/jannik/publications/dh2015-sydney-fischer-stroetgen-german-literature-slides.pdf)) In order to answer that unusual question, we extracted exact dates and months from a corpus of 2,700+ works of German-language fiction from 1510 to the 1940s. Our results suggested that ["the marvellous month of May"](https://de.wikisource.org/wiki/Im_wundersch%C3%B6nen_Monat_Mai) (Heinrich Heine) is preeminent in our corpus of German fiction. There is enough evidence to claim that May (at least in the northern hemisphere) is the favourite month of poets, and Heine is just one example. But May's preeminence in prose was a real finding and there are a bunch of explanations, but this (along with many other insights yielded by this whole date-extraction-from-fiction business) shall happen in the corresponding research paper, not here.

As a by-product (and no more than that), we coded a native Android app to showcase the more exciting and self-explanatory of our results. We called our app **TIWOLI** (short for "Today in World Literature") and made it **[available via the Google Play Store](https://play.google.com/store/apps/details?id=de.wannauchimmer.apps.tiwoli)**. (There's also a version for iOS, done by our dear friend [Thomas Bögel](http://thboegel.de/), but updates will kick in a bit slower on that platform.)

Now what TIWOLI does is give you the opportunity to zigzag through an entire world-literary year, a calendar filled with fictional happenings. Here some screenshots with some of the examples from above:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-06-16-joyce-ulysses.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/4300">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-02-01-dahl-charlie.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://books.google.com/books?id=v7WeJp2CU-QC&pg=PT55">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-11-05-sterne-tristram.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/1079">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-12-20-verne-eighty.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/103">source</a>)</figcaption></figure></li>
 </ul>
</div>
<div style="clear:left;" />

We're currently curating three corpora for the app, in **English**, **Spanish** and **German**. In some cases, you can even switch between translations of one and the same passage (not in all cases, though, the contents of our corpora are very different per language). This is a 1st of January example from Balzac's novel "Eugénie Grandet":

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-01-01-balzac-eugenie.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/1715">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-01-01-balzac-eugenia.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://es.wikisource.org/wiki/Eugenia_Grandet">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-01-01-balzac-eugenie.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="http://gutenberg.spiegel.de/buch/4850/3">source</a>)</figcaption></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The interface was also translated into the three languages (it will fall back to English if your system language cannot be matched). Here are the three versions of our welcome screen, plus the English version of the settings page:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-welcome.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-bienvenido.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-willkommen.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-settings.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

If you like you can set the alarm so it informs you about fictional events that "happened" on the current day.

It was not all that easy to fill up a whole year with suitable quotes for every day. To replenish the English corpus with nice enough quotes we are very grateful to Mark Algee-Hewitt and the Stanford Literary Lab who helped us out with their corpus of English-language fiction. Let's give you some more:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-01-15-bronte-jane-eyre.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/1260">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-02-01-twain-wilson.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/102">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-02-22-fitzgerald-beautiful.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/9830">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-03-04-doyle-scarlet.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/244">source</a>)</figcaption></figure></li>
 </ul>
</div>
<div style="clear:left;" />

For each corpus, the app contains quotes from translated world-literary works, too, because after all, weltliteratur is the raison d'être of this blog:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-03-16-novalis-ofterdingen.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/31873">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-03-25-hugo-hunchback.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/2610">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-04-07-gogol-nose.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/36238">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-05-20-turgenev-fathers.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://www.gutenberg.org/ebooks/30723">source</a>)</figcaption></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The dates from the Russian 19th-century novels point to the Julian calendar, of course (which was 12 days behind the Gregorian back then). Some more translated literature:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-06-12-hamsun-mysteries.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://books.google.com/books?id=xB6nAgAAQBAJ&pg=PT4">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-07-05-voltaire-micromegas.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="http://en.wikisource.org/wiki/Micromegas/Chapter_3">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-07-27-zweig-chess.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="https://books.google.com/books?id=Uv4UAgAAQBAJ&pg=PT31">source</a>)</figcaption></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-09-23-hoffmann-pot.png" alt="Screenshot from TIWOLI app."><figcaption>(<a href="http://gutenberg.net.au/ebooks06/0605801h.html">source</a>)</figcaption></figure></li>
 </ul>
</div>
<div style="clear:left;" />

For every quote we provide a link to the full-text source (gutenberg.org, gutenberg.net.au, archive.org, books.google.com, …). Epitexts and links/metadata are generated automatically. The portraits/pictures were not chosen by us, we're relying on the 'principal image' provided by Wikidata, a great way to easily enrich an app. Let's give you the Defoe examples from above, accompanied by Poe (for the sake of rhyming names):

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-06-22-poe-roget.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-07-10-poe-maelstrom.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-09-30-defoe-robinson.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-12-19-defoe-robinson.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

Some more German literature in translation, including the aforementioned destiny of storm-and-stressy Werther:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-09-27-fontane-effi.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-10-03-fontane-effi.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-10-30-hoffmann-sandman.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-12-21-goethe-werther.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The first two quotes are from Fontane's "Effi Briest", in many respects the righteous German counterpart to "Madame Bovary". The second quote alludes to Effi's and Instetten's wedding which coincides with the national day of Germany (not a good omen, given the tragic outcome of the novel 😇).

Four final examples from the English corpus:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-07-31-shelley-frankenstein.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-11-02-eliot-bede.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-11-09-wilde-dorian.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-12-10-stevenson-hyde.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The last quote, from "Jekyll &amp; Hyde", is interesting insofar as it can be regarded a mistake by the author that went into several print editions ([see here](https://books.google.com/books?id=sk7zCQAAQBAJ&pg=PA64), for example).

We also harvested some newer books as you can see in the Auster example below (the picture is not the best, but somebody might upload a better one to Wikimedia Commons someday). There's also one more Brontë quote and two nice quotes from the time-travel novel by Bellamy (where times and dates are the actual subject):

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-03-20-bronte-heights.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-05-19-auster-glass.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-05-30-bellamy-2000.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-en-09-10-bellamy-2000.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

Now let's sneak a peek at the Spanish corpus. You can easily switch to the other corpora at any point from within the app.

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-04-22-valera-pepita.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-06-15-caballero-gaviota.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-07-12-baroja-silvestre.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-07-20-cervantes-quijote.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

We can also follow the chronology of Borges' cuento "La muerte y la brújula" ("Death and the Compass"):

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-12-03-borges-brujula.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-01-03-borges-brujula.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-02-03-borges-brujula.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-03-01-borges-brujula.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

Some concluding Spanish examples:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-02-28-dumas-montecristo.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-12-21-goethe-werther.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-10-11-marquez-soledad.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-es-12-31-aira-fantasmas.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

On to the German corpus:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-01-20-buechner-lenz.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-04-04-schnitzler-gustl.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-04-12-lasswitz-planeten.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-07-27-zweig-schachnovelle.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The first one, from Georg Büchner's novella fragment "Lenz", is probably one of the most famous first sentences. In the second one, Schnitzler's "Leutnant Gustl" is pondering his destiny on 4th of April, resulting in **not** killing himself. In the third one, the government of the Martian States takes control over our planet, because we earthlings are not capable of maintaining peace (the author of the passage, Kurd Lasswitz, can be regarded a pioneer of German sci-fi lit). The fourth quote is especially interesting, since the "27th of July" is also discussed in a "meta" way, as a combination of a printed number and a word, which serves as intellectual nourishment for the imprisoned intellectual.

We already featured Fontane with some passages translated to English. But what is it with the Prussian author and the 3rd of October? It is an eventful day in many of his novels, and we're not sure if anyone has looked into that yet:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-10-03-fontane-birnbaum.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-10-03-fontane-effi.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-10-03-fontane-stechlin.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

Fitfully, we included some quotations from contemporary fiction. The given sources contain page numbers as they point to print editions of the works:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-07-19-zeh-unterleuten.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-07-23-goetz-holtrop.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-08-15-werner-abgang.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-12-12-enzensberger-robert.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

Some more:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-10-07-schmidt-atheisten.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-10-12-stein-rabbi.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-11-09-richter-gran-via.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

The first quote from Arno Schmidt's 1972 novel ["The School for Atheists"](https://en.wikipedia.org/wiki/The_School_for_Atheists) points to a future date, the 7th of October, 2014. When we traversed this point in time two years ago, at least one major newspaper published an article about this long-imminent event (German weekly "Die Zeit": ["The story starts now."](http://www.zeit.de/2014/43/arno-schmidt-tellingstedt-die-schule-der-atheisten)).

How about Jean Paul, the greatest of all May lovers:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-05-01-jean-paul-hesperus.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-05-03-jean-paul-quintus.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-05-16-jean-paul-quintus.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>
<div style="clear:left;" />

And last not least, some Christmas quotes:

<div id="tiwoligallery">
 <ul>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-12-24-droste-huelshoff-judenbuche.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-12-24-hesse-unterm-rad.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-12-24-hoffmann-nussknacker-und-mausekoenig.png" alt="Screenshot from TIWOLI app."></figure></li>
  <li><figure><img src="{{ site.url }}/images/tiwoli/tiwoli-de-12-24-mann-buddenbrooks.png" alt="Screenshot from TIWOLI app."></figure></li>
 </ul>
</div>

(Admittedly, this turned out to be a BuzzFeed-like über-post, far too long with far too many pics.)

So much for our app, TIWOLI. Also if it wasn't part of our original research, it helped to sharpen our notion of dates and month names in fictional texts. Literature as a genre has an inclination to waive exact dates and prefers temporal settings like "at the beginning of November", ["It was a dark and stormy night"](https://en.wikipedia.org/wiki/It_was_a_dark_and_stormy_night), etc. But sometimes exact dates do occur, of course. And if they do, they have a tendency to mean something. (Mind you, epistolary and historic novels are usually full of exact dates. We tried to exclude them from the app and just used some as fill-ins, Goethe's "Werther", all Jules Verne novels and Benito Pérez Galdós proved especially useful. 😊)

We also have two cliffhangers for you:

1. The Cologne Center for eHumanities ([CCeH](http://www.cceh.uni-koeln.de/)) is currently building a web interface with our data. Prototypes look very promising.

2. There's an easter egg somewhere in the app. Whoever finds it first is our hero/ine!
