---
title: Contributors to World Literature – Identifying Writers in Wikipedia, Part II
layout: post
author: [robert, frank]
comments: true
date: 2016-08-19
---

In
[the first post](/Contributors-to-World-Literature-Identifying-Writers-in-Wikipedia-Part-I/)
of this 2-part series we introduced six features of Wikipedia pages on
writers that might help us figure out if those pages are, in fact,
about (literary) writers. Today we want to discuss which of these
features are actually suited to reliably identify writers in
Wikipedia. Our goal here is to build a set of contributors to world
literature that we can further investigate (and keep updated, as
Wikipedia evolves). Instead of providing a conclusive answer here,
this post will concentrate on observations that could eventually help
to implement an approach for the automated identification of literary
writers in Wikipedia.

## First Sentence

![The first sentence on the Wikipedia Page of John Irving](/images/wp_john_irving_first_sentence.png)

- This feature is available throughout all language versions.
- The automated analysis of sentences requires some sophisticated
  natural language processing which should also be available for
  different languages. The quality of such approaches highly
  depends on the chosen language.
- The results are quite ambiguous, since even within one language
  version there is no standardised way to describe writers.
- DBpedia has implemented a
  [framework for fact extraction](https://github.com/dbpedia/fact-extractor)
  which could potentially extract this information.
<!-- DBpedia provides datasets that classify persons based on data
  extracted from the running text of the article. **point to this
  dataset and briefly explain it** -->

## Table of Contents

![The table of contents on the Wikipedia page of John Irving](/images/wp_john_irving_toc.png)

- At first sight, a "Bibliography" section seems to be the prevalent
  way to list original works of an author in the English Wikipedia.
  But not all writers have one. Also, the name of the section is
  not consistent (e.g., "Works", as can be seen in the article on
  [John Milton](https://en.wikipedia.org/wiki/John_Milton#Works)).
  "Bibliography" can also refer to a list of secondary literature
  (see the article on
  [Gabriel García Márquez](https://en.wikipedia.org/wiki/Gabriel_García_Márquez#Bibliography)).
- Albeit its ambiguity, finding the "Bibliography" headline in the
  wiki source code is easy. Finding equivalent headings in other
  language versions would require some effort, though.
- It is unclear if and how this feature is used in other language
  versions.
- The section structure of articles is currently not provided by
  DBpedia.

## Occupation Property

![The infobox on the Wikipedia page of John Irving](/images/wp_john_irving_infobox.png)

- This property often contains several (ambiguous) values without
  further distinctions ("writer", "novelist", "poet", etc.).
- Values of this property are highly language-dependent, it is rather
  difficult to make use of it in a cross-language environment.
- Not all language editions permit infoboxes for writers (among
  others, the German edition).
- If available, the infobox properties are extracted by DBpedia. They
  can be found in the [infobox properties dataset][dbpedia-infobox]
  and in the
  [mapping-based properties dataset][dbpedia-mapping]. The
  [latest dataset](http://wiki.dbpedia.org/Downloads2015-10) contains
  this information only in the infobox properties dataset:

  ````xml
<http://dbpedia.org/resource/John_Irving> <http://dbpedia.org/property/occupation> "Novelist"@en .
<http://dbpedia.org/resource/John_Irving> <http://dbpedia.org/property/occupation> "Screenwriter"@en .
  ````


## List of Works

![The "John Irving" template on the Wikipedia page of John Irving](/images/wp_john_irving_template_john_irving.png)

- In our example page on
  [John Irving](https://en.wikipedia.org/wiki/John_Irving), this
  feature was implemented using a specific
  [John Irving template](https://en.wikipedia.org/wiki/Template:John_Irving).
  Other popular/canonised writers also have that kind of template, yet in
  general, this feature is not very widespread. There are categories for
  such templates, like
  ["Category:Novelist navigational boxes"](https://en.wikipedia.org/wiki/Category:Novelist_navigational_boxes).

## Categories

![The categories of the Wikipedia page of John Irving](/images/wp_john_irving_categories.png)

- The category graph is quite inconsistent. In particular, it is not a
  tree. (cf. O. Medelyan, D. Milne, C. Legg, I. H. Witten (2009),
  [Mining Meaning from Wikipedia](http://dx.doi.org/10.1016/j.ijhcs.2009.05.004))
- As we have seen, there are many categories that could be used to
  identify a person as a writer, but they do not cover all
  writers. Categories higher up the hierarchy **(e.g., )** would cover
  more writers but due to some dubious subcategories **(e.g., )** also
  cover pages that are definitely not about writers.
- For instance, starting the traversal at the
  [Writers by Century](https://en.wikipedia.org/wiki/Category:Writers_by_century)
  category in the English version, the set would contain persons like
  [Winston Churchill]() and [Leonardo da Vinci](), while omitting
  writers like [Gertrude Stein]() and [Heinrich Heine]().
- Each language version has its own category structure. Thus, the
  effort of identifying corresponding categories and removing false
  positives would need to be repeated for each language.
- Articles are usually assigned to several categories which would enable
  identification of writers which also had other occupations.
- DBpedia provides the [article_categories]() dataset which contains
  the assignment of categories to articles and the [skos_categories]()
  dataset which contains the category graph.

## Writer Template

![The source code of the "writer" template of the Wikipedia page of John Irving](/images/wp_john_irving_template_writer.png)

- Not all language editions have or use a writer template. E.g., the
  German Wikipedia does not use the 'writer' template and, thus, its page
  on
  [Johann Wolfgang von Goethe](https://de.wikipedia.org/wiki/Johann_Wolfgang_von_Goethe)
  lacks an infobox.
- Each page can be assigned to exactly one template, which means that
  some persons do not have a writer template, although we'd clearly
  like to have them in our set. This includes
  [Franz Kafka](https://en.wikipedia.org/wiki/Franz_Kafka) (neutral
  person template) and
  [Umberto Eco](https://en.wikipedia.org/wiki/Umberto_Eco) (tied to
  a [philosopher template]()).
- The association of Wikipedia pages to templates has been extracted
  by DBpedia which also includes a mapping between corresponding
  templates of different language versions. For the English Wikipedia,
  the mapping for the articles can be found in the
  [instance_types_en]() dataset.

| feature             | languages | usage    | effort |
|---------------------+-----------+----------+--------|
| first sentence      | all       | complete | high   |
| table of contents   | all       | some     | low    |
| list of works       | few       | few      |        |
| occupation property | some      | many     |        |
| categories          | all       | many     | high   |
| writer template     | some      | many     | low    |

Given the large variety of properties the different features have, it
is quite difficult to devise an approach to identify writers on
Wikipedia that works across different language versions. In one of our
next blog posts we show



[dbpedia-infobox]: http://wiki.dbpedia.org/services-resources/documentation/datasets#infoboxproperties
[dbpedia-mapping]: http://wiki.dbpedia.org/services-resources/documentation/datasets#mappingbasedliterals
