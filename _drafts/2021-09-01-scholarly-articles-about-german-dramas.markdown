---
title: 'Scholarly Articles about German Dramas'
layout: post
author: [robert, frank]
comments: true
date: 2021-09-01
---

# Context

- [What matters? Key passages in literary
  works](https://gepris.dfg.de/gepris/projekt/424207720?language=en)
  analysing how scholarly articles cite literary works and whether
  these citations can be used to identify key passages.

  - start with two works, then focus on (German) drama
  - thus, need a corpus of literary (interpretatory) works on German
    drama
  - distant reading, in general: larger corpus desirable,
    specifically, having several works dealing with the same drama
  - thus: how to find works and how to select dramas?

  - we answer here the question: which German dramas have been subject
    to the most interpretations (according to the BDSL)?

# Data Sources

- [GerDraCor](https://dracor.org/ger), is a German Drama Corpus of the
  [DraCor](https://dracor.org/) project and comprises (currently) XYZ
  German dramas from STARTYEAR to ENDYEAR.
  - full texts of dramas (important for our analysis) but also
    detailed metadata, including title, author, year

- [online catalogue of the BDSL](http://www.bdsl-online.de/) – the
  [Bibliographie der deutschen Sprach- und
  Literaturwissenschaft](https://www.ub.uni-frankfurt.de/bdsl/) – is a large
  bibliography of more than 300,000 scholarly works on German language
  and literature.
  - comprehensive search facilities   - specifically, it is possible to search
    "Behandeltes Werk" and  "Behandelte Person",

# Implementation

- specifically, it is possible to search
    "Behandeltes Werk", which allows us to restrict the search to scholarly works
    whose subject is a specific work (using the work's title)
  - since some titles are ambigue (e.g., ) initial tests showed, that
    we have to further restrict the search to "Behandelte Person",
    naming the author of the literary work

- GerDraCor snapshot as of January 15, 2020 (480 works)
- BDSL queries on January 30, 2020

# Results

For the following 153 works we could find an interpretation (thus, for 327 we could not!):

| Work                                                            | Author                            | interpretations |
|-----------------------------------------------------------------|-----------------------------------|-----------------|
| Faust                                                           | Goethe, Johann Wolfgang           |            2037 |
| Dantons Tod                                                     | Büchner, Georg                    |             309 |
| Nathan der Weise                                                | Lessing, Gotthold Ephraim         |             307 |
| Penthesilea                                                     | Kleist, Heinrich von              |             304 |
| Iphigenie auf Tauris                                            | Goethe, Johann Wolfgang           |             243 |
| Emilia Galotti                                                  | Lessing, Gotthold Ephraim         |             193 |
| Prinz Friedrich von Homburg                                     | Kleist, Heinrich von              |             172 |
| Die Räuber                                                      | Schiller, Friedrich               |             171 |
| Wilhelm Tell                                                    | Schiller, Friedrich               |             147 |
| Maria Stuart                                                    | Schiller, Friedrich               |             123 |
| Die Jungfrau von Orleans                                        | Schiller, Friedrich               |             116 |
| Leonce und Lena                                                 | Büchner, Georg                    |             116 |
| Die Hermannsschlacht                                            | Kleist, Heinrich von              |             114 |
| Elektra                                                         | Hofmannsthal, Hugo von            |             110 |
| Torquato Tasso                                                  | Goethe, Johann Wolfgang           |             108 |
| Kabale und Liebe                                                | Schiller, Friedrich               |             102 |
| Die letzten Tage der Menschheit                                 | Kraus, Karl                       |             100 |
| Amphitryon                                                      | Kleist, Heinrich von              |              97 |
| Reigen                                                          | Schnitzler, Arthur                |              85 |
| Der Schwierige                                                  | Hofmannsthal, Hugo von            |              77 |
| Die Zauberflöte                                                 | Schikaneder, Johann Emanuel       |              71 |
| Miß Sara Sampson                                                | Lessing, Gotthold Ephraim         |              70 |
| Egmont                                                          | Goethe, Johann Wolfgang           |              65 |
| Die Familie Schroffenstein                                      | Kleist, Heinrich von              |              57 |
| Die Soldaten                                                    | Lenz, Jakob Michael Reinhold      |              50 |
| Frühlings Erwachen                                              | Wedekind, Frank                   |              47 |
| Der Rosenkavalier                                               | Hofmannsthal, Hugo von            |              47 |
| Die natürliche Tochter                                          | Goethe, Johann Wolfgang           |              45 |
| Draußen vor der Tür                                             | Borchert, Wolfgang                |              45 |
| Ariadne auf Naxos                                               | Hofmannsthal, Hugo von            |              44 |
| Maria Magdalene                                                 | Hebbel, Friedrich                 |              43 |
| Judith                                                          | Hebbel, Friedrich                 |              43 |
| König Ottokars Glück und Ende                                   | Grillparzer, Franz                |              42 |
| Die Verschwörung des Fiesco zu Genua                            | Schiller, Friedrich               |              41 |
| Der Turm                                                        | Hofmannsthal, Hugo von            |              40 |
| Die Jüdin von Toledo                                            | Grillparzer, Franz                |              40 |
| Philotas                                                        | Lessing, Gotthold Ephraim         |              39 |
| Jedermann                                                       | Hofmannsthal, Hugo von            |              36 |
| Stella                                                          | Goethe, Johann Wolfgang           |              35 |
| Die Frau ohne Schatten                                          | Hofmannsthal, Hugo von            |              34 |
| Die Büchse der Pandora                                          | Wedekind, Frank                   |              31 |
| Die Juden                                                       | Lessing, Gotthold Ephraim         |              30 |
| Ein Bruderzwist in Habsburg                                     | Grillparzer, Franz                |              29 |
| Herzog Theodor von Gothland                                     | Grabbe, Christian Dietrich        |              28 |
| Die Schwärmer                                                   | Musil, Robert                     |              27 |
| Der grüne Kakadu                                                | Schnitzler, Arthur                |              26 |
| Anatol                                                          | Schnitzler, Arthur                |              26 |
| Agnes Bernauer                                                  | Hebbel, Friedrich                 |              25 |
| Die Ratten                                                      | Hauptmann, Gerhart                |              25 |
| Der gestiefelte Kater                                           | Tieck, Ludwig                     |              23 |
| Liebelei                                                        | Schnitzler, Arthur                |              23 |
| Professor Bernhardi                                             | Schnitzler, Arthur                |              21 |
| Kasimir und Karoline                                            | Horváth, Ödön von                 |              21 |
| Der Unbestechliche                                              | Hofmannsthal, Hugo von            |              21 |
| Arabella                                                        | Hofmannsthal, Hugo von            |              21 |
| Don Juan und Faust                                              | Grabbe, Christian Dietrich        |              21 |
| Der Marquis von Keith                                           | Wedekind, Frank                   |              20 |
| Gyges und sein Ring                                             | Hebbel, Friedrich                 |              20 |
| Proserpina                                                      | Goethe, Johann Wolfgang           |              20 |
| Clavigo                                                         | Goethe, Johann Wolfgang           |              20 |
| Der böse Geist Lumpazivagabundus oder Das liederliche Kleeblatt | Nestroy, Johann                   |              19 |
| Weh dem, der lügt!                                              | Grillparzer, Franz                |              19 |
| Der Traum ein Leben                                             | Grillparzer, Franz                |              19 |
| Scherz, Satire, Ironie und tiefere Bedeutung                    | Grabbe, Christian Dietrich        |              19 |
| Die Kindermörderin                                              | Wagner, Heinrich Leopold          |              18 |
| Hermanns Schlacht                                               | Klopstock, Friedrich Gottlieb     |              18 |
| Das weite Land                                                  | Schnitzler, Arthur                |              17 |
| Der Talisman                                                    | Nestroy, Johann                   |              17 |
| Der Tod des Tizian                                              | Hofmannsthal, Hugo von            |              17 |
| Die Wupper                                                      | Lasker-Schüler, Else              |              15 |
| Herodes und Mariamne                                            | Hebbel, Friedrich                 |              15 |
| Des Meeres und der Liebe Wellen                                 | Grillparzer, Franz                |              15 |
| Das Liebeskonzil                                                | Panizza, Oskar                    |              14 |
| Ödipus und die Sphinx                                           | Hofmannsthal, Hugo von            |              14 |
| Die Gründung Prags                                              | Brentano, Clemens                 |              14 |
| Der Zerrissene                                                  | Nestroy, Johann                   |              13 |
| Die Zwillinge                                                   | Klinger, Friedrich Maximilian     |              13 |
| Das Salzburger große Welttheater                                | Hofmannsthal, Hugo von            |              13 |
| Die Ahnfrau                                                     | Grillparzer, Franz                |              13 |
| Erdgeist                                                        | Wedekind, Frank                   |              12 |
| Judith und Holofernes                                           | Nestroy, Johann                   |              12 |
| Hannibal                                                        | Grabbe, Christian Dietrich        |              12 |
| Der Triumph der Empfindsamkeit                                  | Goethe, Johann Wolfgang           |              12 |
| Der einsame Weg                                                 | Schnitzler, Arthur                |              11 |
| Julius von Tarent                                               | Leisewitz, Johann Anton           |              11 |
| Genoveva                                                        | Hebbel, Friedrich                 |              11 |
| Ein treuer Diener seines Herrn                                  | Grillparzer, Franz                |              11 |
| Ponce de Leon                                                   | Brentano, Clemens                 |              11 |
| Alceste                                                         | Wieland, Christoph Martin         |              10 |
| Sappho                                                          | Grillparzer, Franz                |              10 |
| Die Journalisten                                                | Freytag, Gustav                   |              10 |
| Zriny                                                           | Körner, Theodor                   |               9 |
| Die Familie Selicke                                             | Holz, Arno                        |               9 |
| Almansor                                                        | Heine, Heinrich                   |               9 |
| Der letzte Held von Marienburg                                  | Eichendorff, Joseph von           |               9 |
| Franziska                                                       | Wedekind, Frank                   |               8 |
| Die verkehrte Welt                                              | Tieck, Ludwig                     |               8 |
| Alarcos                                                         | Schlegel, Friedrich               |               8 |
| Wallensteins Lager                                              | Schiller, Friedrich               |               8 |
| Der Alpenkönig und der Menschenfeind                            | Raimund, Ferdinand                |               8 |
| Datterich                                                       | Niebergall, Ernst Elias           |               8 |
| Einen Jux will er sich machen                                   | Nestroy, Johann                   |               8 |
| Der junge Gelehrte                                              | Lessing, Gotthold Ephraim         |               8 |
| Sturm und Drang                                                 | Klinger, Friedrich Maximilian     |               8 |
| Canut                                                           | Schlegel, Johann Elias            |               7 |
| Wallensteins Tod                                                | Schiller, Friedrich               |               7 |
| Der Engländer                                                   | Lenz, Jakob Michael Reinhold      |               7 |
| Ugolino                                                         | Gerstenberg, Heinrich Wilhelm von |               7 |
| Moral                                                           | Thoma, Ludwig                     |               6 |
| Freiheit in Krähwinkel                                          | Nestroy, Johann                   |               6 |
| Demetrius                                                       | Hebbel, Friedrich                 |               6 |
| Des Epimenides Erwachen                                         | Goethe, Johann Wolfgang           |               6 |
| Die Freier                                                      | Eichendorff, Joseph von           |               6 |
| Jerusalem                                                       | Arnim, Ludwig Achim von           |               6 |
| Halle                                                           | Arnim, Ludwig Achim von           |               6 |
| Magdalena                                                       | Thoma, Ludwig                     |               5 |
| Babel und Bibel                                                 | May, Karl                         |               5 |
| Erwin und Elmire                                                | Goethe, Johann Wolfgang           |               5 |
| Perdu! oder Dichter, Verleger und Blaustrümpfe                  | Droste-Hülshoff, Annette von      |               5 |
| Hidalla oder Sein und Haben                                     | Wedekind, Frank                   |               4 |
| Der Kammersänger                                                | Wedekind, Frank                   |               4 |
| Der Verschwender                                                | Raimund, Ferdinand                |               4 |
| Der Diamant des Geisterkönigs                                   | Raimund, Ferdinand                |               4 |
| Der Tod Adams                                                   | Klopstock, Friedrich Gottlieb     |               4 |
| Satyros oder der vergötterte Waldteufel                         | Goethe, Johann Wolfgang           |               4 |
| Die Mitschuldigen                                               | Goethe, Johann Wolfgang           |               4 |
| Die Laune des Verliebten                                        | Goethe, Johann Wolfgang           |               4 |
| Die Zensur                                                      | Wedekind, Frank                   |               3 |
| Tristan und Isolde                                              | Wagner, Richard                   |               3 |
| Merlin                                                          | Immermann, Karl                   |               3 |
| Johann Faust                                                    | Weidmann, Paul                    |               2 |
| Musik                                                           | Wedekind, Frank                   |               2 |
| Heimat                                                          | Sudermann, Hermann                |               2 |
| Die Piccolomini                                                 | Schiller, Friedrich               |               2 |
| Der Barometermacher auf der Zauberinsel                         | Raimund, Ferdinand                |               2 |
| Das Haus der Temperamente                                       | Nestroy, Johann                   |               2 |
| Der Erbförster                                                  | Ludwig, Otto                      |               2 |
| Der Kreidekreis                                                 | Klabund                           |               2 |
| Ein Trauerspiel in Berlin                                       | Holtei, Karl von                  |               2 |
| Alkestis                                                        | Hofmannsthal, Hugo von            |               2 |
| Colberg                                                         | Heyse, Paul                       |               2 |
| Uriel Acosta                                                    | Gutzkow, Karl                     |               2 |
| Tannhäuser und Der Sängerkrieg auf Wartburg                     | Wagner, Richard                   |               1 |
| Ernst Herzog von Schwaben                                       | Uhland, Ludwig                    |               1 |
| Der Weibsteufel                                                 | Schönherr, Karl                   |               1 |
| Golo und Genovefa                                               | Müller, Friedrich (Maler Müller)  |               1 |
| Die Makkabäer                                                   | Ludwig, Otto                      |               1 |
| Franz von Sickingen                                             | Lassalle, Ferdinand               |               1 |
| Simsone Grisaldo                                                | Klinger, Friedrich Maximilian     |               1 |
| Die Frau im Fenster                                             | Hofmannsthal, Hugo von            |               1 |
| Brutus                                                          | Brawe, Joachim Wilhelm von        |               1 |
| Narziß                                                          | Brachvogel, Albert Emil           |               1 |
| Die Nase des Michelangelo                                       | Ball, Hugo                        |               1 |

Once more, Goethe's Faust stands out with an order of magnitude more
scholarly works having it as main subject.
