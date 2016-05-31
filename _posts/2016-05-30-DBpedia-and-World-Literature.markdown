---
title: DBpedia and World Literature
layout: post
author: [robert, frank]
comments: true
date: 2016-05-30
---

After our blog post
["Wikidata Meets World Literature"](Wikidata-Meets-World-Literature)
some might have mumbled into their tea cups, "ok yeah, but what about
DBpedia?" Accordingly, let us add some technological diversity to our
initial experiment. [DBpedia](http://www.dbpedia.org/) is a great
project and follows its very own approach, it is also a few years
older than Wikidata. More on the differences between the two projects
can be found
[on Quora](https://www.quora.com/What-is-the-difference-between-Wikidata-and-DBpedia).

So, DBpedia and World Literature. Let's kick off by translating/simplifying the original SPARQL query to match the DBpedia ontology:

~~~ sql
SELECT ?s ?desc ?authorlabel
WHERE {
  ?s rdf:type dbo:Book .
  ?s dbo:author ?author
  OPTIONAL {
    ?s rdfs:label ?desc FILTER (lang(?desc) = "en").
  }
  OPTIONAL {
    ?author rdfs:label ?authorlabel FILTER (lang(?authorlabel) = "en").
  }
}
~~~

This query **[returns][query-book]** a list of resources that have
been assigned the class
[Book](http://mappings.dbpedia.org/server/ontology/classes/Book) in
the
[DBpedia ontology](http://mappings.dbpedia.org/server/ontology/classes/),
along with their authors. (Yes, just **[click][query-book]**, this
will auto-execute the query and show you the results.)

In our original post we used the number of Wikipedia language versions
per book to rank them, with "One Thousand and One Nights" taking away
all the glory (for the time being, that is). We can try something
similar in DBpedia by counting the number of labels per book. Each
Wikipedia language edition from which a resource was extracted by
DBpedia has its label stored using the
[rdfs:label](https://www.w3.org/TR/2004/REC-rdf-schema-20040210/#ch_label)
property. This is our query:

~~~ sql
SELECT ?s ?desc ?authorlabel (COUNT(DISTINCT ?label) as ?labelcount)
WHERE {
  ?s rdf:type dbo:Book .
  ?s rdfs:label ?label .
  ?s dbo:author ?author
  OPTIONAL {
    ?s rdfs:label ?desc FILTER (lang(?desc) = "en").
  }
  OPTIONAL {
    ?author rdfs:label ?authorlabel FILTER (lang(?authorlabel) = "en").
  }
} GROUP BY ?s ?desc ?authorlabel ORDER BY DESC(?labelcount)
~~~

Unfortunately, [the output][query-labels] is a bit disappointing:

| s                                      | desc                                       | authorlabel                     | labelcount |
|----------------------------------------|--------------------------------------------|---------------------------------|------------|
| [:The_Adventures_of_Tom_Sawyer](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Adventures_of_Tom_Sawyer)         | "The Adventures of Tom Sawyer"@en          | "Mark Twain"@en                 |         12 |
| [:Strange_Case_of_Dr_Jekyll_and_Mr_Hyde](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Strange_Case_of_Dr_Jekyll_and_Mr_Hyde)| "Strange Case of Dr Jekyll and Mr Hyde"@en | "Robert Louis Stevenson"@en     |         12 |
| [:Fifty_Shades_of_Grey](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Fifty_Shades_of_Grey)                 | "Fifty Shades of Grey"@en                  | "E. L. James"@en                |         12 |
| [:Gray's_Anatomy](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Gray's_Anatomy)                       | "Gray's Anatomy"@en                        | "Henry Gray"@en                 |         12 |
| [:Sense_and_Sensibility](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Sense_and_Sensibility)                | "Sense and Sensibility"@en                 | "Jane Austen"@en                |         12 |
| [:A_Brief_History_of_Time](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/A_Brief_History_of_Time)              | "A Brief History of Time"@en               | "Stephen Hawking"@en            |         12 |
| [:Mein_Kampf](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Mein_Kampf)                           | "Mein Kampf"@en                            | "Adolf Hitler"@en               |         12 |
| [:Crime_and_Punishment](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Crime_and_Punishment)                 | "Crime and Punishment"@en                  | "Fyodor Dostoyevsky"@en         |         12 |
| [:Catching_Fire](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Catching_Fire)                        | "Catching Fire"@en                         | "Suzanne Collins"@en            |         12 |
| [:David_Copperfield](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/David_Copperfield)                    | "David Copperfield"@en                     | "Charles Dickens"@en            |         12 |
| [:Mansfield_Park](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Mansfield_Park)                       | "Mansfield Park"@en                        | "Jane Austen"@en                |         12 |
| [:Les_Liaisons_dangereuses](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Les_Liaisons_dangereuses)             | "Les Liaisons dangereuses"@en              | "Pierre Choderlos de Laclos"@en |         12 |
| [:Murder_on_the_Orient_Express](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Murder_on_the_Orient_Express)         | "Murder on the Orient Express"@en          | "Agatha Christie"@en            |         12 |
| [:The_Sign_of_the_Four](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Sign_of_the_Four)                 | "The Sign of the Four"@en                  | "Arthur Conan Doyle"@en         |         12 |
| [:The_Republic_(Plato)][the-republic]                       | "The Republic (Plato)"@en                  | "Plato"@en                      |         12 |
| [:The_Communist_Manifesto](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Communist_Manifesto)              | "The Communist Manifesto"@en               | "Friedrich Engels"@en           |         12 |
| [:From_the_Earth_to_the_Moon](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/From_the_Earth_to_the_Moon)           | "From the Earth to the Moon"@en            | "Jules Verne"@en                |         12 |
| [:Buddenbrooks](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Buddenbrooks)                         | "Buddenbrooks"@en                          | "Thomas Mann"@en                |         12 |
| [:The_Brothers_Karamazov](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Brothers_Karamazov)               | "The Brothers Karamazov"@en                | "Fyodor Dostoyevsky"@en         |         12 |
| [:The_Trial](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Trial)                            | "The Trial"@en                             | "Franz Kafka"@en                |         12 |



Seems that books have been extracted from only 12 language editions
(ar, de, en, es, fr, it, ja, nl, pl, pt, ru, zh). Or, only these 12
languages feature a
[page template for books](https://en.wikipedia.org/wiki/Help:Template).
Or … well, let's stop speculating and have a look: DBpedia features a
page with
[statistics about the extracted data](http://wiki.dbpedia.org/services-resources/datasets/cross-language-overlap-statistics)
and we can see in the "Cross-Language Instance Overlap" table that
there are, for instance, 268 books appearing in 16 language editions.
However, not all datasets from all language versions are available at
the
[public SPARQL endpoint](http://wiki.dbpedia.org/OnlineAccess#1.1%20Public%20SPARQL%20Endpoint).
[This list](http://downloads.dbpedia.org/2015-04/core/) shows that
currently a "labels" dataset has been loaded for exactly the 12
language versions we mentioned above. For the same reason, other
properties like
[dbo:abstract](http://dbpedia.org/snorql/?property=http%3A//dbpedia.org/ontology/abstract)
or [owl:sameAs](http://www.w3.org/2002/07/owl#sameAs) that could be
linked to the number of language editions show the same behaviour. (For
an overview of potential properties take a look at the DBpedia entry
on
["The Adventures of Tom Sawyer"](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Adventures_of_Tom_Sawyer).)

When looking for alternatives we found the [PageRank dataset](http://people.aifb.kit.edu/ath/) by Andreas Thalhammer. Fortunately, it is deployed on the official DBpedia SPARQL endpoint and so, instead of counting the number of language editions, we can easily use the [PageRank](https://en.wikipedia.org/wiki/PageRank) of each page within the English Wikipedia as a measure of importance:

~~~ sql
PREFIX vrank:<http://purl.org/voc/vrank#>

SELECT ?s (SAMPLE(?desc) AS ?label) (GROUP_CONCAT(?authorlabel, ', ') AS ?author) (MAX(?v) AS ?rank)
FROM <http://dbpedia.org>
FROM <http://people.aifb.kit.edu/ath/#DBpedia_PageRank>
WHERE {
  ?s rdf:type dbo:Book .
  ?s vrank:hasRank/vrank:rankValue ?v .
  ?s dbo:author ?author
  OPTIONAL {
    ?s rdfs:label ?desc FILTER (lang(?desc) = "en").
  }
  OPTIONAL {
    ?author rdfs:label ?authorlabel FILTER (lang(?authorlabel) = "en").
  }
} GROUP BY ?s ORDER BY DESC(?rank)
~~~

We modified the query so it groups authors of multi-author books into one row. Despite some Wikipedia-related distortions, the result is much more meaningful:

| s                                 | label                                 | author                                                    |    rank |
|-----------------------------------|---------------------------------------|-----------------------------------------------------------|---------|
| [:The_World_Factbook](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_World_Factbook)              | "The World Factbook"@en               | "Central Intelligence Agency"                             | 146.277 |
| [:Systema_Naturae](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Systema_Naturae)                 | "Systema Naturae"@en                  | "Carl Linnaeus"                                           | 68.6522 |
| [:Natural_History_(Pliny)][natural-history]                | "Natural History (Pliny)"@en          | "Pliny the Elder"                                         | 64.9683 |
| [:On_the_Origin_of_Species](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/On_the_Origin_of_Species)        | "On the Origin of Species"@en         | "Charles Darwin"                                          | 56.7624 |
| [:The_Rolling_Stone_Album_Guide](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Rolling_Stone_Album_Guide)   | "The Rolling Stone Album Guide"@en    | "Anthony DeCurtis, Dave Marsh"                            | 47.9486 |
| [:Don_Quixote](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Don_Quixote)                     | "Don Quixote"@en                      | "Miguel de Cervantes"                                     | 45.3332 |
| [:All_Music_Guide_to_Jazz](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/All_Music_Guide_to_Jazz)         | "All Music Guide to Jazz"@en          | "Vladimir Bogdanov (editor), Stephen Thomas Erlewine"     |  44.641 |
| [:Alice's_Adventures_in_Wonderland](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Alice's_Adventures_in_Wonderland)| "Alice's Adventures in Wonderland"@en | "Lewis Carroll"                                           | 42.4669 |
| [:All_Music_Guide_to_the_Blues](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/All_Music_Guide_to_the_Blues)    | "All Music Guide to the Blues"@en     | "Vladimir Bogdanov, Stephen Thomas Erlewine"              | 40.9857 |
| [:Records_of_the_Grand_Historian](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Records_of_the_Grand_Historian)  | "Records of the Grand Historian"@en   | "Sima Qian"                                               |  40.262 |
| [:Nineteen_Eighty-Four](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Nineteen_Eighty-Four)            | "Nineteen Eighty-Four"@en             | "George Orwell"                                           | 39.9243 |
| [:The_Republic_(Plato)][the-republic]            | "The Republic (Plato)"@en             | "Plato"                                                   | 38.9124 |
| [:The_Wealth_of_Nations](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Wealth_of_Nations)           | "The Wealth of Nations"@en            | "Adam Smith"                                              | 37.4529 |
| [:Euclid's_Elements](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Euclid's_Elements)               | "Euclid's Elements"@en                | "Euclid"                                                  | 36.0581 |
| [:Paradise_Lost](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Paradise_Lost)                   | "Paradise Lost"@en                    | "John Milton"                                             | 32.8596 |
| [:Moby-Dick](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Moby-Dick)                       | "Moby-Dick"@en                        | "Herman Melville"                                         |  32.632 |
| [:Encyclopædia_Iranica](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Encyclopædia_Iranica)            | "Encyclopædia Iranica"@en             | "Ehsan Yarshater"                                         | 30.9694 |
| [:Dracula](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Dracula)                         | "Dracula"@en                          | "Bram Stoker"                                             | 29.6592 |
| [:Histories_(Herodotus)][histories]            | "Histories (Herodotus)"@en            | "Herodotus"                                               | 29.4831 |
| [:The_Hobbit](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Hobbit)                      | "The Hobbit"@en                       | "J. R. R. Tolkien"                                        | 29.4576 |

These are the top 20 books, ranked by their PageRank within the English Wikipedia. One thing still blocking the view a bit are the popular encyclopedic works, of course. The many, many in-links earned by [the "World Factbook"](https://en.wikipedia.org/w/index.php?title=Special:WhatLinksHere/The_World_Factbook&limit=500) or [the "Rolling Stone Album Guide"](https://en.wikipedia.org/w/index.php?title=Special:WhatLinksHere/The_Rolling_Stone_Album_Guide&limit=500) will not speak for their unrivalled literary quality, supposedly. Sorting out the literary works from this set of (all kinds of) books would be the obvious next step.




[query-book]: http://dbpedia.org/snorql/?query=SELECT+%3Fs+%3Fdesc+%3Fauthorlabel%0D%0AWHERE+{++%3Fs+rdf%3Atype+dbo%3ABook+.%0D%0A++%3Fs+dbo%3Aauthor+%3Fauthor%0D%0A++OPTIONAL+{++++%3Fs+rdfs%3Alabel+%3Fdesc+FILTER+%28lang%28%3Fdesc%29+%3D+%22en%22%29.%0D%0A++}%0D%0A++OPTIONAL+{++++%3Fauthor+rdfs%3Alabel+%3Fauthorlabel+FILTER+%28lang%28%3Fauthorlabel%29+%3D+%22en%22%29.%0D%0A++}%0D%0A}%0D%0A

[query-labels]: http://dbpedia.org/snorql/?query=SELECT+%3Fs+%3Fdesc+%3Fauthorlabel+%28COUNT%28DISTINCT+%3Flabel%29+as+%3Flabelcount%29%0D%0AWHERE+{++%3Fs+rdf%3Atype+dbo%3ABook+.%0D%0A++%3Fs+rdfs%3Alabel+%3Flabel+.%0D%0A++%3Fs+dbo%3Aauthor+%3Fauthor%0D%0A++OPTIONAL+{++++%3Fs+rdfs%3Alabel+%3Fdesc+FILTER+%28lang%28%3Fdesc%29+%3D+%22en%22%29.%0D%0A++}%0D%0A++OPTIONAL+{++++%3Fauthor+rdfs%3Alabel+%3Fauthorlabel+FILTER+%28lang%28%3Fauthorlabel%29+%3D+%22en%22%29.%0D%0A++}%0D%0A}+GROUP+BY+%3Fs+%3Fdesc+%3Fauthorlabel+ORDER+BY+DESC%28%3Flabelcount%29+LIMIT+20

[the-republic]: http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Republic_(Plato)
[natural-history]: http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Natural_History_(Pliny)
[histories]: http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/Histories_(Herodotus)
