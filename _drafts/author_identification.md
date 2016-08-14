---
title: Identifying authors in Wikipedia
layout: post
author: [robert, frank]
comments: true
date: 2016-08-16
---

The first challenge we face when trying to analyse the
representation of world literature on Wikipedia is the automatic
identification of writers and works across its 280+ language
versions. Since our last posts have shown how to extract works
that are possible candidates for a world-literary canon,
we here focus on writers, i.e., possible contributors to world
literature.

For a start, let us have a detailed look at a the
[Wikipedia page of John Irving](https://en.wikipedia.org/wiki/John_Irving):

![Wikipedia Page of John Irving](/images/wp_john_irving_all.png)

We can identify the following features on the web page which indicate
that John Irving is a writer:

1. The **first sentence** says that John Irving is a novelist:

   ![The first sentence on the Wikipedia Page of John Irving](/images/wp_john_irving_first_sentence.png)
2. The **table of contents** lists a bibliography:
   
   ![The table of contents on the Wikipedia page of John Irving](/images/wp_john_irving_toc.png)
3. The infobox on the right lists as **occupation property** the
   values "Novelist, Screenwriter":

   ![The infobox on the Wikipedia page of John Irving](/images/wp_john_irving_infobox.png)
4. Scrolling down, the
   [template for John Irving](https://en.wikipedia.org/wiki/Template:John_Irving)
   shows **works** by John Irving:

   ![The "John Irving" template on the Wikipedia page of John Irving](/images/wp_john_irving_template_john_irving.png)
5. Scrolling further down, we find a list of **categories**, among
   them
   [20th-century American novelists](https://en.wikipedia.org/wiki/Category:20th-century_American_novelists),
   [21st-century American novelists](https://en.wikipedia.org/wiki/Category:21st-century_American_novelists),
   [American feminist writers](https://en.wikipedia.org/wiki/Category:American_feminist_writers),
   and
   [American male screenwriters](https://en.wikipedia.org/wiki/Category:American_male_screenwriters):

   ![The categories of the Wikipedia page of John Irving](/images/wp_john_irving_categories.png)
6. In addition, by looking at
   [the wiki source code of the page ][source-code] we can see that
   the infobox uses the **writer template**:

   ![The source code of the "writer" template of the Wikipedia page of John Irving](/images/wp_john_irving_template_writer.png)

To use one of these features to automatically identify John Irving as
a writer, we first have to answer the following questions:

1. Which of the information is universally available (i.e., in
   different language versions)?
2. Which of the information is available in DBpedia or Wikidata?
3. How widespread is the information used?
4. How easy is it to actually use the information to identify writers?

In our next blog post we will address these questions.



[source-code]: https://en.wikipedia.org/w/index.php?title=John_Irving&action=edit&editintro=Template:BLP_editintro
