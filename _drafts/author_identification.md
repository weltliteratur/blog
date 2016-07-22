---
title: Identifying authors in Wikipedia
layout: post
author: [robert, frank]
comments: true
date: 2016-07-22
---

Let us have a detailed look at a the
[Wikipedia page of John Irving](https://en.wikipedia.org/wiki/John_Irving):

(here screenshot)

We can identify the following features on the web page which tell us
that John Irving is a writer: (for each a screenshot)

1. The /first sentence/ says "John Winslow Irving [...] is an American
   novelist and Academy Award-winning screenwriter."
2. The /table of contents/ lists a bibliography.
3. The /infobox/ on the right says as "Occupation: Novelist,
   Screenwriter".
4. Scrolling down, we find a list of /categories/, among them
   "20th-century American novelists, "21st-century American
   novelists", "American feminist writers", and "American male
   screenwriters".
5. In addition, by looking at
   [the wiki source code of the page ][source-code] we can see that
   the infobox uses the /writer template/:

   {% raw %}
       {{Infobox writer <!--for more information, see [[:Template:Infobox writer/doc]]-->
       | name = John Irving |
       | | image = John Irving at Cologne 2010 (7108).jpg
       ```
   {% endraw %}
	   
- Which of this information is universally available (i.e., in
  different language versions)?
- Which of this information is available in a) DBpedia, b) Wikidata?
- How widespread is the information used? (show counter examples,
  e.g., Kafka and Eco or Tom Cruise & Co.)
- How easy is it to use this information? (Categories: difficult,
  because ... occupation: difficult, because, etc.)

- we explain the different options to assign the flag "writer" to an
  entity in Wikipedia
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
