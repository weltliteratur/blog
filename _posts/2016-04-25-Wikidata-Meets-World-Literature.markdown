---
title: Wikidata Meets World Literature
layout: post
author: [christopher, frank]
comments: true
date: 2016-04-25
---

You can currently access and contribute to [281 active Wikipedia language versions](https://meta.wikimedia.org/wiki/List_of_Wikipedias). What follows is a top-25 list of 'books' ranked by the number of Wikipedia language dedicated to these 'books' (results first, explanation thereafter):

| Wikidata item                                       | Title                                     | Authorlabel                | Linkcount | 
|-----------------------------------------------------|-------------------------------------------|----------------------------|-----------| 
| [Q8258](http://www.wikidata.org/entity/Q8258)       | One Thousand and One Nights               | anonymous                  | 116       | 
| [Q15228](http://www.wikidata.org/entity/Q15228)     | The Lord of the Rings                     | J. R. R. Tolkien           | 115       | 
| [Q480](http://www.wikidata.org/entity/Q480)         | Don Quixote                               | Miguel de Cervantes        | 113       | 
| [Q25338](http://www.wikidata.org/entity/Q25338)     | Le Petit Prince                           | Antoine de Saint-Exupéry   | 110       | 
| [Q40591](http://www.wikidata.org/entity/Q40591)     | The Communist Manifesto                   | Karl Marx/Friedrich Engels | 108       | 
| [Q459842](http://www.wikidata.org/entity/Q459842)   | Book of Mormon                            | Joseph Smith               | 106       | 
| [Q208460](http://www.wikidata.org/entity/Q208460)   | Nineteen Eighty-Four                      | George Orwell              | 102       | 
| [Q8251](http://www.wikidata.org/entity/Q8251)       | The Art of War                            | Sun Tzu                    | 95        | 
| [Q92640](http://www.wikidata.org/entity/Q92640)     | Alice's Adventures in Wonderland          | Lewis Carroll              | 93        | 
| [Q8279](http://www.wikidata.org/entity/Q8279)       | Shahnameh                                 | Ferdowsi                   | 93        | 
| [Q74287](http://www.wikidata.org/entity/Q74287)     | The Hobbit                                | J. R. R. Tolkien           | 91        | 
| [Q43361](http://www.wikidata.org/entity/Q43361)     | Harry Potter and the Philosopher's Stone  | J. K. Rowling              | 86        | 
| [Q1396889](http://www.wikidata.org/entity/Q1396889) | Animal Farm                               | George Orwell              | 85        | 
| [Q8265](http://www.wikidata.org/entity/Q8265)       | Dream of the Red Chamber                  | Cao Xueqin                 | 82        | 
| [Q41675](http://www.wikidata.org/entity/Q41675)     | Guinness World Records                    | Craig Glenday              | 80        | 
| [Q48244](http://www.wikidata.org/entity/Q48244)     | Mein Kampf                                | Adolf Hitler               | 80        | 
| [Q8269](http://www.wikidata.org/entity/Q8269)       | The Tale of Genji                         | Murasaki Shikibu           | 79        | 
| [Q165318](http://www.wikidata.org/entity/Q165318)   | Crime and Punishment                      | Fyodor Dostoyevsky         | 77        | 
| [Q47209](http://www.wikidata.org/entity/Q47209)     | Harry Potter and the Chamber of Secrets   | J. K. Rowling              | 77        | 
| [Q47598](http://www.wikidata.org/entity/Q47598)     | Harry Potter and the Prisoner of Azkaban  | J. K. Rowling              | 75        | 
| [Q46887](http://www.wikidata.org/entity/Q46887)     | Harry Potter and the Half-Blood Prince    | J. K. Rowling              | 75        | 
| [Q80817](http://www.wikidata.org/entity/Q80817)     | Harry Potter and the Order of the Phoenix | J. K. Rowling              | 75        | 
| [Q123397](http://www.wikidata.org/entity/Q123397)   | The Republic                              | Plato                      | 74        | 
| [Q170583](http://www.wikidata.org/entity/Q170583)   | Pride and Prejudice                       | Jane Austen                | 74        | 
| [Q147787](http://www.wikidata.org/entity/Q147787)   | Anna Karenina                             | Leo Tolstoy                | 73        | 

Sports commentator proclaims: Legendary Arabian story collection first, the Lord of the Rings a close runner-up, Spanish hack Cervantes completing the podium! But let's curb our enthusiasm for this quirky race for a moment. You cannot be cautious enough when interpreting this kind of lists/rankings. There are a hundred things you'd have to involve when doing this.

Our ranking reveals nothing on the nature or quality of, let's say, these 110 language versions of "Le Petit Prince". We could deal with a one-sentence article in 50 Wikipedias for all we know. Understanding the genesis of Wikipedia and measuring its contents is a research field of its own. And Wikidata, although building on Wikipedia content, of course, is yet another thing whose characteristics you'd have to take into account before jumping to any rash conclusions.

Let's start slowly. What this ranking suggests to show is a list of 25 'books' (we'll come back to this term later) that are of whatsoever importance across many countries/cultures/language communities. It is not at all a proper basis to redefine the term 'world literature' for the digital age. But it does include the idea of 'world' as part of 'world literature', meaning 'books' that transcend national and language borders, also if their literary value may vary considerably. In any case, before starting to interpret anything, you'll always have to communicate how exactly you generated this kind of results. So …

… as an example of how the Wikidata Query Service can facilitate this type of quantitative analysis, we wrote a SPARQL query that orders 'instances of' 'books' with an author by 'site link'. This means that if a work of literature has the statement 'instance of book' in Wikidata, and it has a Wikpedia page, it can be ranked by the number of Wikipedias that have a page for it.

This is easily reproducible for you at your own machines, just head over to [http://query.wikidata.org](http://query.wikidata.org) and copy & paste this in the upper box, then hit "Execute" (and while the query is being processed, throw a glance at Alan Liu's [criticism of the concentration "on pushing the 'execute' button" in the Digital Humanities](http://dhdebates.gc.cuny.edu/debates/text/20)):

~~~ sql
prefix schema: <http://schema.org/>
prefix wd: <http://www.wikidata.org/entity/>
prefix wdt: <http://www.wikidata.org/prop/direct/>

SELECT ?s ?desc ?authorlabel (COUNT(DISTINCT ?sitelink) as ?linkcount)
WHERE {
  ?s wdt:P31 wd:Q571 .
  ?sitelink schema:about ?s .
  ?s wdt:P50 ?author
  OPTIONAL {
    ?s rdfs:label ?desc filter (lang(?desc) = "en").
  }
  OPTIONAL {
    ?author rdfs:label ?authorlabel filter (lang(?authorlabel) = "en").
  }
} GROUP BY ?s ?desc ?authorlabel ORDER BY DESC(?linkcount)
~~~

Did it work for you?

By the way, changing the object criteria from 'book to 'literary work' (wd:Q7725634) returns a different result, that includes books of the Bible (that are not classified as 'instance of book'). Running it without the author, also yields a slightly different result, as there are a few works without an author that are very widely translated (like, for example, today's winner, "One Thousand and One Nights").

The query that yielded the above ranking was run today (April 25, 2016) at 08:25 CEST. If you save the results of your query (which can be done directly in Wikidata's Query Service) and compare it to the same query conducted at a later date, you would have a useful rudiment for the analysis of how certain works gain or lose importance in the Wikipedian universe. Something we might come back to later.

