---
title: "Updates on Vossantos"
layout: post
author: [robert, frank]
comments: true
date: 2020-08-17
---


## Timeline

- new: Timeline
  - link to https://vossanto.weltliteratur.net/timeline/#1077956_3

- screenshot with explanation?


## Automatic Detection of Vossantos


- continuous improvements on the approach
- EMNLP-IJCNLP 2019 paper
  - technical background
- but also working on further improvements
  - sequence labelling
	- to also identify modifier + target!
	- thus: labelled data now also comprises modifier + target


## Modifiers

  - thus: Stats for Modifer available:
	- https://vossanto.weltliteratur.net/emnlp-ijcnlp2019/statistics.html#modifiers

  for example: countries


| count |	country      |
+-------+----------------+
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


or sports

| count		 | sports                                                |
|------------+-------------------------------------------------------|
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
