---
title: Contributors to World Literature – Identifying Writers in Wikipedia, Part I
layout: post
author: [robert, frank]
comments: true
date: 2016-08-18
---

The first challenge we face when trying to analyse the representation
of world literature on Wikipedia is the automatic identification of
literary writers and works across all 280+ language versions. Our last
posts have shown how to extract **works** that are possible candidates
for a Wikipedia-inherent world-literary canon
([Wikidata-based](/Wikidata-Meets-World-Literature/) and
[DBpedia-based](/DBpedia-and-World-Literature/)). In this 2-part post
we focus on the extraction of **writers**, i.e., possible contributors
to world literature.

For a start, let us have a detailed look at the
[Wikipedia page of John Irving](https://en.wikipedia.org/wiki/John_Irving):

![Wikipedia Page of John Irving](/images/wp_john_irving_all.png)

This web page has several features indicating that John Irving is a
writer we want to have in our set. Let's introduce and discuss six of
them:

1. The **first sentence** says that John Irving is a novelist and
   screenwriter:

   ![The first sentence on the Wikipedia Page of John Irving](/images/wp_john_irving_first_sentence.png)
2. The **table of contents** lists a bibliography:
   
   ![The table of contents on the Wikipedia page of John Irving](/images/wp_john_irving_toc.png)
3. The infobox on the right has an **occupation property** with
   values "Novelist" and "Screenwriter":

   ![The infobox on the Wikipedia page of John Irving](/images/wp_john_irving_infobox.png)
4. Scrolling down, the
   [John Irving template](https://en.wikipedia.org/wiki/Template:John_Irving)
   assembles a **list of works** by the author:

   ![The "John Irving" template on the Wikipedia page of John Irving](/images/wp_john_irving_template_john_irving.png)
5. Scrolling down further, we find a list of **categories**, among
   them
   [20th-century American novelists](https://en.wikipedia.org/wiki/Category:20th-century_American_novelists),
   [21st-century American novelists](https://en.wikipedia.org/wiki/Category:21st-century_American_novelists),
   [American feminist writers](https://en.wikipedia.org/wiki/Category:American_feminist_writers),
   and
   [American male screenwriters](https://en.wikipedia.org/wiki/Category:American_male_screenwriters):

   ![The categories of the Wikipedia page of John Irving](/images/wp_john_irving_categories.png)
6. In addition, by looking at
   [the wiki source code of the page][source-code] we realise that
   the infobox uses the **writer template**:

   ![The source code of the "writer" template of the Wikipedia page of John Irving](/images/wp_john_irving_template_writer.png)

To leverage one of these features to automatically identify John
Irving (and others, of course) as a writer, we have to answer these
questions:

1. Which of the information is universally available (i.e., in
   different language versions)?
2. Which of the information is available through DBpedia or Wikidata?
3. How widespread is the information used?
4. How easy is it to actually use the information to identify writers?

We will discuss these questions tomorrow in the 2nd part of this blog post.


[source-code]: https://en.wikipedia.org/w/index.php?title=John_Irving&action=edit&editintro=Template:BLP_editintro
