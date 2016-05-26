---
title: Empirical Data on Over-Length Books
layout: post
author: [frank, ubbo]
comments: true
date: 2016-05-25
---

(Little note upfront: The technical part of this posting involves Docker, RDF→XSLT→JSON, Elasticsearch and Kibana. More on this at the bottom of this page or without further ado [on our GitHub repo](https://github.com/lehkost/DNBTitel-Elasticsearch). Our solution is the result of nothing more than a 4-hour hackathon, so don't expect anything polished.)

As a preliminary for a **study of over-length books** (novels, primarily) we wanted to gather more empirical data. There is still this ["List of longest novels"](https://en.wikipedia.org/wiki/List_of_longest_novels) in the English Wikipedia, but this list is problematic, because it's obviously canon-driven and uses completely different measures to define the extent of books. We also gathered some evidence on our own, a [list with novels of more than a thousand pages](http://www.umblaetterer.de/2014/10/21/tausendseiter/), on another blog (the explanatory text there is in German, watch out). Our list is sorted chronologically, since this is one aspect we have to take into account when planning to pen something like a "History of the Over-Length Novel".

Using the number of pages as measurement is, of course, part of the problem. It would be better to work with number of letters or words per work, but this is not (yet?) part of bibliographic metadata. So, number of pages. How do we access them, large-scale?

## German National Library Enters the Stage

Let's start with this panoramic view of the German Library in Leipzig, predecessor and now part of the German National Library (DNB) – please also note the book towers on the left side:

<figure>
  <img src="/images/dnb-german-library-leipzig-2008.jpg" alt="Panoramic view of the German national Library, source: Wikimedia Commons." />
  <figcaption>Source: <a href="https://commons.wikimedia.org/wiki/File:Deutsche_Buecherei_(German_Library)_2008-Feb.jpg">Wikimedia Commons</a> (CC BY-SA 3.0)</figcaption>
</figure>

Really nice, yes, but it's another kind of picture of the actual German National Library that we're going to show you, one that is much more to the point. When we came across the [data-service page of the German National Library](http://datendienst.dnb.de/cgi-bin/mabit.pl?userID=opendata&pass=opendata&cmd=login), we were almost enthusiastic. They offer different kinds of sets in different formats (all licenced under CC0 1.0!), from which we chose the "DNBTitel.rdf.gz" one comprising the records for all books/items archived at the DNB library (the dump was generated on March 10, 2016, and is 1,5 GB in size, which makes for an uncompressed 21,3 GB). There's no SPARQL endpoint (yet?) by which users could query the catalogue data directly (but you can register for access via [OAI](http://www.dnb.de/oai) and [SRU](http://www.dnb.de/sru)). So, as said before, we decided to download the RDF file and started to build our own query thing.

Now, the other picture of the German National Library we wanted to show you is this:

<figure>
  <img src="/images/dnb-matrix-view-subjects-objects.png" alt="HDT matrix front view: subjects meet objects." />
</figure>

This is the matrix view of the RDF file we downloaded, a 3D scatter plot of triples generated with [HDT-it!](http://www.rdfhdt.org/). Each predicate there has a different colour. In this front view, subjects meet objects, but we can see a pink predicate gleaming through, we're looking at ISBD element [P1053](http://iflastandards.info/ns/isbd/elements/P1053) ("has extent"), the thing we'll be looking at in the following:

<figure>
  <img src="/images/dnb-matrix-view-pink-predicate.png" alt="HDT matrix front view: pink predicate gleaming through." />
</figure>

## Some Results

Btw, we started this little project as part of a spontaneous 4-hour hackathon last July, at the R&D department of the Göttingen State and University Library. Now, just about a year later, we decided to wrap it up a bit and show you how we made it work.

First and foremost, you have to be aware of the history of the German National Library to know what you can expect from any query result. The gist of it is: They were a bit late compared to other national libraries in Europe and began collecting "all German and German-language publications from 1913, foreign publications about Germany, translations of German works, and the works of German-speaking emigrants published abroad between 1933 and 1945" (quoting the official ["About us" page](http://www.dnb.de/EN/Wir/wir_node.html)).

Before we bore you with how we did it, let's go for some results. As a proof of concept, let's see which authors are the ones with the most books in the catalogue (`dcterms:creator`), let's generate a top 25:

<figure>
  <img src="/images/dnb-25-authors-with-most-books.png" alt="Bar chart: 25 authors with most books in the German National Library." />
</figure>

In the bar chart above, the authors are identified by their GND records. Very well then, let's resolve them:

| DNB Identifier                              | Number of Records | Author                      |
|---------------------------------------------|-------------------|-----------------------------|
| [118540238](http://d-nb.info/gnd/118540238) | 5792              | Goethe, Johann Wolfgang von |
| [118617443](http://d-nb.info/gnd/118617443) | 3881              | Steiner, Rudolf             |
| [118577166](http://d-nb.info/gnd/118577166) | 3402              | Mann, Thomas                |
| [11855042X](http://d-nb.info/gnd/11855042X) | 3336              | Hesse, Hermann              |
| [11856515X](http://d-nb.info/gnd/11856515X) | 3227              | Konsalik, Heinz G.          |
| [118637479](http://d-nb.info/gnd/118637479) | 2995              | Zweig, Stefan               |
| [118542257](http://d-nb.info/gnd/118542257) | 2840              | Grimm, Jacob                |
| [118578537](http://d-nb.info/gnd/118578537) | 2732              | Marx, Karl                  |
| [118542265](http://d-nb.info/gnd/118542265) | 2721              | Grimm, Wilhelm              |
| [118530380](http://d-nb.info/gnd/118530380) | 2504              | Engels, Friedrich           |
| [12002179X](http://d-nb.info/gnd/12002179X) | 2478              | Schaal, Eric                |
| [118607626](http://d-nb.info/gnd/118607626) | 2405              | Schiller, Friedrich         |
| [118618725](http://d-nb.info/gnd/118618725) | 2133              | Storm, Theodor              |
| [118514768](http://d-nb.info/gnd/118514768) | 2132              | Brecht, Bertolt             |
| [118559230](http://d-nb.info/gnd/118559230) | 2100              | Kafka, Franz                |
| [118559206](http://d-nb.info/gnd/118559206) | 2086              | Kästner, Erich              |
| [118818651](http://d-nb.info/gnd/118818651) | 2080              | May, Karl                   |
| [118613723](http://d-nb.info/gnd/118613723) | 2070              | Shakespeare, William        |
| [11856109X](http://d-nb.info/gnd/11856109X) | 1828              | Keller, Gottfried           |
| [118512676](http://d-nb.info/gnd/118512676) | 1818              | Böll, Heinrich              |
| [118601024](http://d-nb.info/gnd/118601024) | 1794              | Rilke, Rainer Maria         |
| [118587943](http://d-nb.info/gnd/118587943) | 1781              | Nietzsche, Friedrich        |
| [118534262](http://d-nb.info/gnd/118534262) | 1755              | Fontane, Theodor            |
| [118533436](http://d-nb.info/gnd/118533436) | 1677              | Fischer, Marie Louise       |
| [118520628](http://d-nb.info/gnd/118520628) | 1674              | Christie, Agatha            |

Looks plausible, in a way. And interesting enough for an interpretation (which, for the time being, we won't deliver). One thing becomes clearer now, though, we should really talk about "items", rather than "books". Photographer Eric Schaal, for example, didn't get into this top 25 by writing more than two thousand books. To be honest, we made a top 25 just to get at least some women into this board of men, ranking 24th and 25th. And stating the obvious, Goethe also didn't write almost six thousand books since 1913, what really puts weight on the authors is the substantial number of re-editions, of course.

## Number of Books/Items in the Catalogue

We've got 11.373.862 items altogether (some didn't make it into the Elasticsearch index since we didn't really address error handling or validation; the regexps in our XSLT weren't perfect either, things we can improve next time we're not high-speed hackathoning). Anyway, in **5.874.504 cases** we successfully parsed the [`isbd:P1053`](http://iflastandards.info/ns/isbd/elements/P1053) element (= "has extent") into a usable number of pages, summing up to a total number of 969.846.170 pages. The max number of pages in this set is 2.711.111, which is obviously the result of a metadata apocalypse, somebody must have slipped on the `1` key ([**this** is the book that's said to have more than two million pages](http://d-nb.info/965667081)).

You can glean from our [XSLT file](https://github.com/lehkost/DNBTitel-Elasticsearch/blob/master/dnb2es/rdf2json.xsl) that we're only using extent information if we found a number succeeded by " S." (= "pages") in the `isbd:P1053` string. So we're not using at least 5.499.358 items out of the 11.373.862. Either they had no information on the book extent/number of pages or we didn't parse it because we just used a very basic pattern. But with this simple method we still managed to cover 51,65% of all the books/items stored in the German National Library. We can sure improve our data extraction, but for the time being we're good with what we have. After all, we're still speaking about almost six million book records.

Now onto some more meaningful stuff. Let's take five major publishers and compare them just by looking at the extent of their books. We held a little powwow and, full of intentional bias, chose Aufbau, Eichborn, Hanser, Rowohlt, Suhrkamp. Let's have a look at the number of items per publisher in the catalogue:

<figure>
  <img src="/images/dnb-5-publishers-number-of-items.png" alt="Bar chart: 5 publishers, number of items." />
</figure>

This is an interesting perspective, also if this comparison makes not much sense. For all we know, there could be thousands of re-editions involved. Well, okay.

## Average Number of Pages per Book per Publisher

<figure>
  <img src="/images/dnb-5-publishers-average-number-of-pages.png" alt="Bar chart: 5 publishers, average number of pages." />
</figure>

So obviously, the average Suhrkamp book beats the average Rowohlt book beats the average Eichborn book when considering the number of pages. This comparison is intriguing, but it shouldn't be taken too literally, we're dealing with a certain amount of incorrect metadata as we'll see in the next set of lists.

## Longest Books per Publisher

This brings us a bit closer to our goal. But these lists also show the problems of erroneous data and the need for additional metadata. If we want to look into over-length novels, we'll obviously need another indicator, one of which is not provided by the current DNB dataset. And once again, the lists clarify that it's more appropriate to speak of "item" than of "book", but now let's start with the rankings:

### Aufbau

| DNB Identifier                            | Number of Pages | Author: Title (Year)                            |
|-------------------------------------------|-----------------|-------------------------------------------------|
| [988488205](http://d-nb.info/988488205)   | 1359 S.         | Vikram Chandra: Der Pate von Bombay (2009)      |
| [1001932447](http://d-nb.info/1001932447) | 1291 S.         | Lew Tolstoi: Krieg und Frieden (2010)           |
| [576696420](http://d-nb.info/576696420)   | 1286 S.         | Alexej Tolstoi: Der Leidensweg (2. Aufl., 1955) |
| [576696439](http://d-nb.info/576696439)   | 1286 S.         | Alexej Tolstoi: Der Leidensweg (3. Aufl., 1959) |
| [1011565994](http://d-nb.info/1011565994) | 1243 S.         | Hans Fallada: Wolf unter Wölfen (2011)          |
| [98848823X](http://d-nb.info/98848823X)   | 1227 S.         | Lew Tolstoi: Anna Karenina (2008)               |
| [945188846](http://d-nb.info/945188846)   | 1211 S.         | Friedrich Gorenstein: Der Platz (1995)          |
| [988488272](http://d-nb.info/988488272)   | 1200 S.         | Fjodor Dostojewski: Die Brüder Karamasow (2008) |
| [949346470](http://d-nb.info/949346470)   | 1183 S.         | Lew Tolstoi: Anna Karenina (1996)               |
| [451896025](http://d-nb.info/451896025)   | 1174 S.         | G. W. F. Hegel: Ästhetik (1955)                 |

### Eichborn

| DNB Identifier                          | Number of Pages | Author: Title (Year)                                                       |
|-----------------------------------------|-----------------|----------------------------------------------------------------------------|
| [946561486](http://d-nb.info/946561486) | <s>1814 S.</s>  | (wrong number of pages)                                                    |
| [967526825](http://d-nb.info/967526825) | 1222 S.         | Leo Tolstoi: Krieg und Frieden (2003)                                      |
| [950298603](http://d-nb.info/950298603) | 1081 S.         | Rolf Vollmann: Die wunderbaren Falschmünzer (1997)                         |
| [988571005](http://d-nb.info/988571005) | 991 S.          | Daniel Schwartz: Schnee in Samarkand (2008)                                |
| [979687187](http://d-nb.info/979687187) | 954 S.          | Paul Verhaeghen: Omega minor (2006)                                        |
| [974540919](http://d-nb.info/974540919) | 855 S.          | David M. Crowe: Oskar Schindler (2005)                                     |
| [979691044](http://d-nb.info/979691044) | 852 S.          | Laurence Sterne: Leben und Ansichten von Tristram Shandy, Gentleman (2006) |
| [840181604](http://d-nb.info/840181604) | 841 S.          | Fred Denger: Der grosse Boss (1984)                                        |
| [860929477](http://d-nb.info/860929477) | 841 S.          | Fred Denger: Der grosse Boss (6. Aufl., 1985)                              |
| [870140876](http://d-nb.info/870140876) | 841 S.          | Fred Denger: Der grosse Boss (5. Aufl., 1985)                              |

### Hanser

| DNB Identifier                            | Number of Pages | Author: Title (Year)                                               |
|-------------------------------------------|-----------------|--------------------------------------------------------------------|
| [1022146394](http://d-nb.info/1022146394) | <s>4587 S.</s>  | (wrong number of pages)                                            |
| [99886398X](http://d-nb.info/99886398X)   | 1810 S.         | Walter Doberenz; Thomas Gewinnus: Visual C# 2010 (2010)            |
| [98401098X](http://d-nb.info/98401098X)   | 1806 S.         | Walter Doberenz; Thomas Gewinnus: Borland Delphi 7 (2007)          |
| [998863955](http://d-nb.info/998863955)   | 1802 S.         | Walter Doberenz; Thomas Gewinnus: Visual Basic 2010 (2010)         |
| [760043035](http://d-nb.info/760043035)   | 1672 S.         | Joseph von Eichendorff: Werke (4. Aufl., 1971)                     |
| [451062442](http://d-nb.info/451062442)   | 1606 S.         | Joseph von Eichendorff: Werke (2. Aufl., 1959)                     |
| [451062817](http://d-nb.info/451062817)   | 1590 S.         | Joseph von Eichendorff: Werke (1. Aufl., 1955)                     |
| [453424740](http://d-nb.info/453424740)   | 1511 S.         | Eduard Mörike: Sämtliche Werke (3. Aufl., 1964)                    |
| [780204875](http://d-nb.info/780204875)   | 1511 S.         | Eduard Mörike: Sämtliche Werke (5. Aufl., 1976)                    |
| [970961294](http://d-nb.info/970961294)   | 1469 S.         | Uwe Bünning; Jörg Krause: Windows XP Professional (3. Aufl., 2004) |

### Rowohlt

| DNB Identifier                            | Number of Pages | Author: Title (Year)                                           |
|-------------------------------------------|-----------------|----------------------------------------------------------------|
| [944325807](http://d-nb.info/944325807)   | 2253 S.         | Klaus Harpprecht: Thomas Mann (1995)                           |
| [945394659](http://d-nb.info/945394659)   | 2253 S.         | Klaus Harpprecht: Thomas Mann (16.–30. Tsd., 1995)             |
| [967713358](http://d-nb.info/967713358)   | 2026 S.         | Karl Corino: Robert Musil (2003)                               |
| [101781905X](http://d-nb.info/101781905X) | 1723 S.         | Péter Nádas: Parallelgeschichten (2012)                        |
| [1028105657](http://d-nb.info/1028105657) | 1723 S.         | Péter Nádas: Parallelgeschichten (Taschenbuch, 2013)           |
| [1008548022](http://d-nb.info/1008548022) | 1719 S.         | Rolf Hochhuth: Essayistische Prosa und Gedichte (2011)         |
| [575594950](http://d-nb.info/575594950)   | 1671 S.         | Robert Musil: Der Mann ohne Eigenschaften (1952)               |
| [961281588](http://d-nb.info/961281588)   | 1642 S.         | Rolf Hochhuth: Alle Erzählungen, Gedichte und Romane (2001)    |
| [457661054](http://d-nb.info/457661054)   | 1632 S.         | Robert Musil: Der Mann ohne Eigenschaften (1970)               |
| [575594969](http://d-nb.info/575594969)   | 1632 S.         | Robert Musil: Der Mann ohne Eigenschaften (23.–29. Tsd., 1960) |

### Suhrkamp

| DNB Identifier                            | Number of Pages | Author: Title (Year)                               |
|-------------------------------------------|-----------------|----------------------------------------------------|
| [946102384](http://d-nb.info/946102384)   | <s>3980 S.</s>  | (wrong number of pages)                            |
| [945262094](http://d-nb.info/945262094)   | <s>2909 S.</s>  | (wrong number of pages)                            |
| [991420225](http://d-nb.info/991420225)   | 2569 S.         | Amos Oz: Die Romane (2009)                         |
| [988814668](http://d-nb.info/988814668)   | 2085 S.         | E. M. Cioran: Werke (2008)                         |
| [986493635](http://d-nb.info/986493635)   | 1909 S.         | Marguerite Duras: Die Romane (2008)                |
| [986531766](http://d-nb.info/986531766)   | 1840 S.         | Thomas Bernhard: Die Romane (2008)                 |
| [991398939](http://d-nb.info/991398939)   | 1838 S.         | Hermann Hesse: Die Erzählungen und Märchen (2009)  |
| [988840758](http://d-nb.info/988840758)   | 1782 S.         | Max Frisch: Romane, Erzählungen, Tagebücher (2008) |
| [998413925](http://d-nb.info/998413925)   | 1782 S.         | Bertolt Brecht: Prosa (2013)                       |
| [1008349852](http://d-nb.info/1008349852) | 1735 S.         | Alejo Carpentier: Die Romane (2011)                |

We won't comment these lists now, although they make for some interesting discussions. You can obviously do much more with what we built here and we'll certainly get back to this later. So let's close this blog post with a short note on how we built this bridge from the freely available DNB catalogue data to the results shown above.

## German National Library Goes Elastisearch

The somewhat weird original idea we had when initiating the hackathon was this: We wanted to know how much the German National Library weighs on books, and we wanted to find out by the number of pages of all the books it stores which we then would have multiplied by the average weight of a book page. Well, you can do the maths yourself now, you can find the total number of pages we counted above and then extrapolate, it will be a good enough approximation.

What saves us time now is that we already described our mechanism [on GitHub](https://github.com/lehkost/DNBTitel-Elasticsearch) where we also provide all the info you need to rebuild our machine. We basically reorganised the whole thing as a Docker project, which will create a container running Elasticsearch/Kibana. The repo also features shell scripts for downloading the current version of the German National Library title catalogue. Some selected data fields from every book in that catalogue are then transformed into JSON and pushed to the Elasticsearch instance. After that you will be able to query the DNB catalogue data with Elasticsearch to create nice outputs with Kibana. As should be clear from the text above, the data fields we're focusing on are mainly the number of pages per book and some book metadata (author, title, year, publisher, etc.) for identification.

That's it for now. And lest we forget, special thanks to Max Brodhun and Carsten Thiel for writing the XSLT and helping with the shell scripting, "as quick as boiled asparagus", so to speak, it was only because of them that we could go on with what we *actually* wanted to do. [The next Uludağ is on us!](https://twitter.com/umblaetterer/status/679317574740533248) ;)
