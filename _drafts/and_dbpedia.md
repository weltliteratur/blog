---
title: ... and DBpedia?
layout: post
author: [robert, frank]
comments: true
date: 2016-05-16
---

After our
[first blog post on Wikidata](Wikidata-Meets-World-Literature) some
enthusiasts might have asked "... and DBpedia?" Here we try to deliver
an answer.

Let us start with a simplified translation of the original SPARQL
query to match the DBpedia ontology:

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

This query
[returns](http://dbpedia.org/snorql/?query=SELECT+%3Fs+%3Fdesc+%3Fauthorlabel%0D%0AWHERE+{%0D%0A++%3Fs+rdf%3Atype+dbo%3ABook+.%0D%0A++%3Fs+dbo%3Aauthor+%3Fauthor%0D%0A++OPTIONAL+{%0D%0A++++%3Fs+rdfs%3Alabel+%3Fdesc+FILTER+%28lang%28%3Fdesc%29+%3D+%22en%22%29.%0D%0A++}%0D%0A++OPTIONAL+{%0D%0A++++%3Fauthor+rdfs%3Alabel+%3Fauthorlabel+FILTER+%28lang%28%3Fauthorlabel%29+%3D+%22en%22%29.%0D%0A++}%0D%0A}%0D%0A)
a list of resources which have been assigned the class
[Book](http://mappings.dbpedia.org/server/ontology/classes/Book) in
the DBpedia ontology together with their authors.

To rank those books, we used the number of Wikipdia language editions
in which those books appear. We can try something similar in DBpedia
by counting the number of labels a book has, since for each language
edition in Wikipedia where a resource was extracted by DBpedia its
label is stored using the
[rdfs:label](https://www.w3.org/TR/2004/REC-rdf-schema-20040210/#ch_label)
property:

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

Unfortunately, [the result](http://dbpedia.org/snorql/?query=SELECT+%3Fs+%3Fdesc+%3Fauthorlabel+%28COUNT%28DISTINCT+%3Flabel%29+as+%3Flabelcount%29%0D%0AWHERE+{%0D%0A++%3Fs+rdf%3Atype+dbo%3ABook+.%0D%0A++%3Fs+rdfs%3Alabel+%3Flabel+.%0D%0A++%3Fs+dbo%3Aauthor+%3Fauthor%0D%0A++OPTIONAL+{%0D%0A++++%3Fs+rdfs%3Alabel+%3Fdesc+FILTER+%28lang%28%3Fdesc%29+%3D+%22en%22%29.%0D%0A++}%0D%0A++OPTIONAL+{%0D%0A++++%3Fauthor+rdfs%3Alabel+%3Fauthorlabel+FILTER+%28lang%28%3Fauthorlabel%29+%3D+%22en%22%29.%0D%0A++}%0D%0A}+GROUP+BY+%3Fs+%3Fdesc+%3Fauthorlabel+ORDER+BY+DESC%28%3Flabelcount%29+LIMIT+20) is quite disappionting:

| s                                      | desc                                       | authorlabel                     | labelcount |
|----------------------------------------|--------------------------------------------|---------------------------------|------------|
| :The_Adventures_of_Tom_Sawyer          | "The Adventures of Tom Sawyer"@en          | "Mark Twain"@en                 |         12 |
| :Strange_Case_of_Dr_Jekyll_and_Mr_Hyde | "Strange Case of Dr Jekyll and Mr Hyde"@en | "Robert Louis Stevenson"@en     |         12 |
| :Fifty_Shades_of_Grey                  | "Fifty Shades of Grey"@en                  | "E. L. James"@en                |         12 |
| :Gray's_Anatomy                        | "Gray's Anatomy"@en                        | "Henry Gray"@en                 |         12 |
| :Sense_and_Sensibility                 | "Sense and Sensibility"@en                 | "Jane Austen"@en                |         12 |
| :A_Brief_History_of_Time               | "A Brief History of Time"@en               | "Stephen Hawking"@en            |         12 |
| :Mein_Kampf                            | "Mein Kampf"@en                            | "Adolf Hitler"@en               |         12 |
| :Crime_and_Punishment                  | "Crime and Punishment"@en                  | "Fyodor Dostoyevsky"@en         |         12 |
| :Catching_Fire                         | "Catching Fire"@en                         | "Suzanne Collins"@en            |         12 |
| :David_Copperfield                     | "David Copperfield"@en                     | "Charles Dickens"@en            |         12 |
| :Mansfield_Park                        | "Mansfield Park"@en                        | "Jane Austen"@en                |         12 |
| :Les_Liaisons_dangereuses              | "Les Liaisons dangereuses"@en              | "Pierre Choderlos de Laclos"@en |         12 |
| :Murder_on_the_Orient_Express          | "Murder on the Orient Express"@en          | "Agatha Christie"@en            |         12 |
| :The_Sign_of_the_Four                  | "The Sign of the Four"@en                  | "Arthur Conan Doyle"@en         |         12 |
| :The_Republic_(Plato)                  | "The Republic (Plato)"@en                  | "Plato"@en                      |         12 |
| :The_Communist_Manifesto               | "The Communist Manifesto"@en               | "Friedrich Engels"@en           |         12 |
| :From_the_Earth_to_the_Moon            | "From the Earth to the Moon"@en            | "Jules Verne"@en                |         12 |
| :Buddenbrooks                          | "Buddenbrooks"@en                          | "Thomas Mann"@en                |         12 |
| :The_Brothers_Karamazov                | "The Brothers Karamazov"@en                | "Fyodor Dostoyevsky"@en         |         12 |
| :The_Trial                             | "The Trial"@en                             | "Franz Kafka"@en                |         12 |

It seems that books have been extracted for only 12 language editions
... or only in those 12 languages there exists a
[page template](https://en.wikipedia.org/wiki/Help:Template) for
books. Other properties like
[dbo:abstract](http://dbpedia.org/snorql/?property=http%3A//dbpedia.org/ontology/abstract)
or [owl:sameAs](http://www.w3.org/2002/07/owl#sameAs) that could be
linked to the number of language editions showed the same
behavior. (For an overview on potential properties, have a look at all
the properties of
[The Adventues of Tom Sawyer](http://dbpedia.org/snorql/?describe=http%3A//dbpedia.org/resource/The_Adventures_of_Tom_Sawyer).)


Upon looking for alternatives, we found the
[PageRank dataset](http://people.aifb.kit.edu/ath/) by Andreas
Thalhammer which is loaded into the DBpedia SPARQL endpoint. Instead
of counting the number of language editions, we now use the
[PageRank](https://en.wikipedia.org/wiki/PageRank) of each page within
the English Wikipedia as a measure of importance:

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

The result is much closer to what we would expect:


| s                                 | label                                 | author                                                    |    rank |
|-----------------------------------|---------------------------------------|-----------------------------------------------------------|---------|
| :The_World_Factbook               | "The World Factbook"@en               | "Central Intelligence Agency"                             | 146.277 |
| :Systema_Naturae                  | "Systema Naturae"@en                  | "Carl Linnaeus"                                           | 68.6522 |
| :Natural_History_(Pliny)          | "Natural History (Pliny)"@en          | "Pliny the Elder"                                         | 64.9683 |
| :On_the_Origin_of_Species         | "On the Origin of Species"@en         | "Charles Darwin"                                          | 56.7624 |
| :The_Rolling_Stone_Album_Guide    | "The Rolling Stone Album Guide"@en    | "Anthony DeCurtis, Dave Marsh"                            | 47.9486 |
| :Don_Quixote                      | "Don Quixote"@en                      | "Miguel de Cervantes"                                     | 45.3332 |
| :All_Music_Guide_to_Jazz          | "All Music Guide to Jazz"@en          | "Vladimir Bogdanov (editor), Stephen Thomas Erlewine"     |  44.641 |
| :Alice's_Adventures_in_Wonderland | "Alice's Adventures in Wonderland"@en | "Lewis Carroll"                                           | 42.4669 |
| :All_Music_Guide_to_the_Blues     | "All Music Guide to the Blues"@en     | "Vladimir Bogdanov, Stephen Thomas Erlewine"              | 40.9857 |
| :Records_of_the_Grand_Historian   | "Records of the Grand Historian"@en   | "Sima Qian"                                               |  40.262 |
| :Nineteen_Eighty-Four             | "Nineteen Eighty-Four"@en             | "George Orwell"                                           | 39.9243 |
| :The_Republic_(Plato)             | "The Republic (Plato)"@en             | "Plato"                                                   | 38.9124 |
| :The_Wealth_of_Nations            | "The Wealth of Nations"@en            | "Adam Smith"                                              | 37.4529 |
| :Euclid's_Elements                | "Euclid's Elements"@en                | "Euclid"                                                  | 36.0581 |
| :Paradise_Lost                    | "Paradise Lost"@en                    | "John Milton"                                             | 32.8596 |
| :Moby-Dick                        | "Moby-Dick"@en                        | "Herman Melville"                                         |  32.632 |
| :Encyclopædia_Iranica             | "Encyclopædia Iranica"@en             | "Ehsan Yarshater"                                         | 30.9694 |
| :Dracula                          | "Dracula"@en                          | "Bram Stoker"                                             | 29.6592 |
| :Histories_(Herodotus)            | "Histories (Herodotus)"@en            | "Herodotus"                                               | 29.4831 |
| :The_Hobbit                       | "The Hobbit"@en                       | "J. R. R. Tolkien"                                        | 29.4576 |

