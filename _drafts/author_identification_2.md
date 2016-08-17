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
writers that might help us figure out if those pages are, in fact, about
(literary) writers. Today we want to discuss which of these
features are actually suited to reliably identify writers in
Wikipedia. Our goal here is to build a set of contributors to world
literature that we can further investigate (and keep updated, as
Wikipedia evolves). Instead of providing a conclusive answer here,
this post will concentrate on observations that could eventually help
to implement an approach for the automated identification of literary
writers in Wikipedia.

## First Sentence
- This feature is available throughout all language versions.
- The automatic processing of the sentences requires sophisticated
  natural language processing which would also need to be available
  for different languages. The quality of such approaches highly
  depends on the chosen language.
- The results are quite ambiguous, since even within one language
  version there is no standardized way to describe writers.
- DBpedia provides datasets which classify persons based on data
  extracted from the running text of the article. **point to this
  dataset and briefly explain it**

## Table of Contents
- Not all pages of writers have a bibliography. In particular, less
  popular writers or writers which have written only few works lack a
  bibliography. For instance, [the page of in the English Wikipedia]()
  lacks a bibliography. **add link**
- Extraction of this feature is straightforward for the English
  Wikipedia, since finding the bibliography headline in the wiki
  source code is easy. Finding equivalent headings in other language
  versions requires some effort but should still be easy.
- It is not clear, how much this feature is used in other language
  versions.

## List of Works
- In our example page of
  [John Irving](https://en.wikipedia.org/wiki/John_Irving), this
  feature was implemented by
  [template specific to John Irving](https://en.wikipedia.org/wiki/Template:John_Irving).
  There exist other writers who also have such a template but in
  general, this feature is not very widespread. **provide example** -
  maybe there's a category for such templates?

## Occupation Property
- This property often contains many values, which means one has to
  decide whether all values or only the first one is regarded.
- The values in this property are highly language-dependent, therefore
  it is rather difficult to use in a cross-language setting.
- Even within one language, the values are ambigue: "writer",
  "novelist", "poet" -- one has to decide which terms to consider.
- Since the values are contained in the infoboxes, this works only for
  language editions which have an infobox (which excludes, among
  others, the German edition, since it lacks an infobox for
  writers). **provide link/evidence**
- DBpedia has extracted those properties, they are available in the
  [infobox_properties dataset](). **do they include a language
  mapping?**

# Categories
- The category graph is quite inconsistent, in particular it is not a
  tree. (cf. O. Medelyan, D. Milne, C. Legg, I.H. Witten. (2009)
  [Mining Meaning from Wikipedia](http://dx.doi.org/10.1016/j.ijhcs.2009.05.004))
- As we have seen, there are many categories which could be used to
  identify a person as a writer, yet, they do not cover all
  writers. Categories higher up the hierarchy **(e.g., )** would cover
  more writers but due to some dubious subcategories **(e.g., )** also
  cover pages which definitely are not writers.
- For instance, starting the traversal at the [Writers by Century]()
  category in the English version, the set would contain persons like
  [Winston Churchill]() and [Leonardo da Vinci](), while omitting
  writers like [Gertrude Stein]() and [Heinrich Heine]().
- Each language version has its own category structure, thus the
  effort of identifying appropriate categories and removing false
  positives would need to be repeated.
- An article can be assigned to several categories which would enable
  identification of writers which also had other occupations.
- DBpedia provides the [article_categories]() dataset which contains
  the assignment of categories to articles and the [skos_categories]()
  dataset which contains the category graph.

# Writer Template
- Not all language editions have or use a writer template. E.g., the
  German Wikipedia does not use the writer template and thus its page
  of
  [Johann Wolfgang von Goethe](https://de.wikipedia.org/wiki/Johann_Wolfgang_von_Goethe)
  lacks an infobox.
- Each page can be assigned to exactly one template, which means that
  some persons do not have a writer template, although they are
  clearly writers. This includes
  [Franz Kafka](https://en.wikipedia.org/wiki/Franz_Kafka) and
  [Umberto Eco](https://en.wikipedia.org/wiki/Umberto_Eco) (who both
  have a [philosopher template]()) and
  [Geoffrey Chaucer](https://en.wikipedia.org/wiki/Geoffrey_Chaucer)
  (who has a [template]()).
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
