---
title: Identifying authors in Wikipedia
layout: post
author: [robert, frank]
comments: true
date: 2016-07-22
---

The first challenge one faces who wants to analyze the representation
of world literature on Wikipedia is: how to identify writers and
works? Since our last posts have shown examples how to extract written
works, we here focus on writers.

Therefore, let us have a detailed look at a the
[Wikipedia page of John Irving](https://en.wikipedia.org/wiki/John_Irving):

(here screenshot)

We can identify the following features on the web page which could
tell us that John Irving is a writer: (for each a screenshot)

1. The /first sentence/ says "John Winslow Irving [...] is an American
   novelist and Academy Award-winning screenwriter."
2. The /table of contents/ lists a bibliography.
3. The infobox on the right lists as /occupation property/ the values
   "Novelist, Screenwriter".
4. Scrolling down, we find a list of /categories/, among them
   [20th-century American novelists](), [21st-century American
   novelists](), [American feminist writers](), and [American male
   screenwriters]().
5. In addition, by looking at
   [the wiki source code of the page ][source-code] we can see that
   the infobox uses the /writer template/:

        {\{Infobox writer <!--for more information, see [[:Template:Infobox writer/doc]]-->
        | name = John Irving  |
        | | image = John Irving at Cologne 2010 (7108).jpg

For each of this indications we now have to ask ourselves the
following questions:

1. Which of this information is universally available (i.e., in
   different language versions)?
2. Which of this information is available in DBpedia or Wikidata?
3. How widespread is the information used?
4. How easy is it to actually use the information to identify writers?

Instead of providing a conclusive answer as to which approach is best,
we would like to point out some observations which could aid the
selection of an approach:

- first sentence ::
    - The automatic processing of these sentences requires
      sophisticated natural language processing which would also need
      to be available for different languages. The quality of such
      approaches highly depends on the chosen language.
	- 
- table of contents ::
- occupation property ::
- categories ::
    - The category graph is quite inconsistent, in particular it is
      not a tree.
	- As we have seen, there are many categories which could be used
      to identify Irving as a writer, yet, they do not cover all
      writers. Categories higher up the hierarchy **(e.g., )** would
      cover more writers but due to some dubious subcategories
      **(e.g., )** also cover pages which definitely are not writers.
	- Each language version has its own category structure, thus the
      effort of identifying appropriate categories and removing false
      positives would need to be repeated.
	- An article can be assigned to several categories which would
      enable identification of writers which also had other
      occupations.
- writer template ::


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



[source-code]: https://en.wikipedia.org/w/index.php?title=John_Irving&action=edit&editintro=Template:BLP_editintro
