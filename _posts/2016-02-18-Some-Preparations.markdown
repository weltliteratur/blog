---
title: Some Preparations
layout: post
author: [Christopher, Frank]
comments: true
date: 2016-02-18
---

This is our test query, go to [http://query.wikidata.org](http://query.wikidata.org) and paste this in the box:

~~~ sparql
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

Changing the object criteria from "book" to "literary work" (wd:Q7725634) returns a different result (to be continued) …


