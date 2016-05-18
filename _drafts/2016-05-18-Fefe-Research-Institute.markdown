---
title: Fefe Research Institute
layout: post
author: [robert, frank]
comments: true
date: 2016-05-18
---

Ok, the headline is a joke, of course. But let's start at the beginning. There are three things German computer scientists/IT guys must not miss: their [heise online](http://www.heise.de/) newsticker, their xkcd, and their daily Fefe.

Fefe is the nom de guerre of [Felix von Leitner](https://en.wikipedia.org/wiki/Felix_von_Leitner), a C programmer (check [dietlibc](https://en.wikipedia.org/wiki/Dietlibc)), IT security adept and blogger, running his own speaker's corner **["Fefes Blog"](https://blog.fefe.de/)** since 2005. This blog is notorious for its "cut the crap" non-layout and his author for his brash comments on incidents in the broad field of IT security and their political implications, especially regarding the industry of mass surveillance. His reach is enormous and will surely beat that of many established newspapers (according to [this 2011 post](https://blog.fefe.de/?ts=b3d1b6bf), anyway; newer numbers would be helpful, though).

We don't know if pressing F5 at least three times a day in the browser tab reserved for "Fefes Blog" makes us part of the fan base. Either way, we couldn't abstain from sneaking a peek behind the curtain and wanted to analyse some traits of Fefe's characteristic style and tone. They are, in fact, so characteristic that he was even [mimicked by the ultimate German satire magazine "Titanic"](http://www.titanic-magazin.de/news/was-passiert-eigentlich-gerade-auf-fefes-blog-6220/), which sure counts for something.

Before we get to it: There have been other attempts to analyse Fefe's language, just take the inspiring 2012 blog post ["Darüber lacht Fefe"](http://www.security-informatics.de/blog/?p=956) by Joachim Scharloth. What we're going to do is, in fact, something very basic, we're basically looking for word (and URL) frequencies and n-grams. For that purpose, we wrote a little Python script which does the following three things:

* download the whole blog (easy on bandwidth, because, one: "Fefes Blog" really features the lightest HTML code imaginable, and two: `time.sleep(random.randint(1, 10))` while scraping)
* parse HTML files: extract date, post identifier and the actual post and put them into a single 3-column TSV file (this is really some of the cleanest data you can work with, what a feast!)
* start analysis

After step two, the TSV file contained all blog entries from the beginning (March, 2005) to Mid-May, 2016, which is the cut-off time for our dataset.

## Main Sources

These are the most frequent top-level domains linked to in "Fefes Blog":

| Rank | TLD                | Frequency |
|------|--------------------|-----------|
| 1    | spiegel.de         | 4042      |
| 2    | fefe.de            | 3316      |
| 3    | heise.de           | 2673      |
| 4    | wikipedia.org      | 1319      |
| 5    | bbc.co.uk          | 1102      |
| 6    | tagesschau.de      | 1096      |
| 7    | guardian.co.uk     | 1043      |
| 8    | youtube.com        | 1010      |
| 9    | nytimes.com        | 692       |
| 10   | twitter.com        | 624       |
| 11   | tagesspiegel.de    | 531       |
| 12   | yahoo.com          | 489       |
| 13   | rian.ru            | 485       |
| 14   | zeit.de            | 475       |
| 15   | faz.net            | 468       |
| 16   | reuters.com        | 443       |
| 17   | taz.de             | 408       |
| 18   | sueddeutsche.de    | 400       |
| 19   | cnn.com            | 376       |
| 20   | washingtonpost.com | 364       |

So this list shows Fefe's main sources. Now, it's part of his irony to urge his readers – in the subheader of the blog – to send him "fancy conspiracy links". This, at least for some, leaves room for irritation and Fefe kind of clarifies this in the [FAQ](https://blog.fefe.de/faq.html): "Why do you write 'conspiracy links' if your content is all normal news?" Reply: "Yes."

## Countries Mentioned

This list is a bit half-baked, since we're only counting exact hits and only added synonyms for two countries (GB, USA). Wales, Scotland and England where, too, mapped to Great Britain. All a bit hasty, but anyway:

| Rank | Country        | Frequency | 
|------|----------------|-----------| 
| 1    | USA            | 1918      | 
| 2    | Deutschland    | 1506      | 
| 3    | Israel         | 997       | 
| 4    | Iran           | 927       | 
| 5    | Großbritannien | 708       | 
| 6    | China          | 657       | 
| 7    | Irak           | 474       | 
| 8    | Afghanistan    | 354       | 
| 9    | Griechenland   | 298       | 
| 10   | Ukraine        | 294       | 
| 11   | Frankreich     | 287       | 
| 12   | Türkei         | 279       | 
| 13   | Japan          | 253       | 
| 14   | Syrien         | 231       | 
| 15   | Schweiz        | 222       | 
| 16   | Österreich     | 209       | 
| 17   | Polen          | 177       | 
| 18   | Pakistan       | 172       | 
| 19   | Italien        | 167       | 
| 20   | Schweden       | 158       | 

We matched our dataset against the list of countries provided [by datendieter.de](http://www.datendieter.de/item/Verzeichnis_aller_Staaten_der_Welt). (Btw, it's very probably that Daten-Dieter is a close friend of [MS-DOS-Manfred, BIOS-Bernhard, Hardware-Hanspeter and Lötkolben-Ludwig](https://www.youtube.com/watch?v=2Nlm2XSBJmQ), but that's a whole different story.)

## Countries Mentioned Over Time

We can also add time as a component, so here's a line chart showing Fefe's interest in the 12 most-mentioned countries over time:

<figure>
  <img src="https://raw.githubusercontent.com/weltliteratur/blog/gh-pages/images/fefe_time_countries.png" alt="Mentioning of countries over time in Fefes Blog." />
</figure>

This chart we can actually try to read out loud a bit: The Snowden year, 2013, marks the beginning of an increasing coverage of the USA and Great Britain. In 2014, Russia and Ukraine are peaking, for obvious reasons. One more interesting thing is the slow but steady decline of interest in Israel and Iran since 2005. Greece is starting to be covered in late 2009 with the beginning of the Greek government-debt crisis. So as can be expected from the list of his main sources seen above, Fefe's blog more or less mirrors mainstream media coverage.

## Acronyms

Well, acronyms, or words written in capitel letters:

| Rank | Acronym/Word | Frequency | 
|------|--------------|-----------| 
| 1    | USA          | 2332      | 
| 2    | CDU          | 1213      | 
| 3    | US           | 927       | 
| 4    | EU           | 926       | 
| 5    | NSA          | 800       | 
| 6    | SPD          | 723       | 
| 7    | WTF          | 556       | 
| 8    | BND          | 541       | 
| 9    | FDP          | 486       | 
| 10   | BKA          | 484       | 
| 11   | CIA          | 467       | 
| 12   | CCC          | 393       | 
| 13   | DAS          | 366       | 
| 14   | OK           | 341       | 
| 15   | FBI          | 313       | 
| 16   | DIE          | 277       | 
| 17   | BESTEN       | 253       | 
| 18   | IV           | 250       | 
| 19   | CSU          | 232       | 
| 20   | NIE          | 217       | 

## 3-Grams

Let's now look at some n-grams (we used [AntConc](http://www.laurenceanthony.net/software/antconc/) for this). Attention, the lists were curated by us and only show the frequencies for self-contained phrases, which in our opinion are contributing to the typical Fefe sound.

| Rank | Frequency | Phrase                           |
|------|-----------|----------------------------------|
| 1    | 863       | in den usa                       |
| 3    | 387       | lacher des tages                 |
| 28   | 209       | das ehemalige nachrichtenmagazin |
| 49   | 173       | bug des tages                    |
| 56   | 166       | die amis haben                   |

Runner-up among the 3-grams is "das ist ja", and then we have "das ist ein" and "was für eine" ranking 4th and 5th. Sure, all these high-frequent 3-grams add to Fefe's stylometric fingerprint, but since we're not (yet) doing stylometry here, we decided to curate the n-gram lists a bit to not overthrow you with endless lists of boring syntagmas.

## 4-Grams

| Rank | Frequency | Phrase                     |
|------|-----------|----------------------------|
| 3    | 214       | kommt ihr nie drauf        |
| 10   | 115       | stellt sich raus dass      |
| 13   | 109       | oh und wo wir              |
| 38   | 75        | kennt ihr den schon        |
| 39   | 75        | was für eine farce         |
| 49   | 68        | wie arsch auf eimer        |
| 61   | 61        | einmal mit profis arbeiten |
| 67   | 60        | wir werden alle störben    |
| 69   | 59        | wer hätte das gedacht      |

## 5-Grams

| Rank | Frequency | Phrase                        |
|------|-----------|-------------------------------|
| 21   | 62        | habt ihr das auch gehört      |
| 42   | 45        | bei uns ist kernkraft sicher  |
| 50   | 40        | bei uns ist atomkraft sicher  |
| 58   | 37        | was kann da schon passieren   |
| 81   | 30        | was kann da schon schiefgehen |

## 6-Grams

| Rank | Frequency | Phrase                              |
|------|-----------|-------------------------------------|
| 2    | 89        | oh und wo wir gerade bei            |
| 7    | 65        | die polizei dein freund und helfer  |
| 10   | 60        | na dann ist ja alles gut            |
| 13   | 52        | da weiß man was man hat             |
| 17   | 41        | update mir mailt gerade jemand dass |
| 25   | 35        | das geht ja mal gar nicht           |

## 7-Grams

The 7-grams are the best and prove to be **real Fefe earworms**, don't they?

| Rank | Frequency | Phrase                                      |
|------|-----------|---------------------------------------------|
| 1    | 85        | also damit konnte ja wohl niemand rechnen   |
| 2    | 76        | die besten der besten der besten sir        |
| 3    | 63        | das wird euch jetzt sicher genau so         |
| 4    | 52        | kann man sich gar nicht ausdenken sowas     |
| 5    | 48        | aus der beliebten kategorie bei uns ist     |
| 6    | 38        | man sich mal auf der zunge zergehen         |
| 12   | 33        | aus der beliebten reihe bei uns ist         |
| 13   | 33        | aus der beliebten serie bei uns ist         |
| 15   | 31        | wo kämen wir da auch hin wenn               |
| 24   | 25        | beste demokratie die man für geld kaufen    |
| 30   | 24        | da fühlt man sich doch gleich viel          |
| 33   | 21        | gar nicht so viel fressen wie man           |

## Fun Part I: Given Names of German IT Guys

When Fefe posts a link, hint or story that someone sent him, he gives due credit, the pattern being "(Danke, [name].)" So we also looked into 2-grams starting with "danke", and while the result was somehow predictable, it is still quite funny, isn't it? It not only sheds a light on who Fefe's fiercest audience is, but also shows the opulence of names given to German boys in the 1970ies and 1980ies.

| Rank | Frequency | 2-Gram/Name     |
|------|-----------|-----------------|
| 1    | 237       | danke mathias   |
| 2    | 220       | danke frank     |
| 3    | 183       | danke christian |
| 4    | 176       | danke thomas    |
| 5    | 164       | danke stefan    |
| 6    | 135       | danke andreas   |
| 7    | 135       | danke michael   |
| 8    | 106       | danke martin    |
| 9    | 106       | danke peter     |
| 10   | 100       | danke daniel    |
| 11   | 100       | danke klaus     |
| 12   | 95        | danke matthias  |
| 13   | 94        | danke florian   |
| 14   | 94        | danke jan       |
| 15   | 91        | danke rop       |
| 16   | 84        | danke jens      |
| 17   | 73        | danke timo      |
| 18   | 73        | danke tobias    |
| 19   | 65        | danke sebastian |
| 20   | 64        | danke markus    |
| 21   | 59        | danke alexander |
| 22   | 55        | danke johannes  |
| 23   | 55        | danke jörg      |
| 24   | 54        | danke kris      |
| 25   | 49        | danke ralf      |
| 26   | 45        | danke lutz      |
| 27   | 45        | danke sven      |
| 28   | 43        | danke julian    |
| 29   | 42        | danke christoph |
| 30   | 39        | danke philipp   |
| 31   | 39        | danke stephan   |
| 32   | 37        | danke gerry     |
| 33   | 37        | danke hans      |
| 34   | 36        | danke simon     |
| 35   | 35        | danke bernd     |

Somebody suggested to put the names in a word cloud, but we hate word clouds. :)

If you happen to know some of Fefe's friends and colleagues, you can surely guess who is behind some of the credits pinned to a name (disclosure: we, the authors of this article, have been thanked at least twice, too, if we recall correctly).

## Fun Part II: Using Markov Chains to Generate Fefe Texts

And now, this: Let's generate some pseudo random Fefe text by using Markov chains. For this experiment we quickly forked dellis23's [markov.py script](https://gist.github.com/dellis23/6174914) and adjusted it, the chain size we worked with is 3 and gives us results like this:

> Ziegen fickt", erklärte drastisch US-Präsident Harry S. Truman einem nachdenklichen Kongressabgeordneten. "Wenn er aus und das Ende des Tages: Die Belegschaft sagt, dass die Behörden so 2009 herum angefangen, missliebige Mitbürgern nach allen Regeln der Kunst auseinandernehmen. Ich weiß, welches T-Shirt ich ab jetzt haben, wo sie den Hartz IV kürzen will, stürmen noch schnell und lautlos miterledigen. Keine weiteren Fragen. Die Mühlen der Full-Disclosure-Fraktion bei Sicherheitslücken: Der Jeep-Hack neulich wurde noch der Presse. Erstens: Nachtsicht- und GPS-Geräte kaufen -> 3 Jahre Haft vorgeschlagen. (Danke, Marcel) Die Russen sind schlauer als der losredete, war das in der Türkei.

This is far from being anything worthwhile and the mere result of toying around with this juicy corpus. But alright, let's generate another one:

> Mit Terrorismus hat das mit Cyberangriffen deutlich anders aus, Stichwort Lawful Interception. Wieder was gelernt, diesmal über amerikanische Studenten: Ich habe ehrlich gesagt nicht so aus, dass der vor Gericht erstreiten muss, kann ich nur mit Adblocker nicht zu uns, denn in westlichen Demokratien wie der öffentliche GNU-CVS-Server, furchtbar überlastet ist, und daher muss auch sein Lebensunterhalt direkt davon abhängt, dass er jetzt alles seine Ordnung" um. Denn die Labels daran zugrunde gehen werden. Francesco-Parisi-Universität Styrum — endlich mal was tun diesmal! Sonst lassen die Regierung mit den Nazis damals funktionieren. Zweitens: Wir merken es oft nicht gelöscht würden.

The code is quite simple and can sure be optimised in many ways, but for today the Fefe Research Institute pulls the plug.
