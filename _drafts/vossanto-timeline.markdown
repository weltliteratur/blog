---
title: "Updates on Vossian Antonomasia"
layout: post
author: [robert, frank]
comments: true
date: 2020-08-17
---

Our [last article on Vossian
Antonomasia](https://weltliteratur.net/vossian-antonomasia-new-york-times/)
appeared more than a year ago, yet, since then we were busy improving
our methods, writing papers, and extending the [web
page](https://vossanto.weltliteratur.net/). This blog post provides an
update on recent developments.


## Timeline

Last year [our research
group](https://www.ibi.hu-berlin.de/de/forschung/info_processing_analytics)
run a small code sprint to create a platform to visually explore our
New York Times corpus of Vossian Antonomasia. Thanks to [Sjaak
Priester](https://github.com/sjaakp) and his excellent [JavaScript
Dateline widget](https://github.com/sjaakp/dateline) we could quickly
set up a [timeline](https://vossanto.weltliteratur.net/timeline/):

![Timeline Example: Michael Jordan](../images/va_timeline_mj.png)

It contains all Vossian Antonomasia from our [2019 EMNLP-IJCNLP
paper](https://doi.org/10.18653/v1/D19-1647). Each Vossanto is
represented by a circle and the name of its source (the entity whose
properties or qualities are transferred to another entity). The color
of the circle indicates the New York Times desk that is responsible
for the corresponding article. By clicking on an entry more
information is shown, as can be seen in the above screenshot:

- a photo from [Wikimedia Commons](https://commons.wikimedia.org/)
  (for most sources),
- the sentence containing the Vossian Antonomasia with **source** and
  *modifier* highlighted,
- the article id with a link to the article's web page,
- the name of the author,
- the name of the desk,
- the source and license for the photo,
- a permanent link to that Vossian Antonomasia.

If you want to test it yourself, you can either scroll through the
 [timeline](https://vossanto.weltliteratur.net/timeline/) or just
 follow [this example](https://vossanto.weltliteratur.net/timeline/#1077956_3).

Not just a gimmick but really helpful is another feature, almost
hidden in the top left corner: the full text search facility. After
typing some words it shows all Vossian Antonomasia that contain the
word. Clicking on a match scrolls to the corresponding point in the
timeline and shows the details. This provides many more opportunities
to find interesting Vossian Antonomasia! For example, search for
*Germany* or *Bill gates* to find where he was used as [the
target](https://vossanto.weltliteratur.net/timeline/#1037053_0).

## Automatic Detection of Vossantos


- continuous improvements on the approach
- EMNLP-IJCNLP 2019 [paper](https://doi.org/10.18653/v1/D19-1647)
  - technical background
- but also working on further improvements
  - sequence labelling
	- to also identify modifier + target!
	- thus: labelled data now also comprises modifier + target


## Modifiers

Since we need labelled data for training and evaluating our machine
learning approaches, we went over more than 3000 Vossantos to also
annotate their modifiers andtargets. Therefore, we can now present
reliable statistics on the most frequent modifiers in the corpus. The
top ten are:

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
for example, countries:


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


or sports:

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


lengths (number of words) of modifiers


## JSON Data Dump


- [data is now also available in
JSON](https://github.com/weltliteratur/vossanto/blob/master/timeline/vossantos.json)
which simplifies re-usability. As a bonus, links to images for sources
on [Wikimedia Commons](https://commons.wikimedia.org/) are included
und damit leichter nachnutzbar as well as links to
[Wikidata](https://www.wikidata.org/). Example:

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
explanation for fields:



## Future

- other languages
- better understand usage


Finally, as always: all details on https://vossanto.weltliteratur.net/
