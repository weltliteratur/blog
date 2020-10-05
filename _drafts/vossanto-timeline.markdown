---
title: "Updates on Vossian Antonomasia"
layout: post
author: [robert, frank]
comments: true
date: 2020-08-17
---

Our [last article on Vossian
Antonomasia](https://weltliteratur.net/vossian-antonomasia-new-york-times/)
(*Vossanto*) appeared more than a year ago, yet, since then we were
busy improving our methods, writing papers, and extending the [web
page](https://vossanto.weltliteratur.net/). This blog post provides an
update on recent developments.


## Timeline

Last year [our research group at
IBI](https://www.ibi.hu-berlin.de/de/forschung/info_processing_analytics)
run a small code sprint to create a visual exploration platform for
our New York Times corpus of Vossantos. Thanks to [Sjaak
Priester](https://github.com/sjaakp) and his excellent [JavaScript
Dateline widget](https://github.com/sjaakp/dateline) we could quickly
set up a [timeline](https://vossanto.weltliteratur.net/timeline/):

![Timeline Example: Michael Jordan](../images/va_timeline_mj.png)

It contains all Vossantos from our [2019 EMNLP-IJCNLP
paper](https://doi.org/10.18653/v1/D19-1647). Each Vossanto is
represented by a circle and the name of its source (the entity whose
properties or qualities are transferred to another entity). The color
of the circle indicates the New York Times desk that is responsible
for the corresponding article. By clicking on an entry more
information is shown, as can be seen in the above screenshot:

- a photo from [Wikimedia Commons](https://commons.wikimedia.org/)
  (for most sources),
- the sentence containing the Vossanto with **source** and *modifier*
  highlighted,
- the article id with a link to the article's web page,
- the name of the author,
- the name of the desk,
- the source and license for the photo,
- a permanent link to that Vossanto.

If you want to test it yourself, you can either scroll through the
 [timeline](https://vossanto.weltliteratur.net/timeline/) or just
 follow [this example](https://vossanto.weltliteratur.net/timeline/#1077956_3).

Not just a gimmick but really helpful is another feature, almost
hidden in the top left corner: the full text search facility. After
typing some words it shows all Vossantos that contain the
word. Clicking on a match scrolls to the corresponding point in the
timeline and shows the details. This provides many more opportunities
to find interesting Vossanto! For example, search for "literature" to
find [a Vossanto together with its
explanation](https://vossanto.weltliteratur.net/timeline/#1097313_0).

<!--
 - "Lenin" liefert
  https://vossanto.weltliteratur.net/timeline/#0151446_0 etwas
  literaturhistorisch interessantes

-->

## Automatic Detection of Vossantos

Let us recall the VA extraction approach from our first paper. The approach was semi-automated, sentence-based and focused on humans.
First, we used regular expressions to extract all sentence candidates with one out of nine syntactical VA source pattern, e.g. 'the ENTITY of'.
The key idea was to use Wikidata as an external database for distant supervision.
We kept those sentences as candidates that included the exact name or alias of Wikidata entities with 'instance-of' prtoperty 'human'. 
Afterwards we created manually a 'blacklist' with words that are also common nouns or otherwise unlikely to be a source of VA to exlude candidates like 'the House of' (as 'House' is an alias of the botanist 'Homer Doliver House' and was kept as a candidate in the seccond step).

In our EMNLP-IJCNLP 2019 [paper](https://doi.org/10.18653/v1/D19-1647) we automated the process of extracting VA from text.
We developed three different approaches.
The first approach is mainly based on the old approach, but instead of using a manually curated blacklist, we introduced a 'popularity measure' to find out, which candidates after the Wikidata linking step should be removed.
In detail, we used Wikidata again and compared the 'popularity' (e.g. the number of Wikidata sitelinks per entity) between the human entity and if exisiting, another entity having the same label, e.g. the human entity 'House' (the botanist) only has 9 sitelinks, the entity 'House' (the building) has 178 sitelinks. Thus we removed those candidates since it was unlikely that the linking in the Wikidatastep was right.

In addition, we removed all candidates where the source (e.g., ‘Prince’) together with multiplewords following it (e.g., ‘of Wales’) matched the name or alias of another Wikidata entity (https://www.wikidata.org/wiki/Q43274). This allowed us to remove frequent false positives like ‘Prince of Wales’.

As we focused on 'persons' as a VA source, our seccond approach is based on named entity recognition.
Instead of using Wikidata to detect sentence candidates, we used the NER tool to detect entities.
We also used the last step from the first approach (detecting false positives).

Our last approach is based on the corpus from our old approach:
In particular, we used the labeled corpus as a training dataset and trained a neural network. First we transformed each word of a sentence into a word vector, using pre-trained word embeddings (e.g. GloVe embeddings).

Afterwards we fed our neural network with these vectors. Our network consists of a bi-directional long short-term memory layer (BLSTM) and a feedforward layer on top of it to compute the binary label.

Evaluating the approaches is a hard problem itself because of the sparsity of the phenomen. It is unfeasible to determine recall on the whole NYT corpus.
Instead we compute precision, recall and f1 based on the labeled corpus.
The BLSTM performs best, boosting the precision to 87%.
The results are shown in the following table:

| Approach                 | Precision | Recall |    F1 |
|--------------------------+-----------+--------+-------|
| semi-automated           |     49.8% |      - |     - |
| Wikidata                 |     67.3% |  93.0% | 78.1% |
| Named-entity-recognition |     71.8% |  81.3% | 76.2% |
| BLSTM                    |     86.9% |  85.3% | 86.1% |



At the moment we are working on different approaches to detect all parts (i.e. target, source and modifier) of VA in a sentence.
One side effect is an enriched corpus, having all parts of VA tagged in each positive labeled sample.




## Modifiers

Since we need labelled data for training and evaluating our machine
learning approaches, we went over more than 3000 Vossantos to also
annotate their modifiers and targets. Therefore, we can now present
reliable statistics on the most frequent modifiers in the corpus. The
top ten modifiers are:

| count | modifier       |
|-------|----------------|
|    56 | his day        |
|    34 | his time       |
|    29 | Japan          |
|    17 | China          |
|    16 | tennis         |
|    16 | his generation |
|    16 | baseball       |
|    14 | her time       |
|    13 | our time       |
|    13 | her day        |

A [longer
list](https://vossanto.weltliteratur.net/emnlp-ijcnlp2019/statistics.html#modifiers)
together with many examples can be found on the latest [statistics
page](https://vossanto.weltliteratur.net/emnlp-ijcnlp2019/statistics.html).

By filtering the modifiers we can create rankings for specific themes,
for example,
[countries](https://vossanto.weltliteratur.net/emnlp-ijcnlp2019/statistics.html#country):


| count |	country      |
|-------|----------------|
|    29 |	Japan        |
|    17 |	China        |
|    10 |	Brazil       |
|     8 |	Iran         |
|     7 |	Mexico       |
|     7 |	Israel       |
|     7 |	India        |
|     4 |	South Africa |
|     4 |	Poland       |
|     3 |	Spain        |


or [sports](https://vossanto.weltliteratur.net/emnlp-ijcnlp2019/statistics.html#sports):

| count		 | sports                                                |
|------------|-------------------------------------------------------|
|         16 | tennis                                                |
|         16 | baseball                                              |
|         10 | basketball                                            |
|          8 | golf                                                  |
|          8 | football                                              |
|          6 | soccer                                                |
|          6 | racing                                                |
|          3 | women's basketball                                    |
|          3 | sailing                                               |
|          3 | auto racing                                           |
|          2 | pro football                                          |
|          2 | New York baseball                                     |
|          1 | Yale football fame                                    |
|          1 | women's college soccer                                |
|          1 | this year's national collegiate basketball tournament |
|          1 | the tennis tour                                       |
|          1 | the tennis field                                      |
|          1 | the soccer set                                        |
|          1 | the racing world                                      |
|          1 | stock-car racing                                      |
|          1 | Rotisserie baseball                                   |
|          1 | pro football owners                                   |
|          1 | professional basketball coaches                       |
|          1 | professional basketball                               |
|          1 | motocross racing in the 1980's                        |
|          1 | micro golfers                                         |
|          1 | major league baseball                                 |
|          1 | Laser sailing                                         |
|          1 | Japanese baseball                                     |
|          1 | Iraqi soccer                                          |
|          1 | horse racing                                          |
|          1 | high school baseball in New York                      |
|          1 | harness racing                                        |
|          1 | golf criticism                                        |
|          1 | football teams                                        |
|          1 | football owners                                       |
|          1 | football announcers                                   |
|          1 | country-club golf                                     |
|          1 | college football these days                           |
|          1 | college football                                      |
|          1 | college basketball                                    |
|          1 | Chinese baseball                                      |
|          1 | Brazilian basketball for the past 20 years            |
|          1 | BMX racing                                            |
|          1 | biddy basketball                                      |
|          1 | basketball announcers                                 |
|          1 | basketball analysts                                   |
|          1 | basketball analysis                                   |
|          1 | baseball's new era                                    |
|          1 | baseball managers                                     |
|          1 | baseball executives                                   |
|          1 | baseball collections                                  |
|          1 | baseball cards                                        |

Apparently, Vossantos are used to introduce athletes and personalities
from foreign countries that are (supposedly) unknown to the reader.

Most modifiers are short, consisting of only one to three words, as
this plot of the distribution of the length (number of words) of
modifiers shows:

![modifier length distribution](https://raw.githubusercontent.com/weltliteratur/vossanto/master/emnlp-ijcnlp2019/nyt_vossantos_modifier_length.png)

The longest modifier we have found so far contains 25 words:

And while he modestly demurs, Mr. Barker is widely regarded as the
**Bob Fosse** of *the carefully choreographed event that consumes
Midtown Manhattan with tin whistles, step dancers and some two million
spectators on that invariably brisk March 17 morning*. (source:
[2001/03/07/1276052](http://query.nytimes.com/gst/fullpage.html?res=9B04E3DE1E3BF934A35750C0A9679C8B63))


## JSON Data Dump

As a side effect of the timeline, the [dataset is now also available
in JSON
format](https://github.com/weltliteratur/vossanto/blob/master/timeline/vossantos.json).
As a bonus, the JSON data contains links to
[Wikidata](https://www.wikidata.org/) as well as links to images for
sources on [Wikimedia Commons](https://commons.wikimedia.org/)
(including license information) and thus can easily be re-used for
further analyses or demos. The following excerpt shows a JSON entry
for an exemplary Vossanto:

```json
{
   "id": "0039183_0",
   "date": "1987-05-10",
   "sourceId": "Q9696",
   "sourceLabel": "John F. Kennedy",
   "sourceImId": "John_F._Kennedy,_White_House_color_photo_portrait.jpg",
   "sourceImThumb": "thumb/c/c3/John_F._Kennedy%2C_White_House_color_photo_portrait.jpg/180px-John_F._Kennedy%2C_White_House_color_photo_portrait.jpg",
   "sourceImLicense": "pd",
   "fId": "1987/05/10/0039183",
   "aUrlId": "9B0DE3DD1E3EF933A25756C0A961948260",
   "text":
   "In the 60's Mr. Bernstein looked like *the John F. Kennedy of* /culture/.",
   "author": "Botstein, Leon", "desk": "Book Review Desk"
}
```

The fields contain the following information:

| key             | content                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------|
| id              | A unique (within the dataset) identifier for the Vossanto.                                 |
| date            | Publication date of the NYT article.                                                       |
| sourceId        | The Wikidata id of the Vossanto's source.                                                  |
| sourceLabel     | The (English) Wikidata label of the source.                                                |
| sourceImId      | The name of the source's image on Wikimedia Commons.                                       |
| sourceImThumb   | The path to the source's image on Wikimedia Commons.                                       |
| sourceImLicense | The license of the source's image.                                                         |
| fId             | The id of the article's file in the NYT dataset.                                           |
| aUrlId          | The id of the article in its URL (`http://query.nytimes.com/gst/fullpage.html?res=<HERE>`) |
| text            | The sentence containing the Vossanto (including ord-mode markup).                          |


## Future

We are very much interested in analysing Vossantos in other languages
than English (specifically, German) and looking for suitable
corpora. Apart from that, our goal is to better understand their usage
and variety.


Finally, as always: all details on https://vossanto.weltliteratur.net/
