---
title: Identifying authors in Wikipedia 2
layout: post
author: [robert, frank]
comments: true
date: 2016-07-22
---

Instead of providing a conclusive answer as to which approach is best,
we would like to point out some observations which could aid the
selection of an approach.

## First Sentence

- The automatic processing of the sentences requires sophisticated
  natural language processing which would also need to be available
  for different languages. The quality of such approaches highly
  depends on the chosen language.
- The results are quite ambigue, since even within one language
  version there is no standardized way to describe writers.
- **TODO**: "The DBpedia community already dealt with this problem by
  providing specific datasets containing data extracted from the
  running text of the article to classify persons." -- point to this
  dataset and briefly explain it.

## Table of Contents
- Not all pages of writers have a bibliography. In particular, less
  popular writers or writers which have written only few works lack a
  bibliography. **examples**

## Occupation Property

- language-dependent
- ambigue: "writer", "novelist", "poet" -- decide which terms to consider
- works only for languages which have an infobox (missing German,
      etc.)
- often lists several occupations
- DBpedia: [infobox_properties]()

# Categories

- The category graph is quite inconsistent, in particular it is not a
  tree. (cf. O. Medelyan, D. Milne, C. Legg, I.H. Witten. (2009)
  Mining Meaning from Wikipedia. International Journal of
  Human-Computer Studies 67(9):716–754.)
- As we have seen, there are many categories which could be used to
  identify Irving as a writer, yet, they do not cover all
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
  clearly writers. This includes [Franz Kafka]() (who has a
  [philosopher template]()) and [Geoffrey Chaucer]() (who as a
  [template]()).
- The association of Wikipedia pages to templates has been extracted
  by DBpedia which also includes a mapping between corresponding
  templates of different language versions. For the English Wikipedia,
  the mapping for the articles can be found in the
  [instance_types_en]() dataset.
  

(show counter examples, e.g., Kafka and Eco or Tom Cruise & Co.)
- How easy is it to use this information? (Categories: difficult,
  because ... occupation: difficult, because, etc.)

- categories
- inconsistent
- refer to paper which judges the quality of the WP category graph
- template: typically an infobox; one hint: no writer template in the
  German Wikipedia!
- content of infoboxes: occupation; sometimes as person data
- here:just priniciple idea and some examples, more detailed eval in a
  later blog post


BTW: https://en.wikipedia.org/wiki/Umberto_Eco is also a philosopher 

