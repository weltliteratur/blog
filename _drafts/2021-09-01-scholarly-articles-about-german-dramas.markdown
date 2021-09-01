---
title: 'Quantification of Scholarly Articles on German Drama'
layout: post
author: [robert, frank]
comments: true
date: 2021-09-01
---

# Context

In our project ["What matters? Key passages in literary
works"](https://gepris.dfg.de/gepris/projekt/424207720?language=en) we
analyse how scholarly articles cite literary works and whether these
citations can be used to identify key passages. We started with a
corpus of 100 scholarly articles dealing with the interpretion of one
of two novellas:

* [*Michael Kohlhaas*](https://en.wikipedia.org/wiki/Michael_Kohlhaas) by Heinrich von Kleist (1808)
* [*Die Judenbuche*](https://en.wikipedia.org/wiki/Die_Judenbuche) by Annette von Droste-Hülshoff (1842)

In the next phase of our project, we want to focus on German-language
drama and are therefore building a corpus of scholarly articles that
set out to interpret German plays. For our distant-reading approach,
this corpus should be substantial, that is, for each play we would like
to have a number of scholarly articles dealing with it. So one of our
operationalisation questions was: "Which plays should we select so
that we can find a reasonable number of scholarly works per play?" Or
more generally: "Which German plays have been interpreted most
frequently by researchers?"

# Data Sources

To answer this question, we utilise two well-known data sources:

* [GerDraCor](https://dracor.org/ger), the German Drama Corpus, which
  is part of the larger [DraCor](https://dracor.org/) project and
  currently comprises 545 German plays from the period
  1657[¹](https://dracor.org/id/ger000538) to
  1947.[²](https://dracor.org/id/ger000476) DraCor provides the full
  texts of all plays (which is crucial for our project) as well as
  detailed metadata such as title, author or year of publication.
* The [BDSL online catalogue](http://www.bdsl-online.de/),
  short for [Bibliography of German Linguistics and
  Literature](https://www.ub.uni-frankfurt.de/bdsl/), a comprehensive
  bibliography of more than 300,000 scholarly works on German language
  and literature. It offers broad search options, in particular it is
  possible to search for articles that refer to a specific work (by
  title) or an author (by name).

# Implementation

1. We downloaded a GerDraCor snapshot on August 31, 2021, by cloning
   its git repository (`git clone git@github.com:dracor-org/gerdracor.git`).
2. Using a small Python script, we extracted the title
   (XPath: `tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:title`)
   and author's name (XPath:
   `tei:teiHeader/tei:fileDesc/tei:titleStmt/tei:author`) for each play.
   The resulting TSV file contains 545 plays. The name of authors is stored
   in the format "Surname, Forename", titles of plays separated from it by a tab character.
   
   Here the first entries of the resulting list:
   ```
   Alberti, Konrad   Brot!
   Alberti, Konrad   Im Suff
   André, Johann   Der Comödienfeind
   Anzengruber, Ludwig   Das vierte Gebot
   Anzengruber, Ludwig   Der Gwissenswurm
   [...]
   ```
3. Looping over the list of plays, we queried BDSL for interpretations
   of each play on the same day, August 31, 2021. It is possible to
   search for "Behandeltes Werk" (work treated), which allows us to
   restrict the search to scholarly articles whose subject is a specific
   work (using the plays' titles). As some titles are ambiguous,
   initial tests have shown that we need to further restrict the
   search to "Behandelte Person" (person treated), which names the
   author of the work.

# Results

## Per Play

For the following 172 plays we were able to find an interpretation
(that is, for 373 we could not):

| Play                                             | Author                           | Interpretations |
|--------------------------------------------------|----------------------------------|-----------------|
| Faust                                            | Johann Wolfgang Goethe           |            2037 |
| Dantons Tod                                      | Georg Büchner                    |             309 |
| Nathan der Weise                                 | Gotthold Ephraim Lessing         |             307 |
| Penthesilea                                      | Heinrich von Kleist              |             304 |
| Iphigenie auf Tauris                             | Johann Wolfgang Goethe           |             243 |
| Emilia Galotti                                   | Gotthold Ephraim Lessing         |             193 |
| Prinz Friedrich von Homburg                      | Heinrich von Kleist              |             172 |
| Die Räuber                                       | Friedrich Schiller               |             171 |
| Wilhelm Tell                                     | Friedrich Schiller               |             147 |
| Der zerbrochne Krug                              | Heinrich von Kleist              |             143 |
| Maria Stuart                                     | Friedrich Schiller               |             123 |
| Leonce und Lena                                  | Georg Büchner                    |             116 |
| Die Jungfrau von Orleans                         | Friedrich Schiller               |             116 |
| Die Hermannsschlacht                             | Heinrich von Kleist              |             114 |
| Elektra                                          | Hugo von Hofmannsthal            |             111 |
| Torquato Tasso                                   | Johann Wolfgang Goethe           |             109 |
| Kabale und Liebe                                 | Friedrich Schiller               |             102 |
| Die letzten Tage der Menschheit                  | Karl Kraus                       |             100 |
| Amphitryon                                       | Heinrich von Kleist              |              97 |
| Reigen                                           | Arthur Schnitzler                |              85 |
| Der Schwierige                                   | Hugo von Hofmannsthal            |              77 |
| Die Zauberflöte                                  | Emanuel Schikaneder              |              71 |
| Miß Sara Sampson                                 | Gotthold Ephraim Lessing         |              70 |
| Egmont                                           | Johann Wolfgang Goethe           |              66 |
| Die Familie Schroffenstein                       | Heinrich von Kleist              |              57 |
| Die Soldaten                                     | Jakob Michael Reinhold Lenz      |              50 |
| Der Rosenkavalier                                | Hugo von Hofmannsthal            |              47 |
| Frühlings Erwachen                               | Frank Wedekind                   |              47 |
| Draußen vor der Tür                              | Wolfgang Borchert                |              45 |
| Die natürliche Tochter                           | Johann Wolfgang Goethe           |              45 |
| Ariadne auf Naxos                                | Hugo von Hofmannsthal            |              44 |
| Judith                                           | Friedrich Hebbel                 |              43 |
| Maria Magdalene                                  | Friedrich Hebbel                 |              43 |
| König Ottokars Glück und Ende                    | Franz Grillparzer                |              42 |
| Die Verschwörung des Fiesco zu Genua             | Friedrich Schiller               |              41 |
| Die Jüdin von Toledo                             | Franz Grillparzer                |              40 |
| Der Turm                                         | Hugo von Hofmannsthal            |              40 |
| Philotas                                         | Gotthold Ephraim Lessing         |              39 |
| Libussa                                          | Franz Grillparzer                |              37 |
| Jedermann                                        | Hugo von Hofmannsthal            |              36 |
| Stella                                           | Johann Wolfgang Goethe           |              35 |
| Die Frau ohne Schatten                           | Hugo von Hofmannsthal            |              34 |
| Geschichten aus dem Wiener Wald                  | Ödön von Horváth                 |              34 |
| Vor Sonnenaufgang                                | Gerhart Hauptmann                |              31 |
| Die Büchse der Pandora                           | Frank Wedekind                   |              31 |
| Die Juden                                        | Gotthold Ephraim Lessing         |              30 |
| Ein Bruderzwist in Habsburg                      | Franz Grillparzer                |              29 |
| Die Hermannsschlacht                             | Christian Dietrich Grabbe        |              28 |
| Herzog Theodor von Gothland                      | Christian Dietrich Grabbe        |              28 |
| Die Schwärmer                                    | Robert Musil                     |              27 |
| Anatol                                           | Arthur Schnitzler                |              26 |
| Der grüne Kakadu                                 | Arthur Schnitzler                |              26 |
| Die Ratten                                       | Gerhart Hauptmann                |              25 |
| Agnes Bernauer                                   | Friedrich Hebbel                 |              25 |
| Liebelei                                         | Arthur Schnitzler                |              23 |
| Der gestiefelte Kater                            | Ludwig Tieck                     |              23 |
| Don Juan und Faust                               | Christian Dietrich Grabbe        |              21 |
| Arabella                                         | Hugo von Hofmannsthal            |              21 |
| Der Unbestechliche                               | Hugo von Hofmannsthal            |              21 |
| Kasimir und Karoline                             | Ödön von Horváth                 |              21 |
| Professor Bernhardi                              | Arthur Schnitzler                |              21 |
| Clavigo                                          | Johann Wolfgang Goethe           |              20 |
| Proserpina                                       | Johann Wolfgang Goethe           |              20 |
| Gyges und sein Ring                              | Friedrich Hebbel                 |              20 |
| Der Marquis von Keith                            | Frank Wedekind                   |              20 |
| Scherz, Satire, Ironie und tiefere Bedeutung     | Christian Dietrich Grabbe        |              19 |
| Der Traum ein Leben                              | Franz Grillparzer                |              19 |
| Weh dem, der lügt!                               | Franz Grillparzer                |              19 |
| Cardenio und Celinde oder Unglücklich Verliebete | Andreas Gryphius                 |              19 |
| Hermanns Schlacht                                | Friedrich Gottlieb Klopstock     |              18 |
| Die Kindermörderin                               | Heinrich Leopold Wagner          |              18 |
| Der Tod des Tizian                               | Hugo von Hofmannsthal            |              17 |
| Der Talisman                                     | Johann Nestroy                   |              17 |
| Das weite Land                                   | Arthur Schnitzler                |              17 |
| Des Meeres und der Liebe Wellen                  | Franz Grillparzer                |              15 |
| Herodes und Mariamne                             | Friedrich Hebbel                 |              15 |
| Die Wupper                                       | Else Lasker-Schüler              |              15 |
| Die Gründung Prags                               | Clemens Brentano                 |              14 |
| Ödipus und die Sphinx                            | Hugo von Hofmannsthal            |              14 |
| Das Liebeskonzil                                 | Oskar Panizza                    |              14 |
| Die Ahnfrau                                      | Franz Grillparzer                |              13 |
| Das Salzburger große Welttheater                 | Hugo von Hofmannsthal            |              13 |
| Die Zwillinge                                    | Friedrich Maximilian Klinger     |              13 |
| Der Zerrissene                                   | Johann Nestroy                   |              13 |
| Der Triumph der Empfindsamkeit                   | Johann Wolfgang Goethe           |              12 |
| Hannibal                                         | Christian Dietrich Grabbe        |              12 |
| Medea                                            | Franz Grillparzer                |              12 |
| Judith und Holofernes                            | Johann Nestroy                   |              12 |
| Erdgeist                                         | Frank Wedekind                   |              12 |
| Ponce de Leon                                    | Clemens Brentano                 |              11 |
| Ein treuer Diener seines Herrn                   | Franz Grillparzer                |              11 |
| Der Sohn                                         | Walter Hasenclever               |              11 |
| Genoveva                                         | Friedrich Hebbel                 |              11 |
| Julius von Tarent                                | Johann Anton Leisewitz           |              11 |
| Der einsame Weg                                  | Arthur Schnitzler                |              11 |
| Die Journalisten                                 | Gustav Freytag                   |              10 |
| Sappho                                           | Franz Grillparzer                |              10 |
| Blunt oder der Gast                              | Karl Philipp Moritz              |              10 |
| Alceste                                          | Christoph Martin Wieland         |              10 |
| Der letzte Held von Marienburg                   | Joseph von Eichendorff           |               9 |
| Almansor                                         | Heinrich Heine                   |               9 |
| Die Familie Selicke                              | Arno Holz                        |               9 |
| Zriny                                            | Theodor Körner                   |               9 |
| Komödie der Verführung                           | Arthur Schnitzler                |               9 |
| Leben und Tod der heiligen Genoveva              | Ludwig Tieck                     |               9 |
| Florian Geyer                                    | Gerhart Hauptmann                |               8 |
| Sturm und Drang                                  | Friedrich Maximilian Klinger     |               8 |
| Der junge Gelehrte                               | Gotthold Ephraim Lessing         |               8 |
| Einen Jux will er sich machen                    | Johann Nestroy                   |               8 |
| Datterich                                        | Ernst Elias Niebergall           |               8 |
| Der Alpenkönig und der Menschenfeind             | Ferdinand Raimund                |               8 |
| Wallensteins Lager                               | Friedrich Schiller               |               8 |
| Alarcos                                          | Friedrich Schlegel               |               8 |
| Die verkehrte Welt                               | Ludwig Tieck                     |               8 |
| Franziska                                        | Frank Wedekind                   |               8 |
| Ugolino                                          | Heinrich Wilhelm von Gerstenberg |               7 |
| Der Engländer                                    | Jakob Michael Reinhold Lenz      |               7 |
| Wallensteins Tod                                 | Friedrich Schiller               |               7 |
| Canut                                            | Johann Elias Schlegel            |               7 |
| Halle                                            | Achim von Arnim                  |               6 |
| Jerusalem                                        | Achim von Arnim                  |               6 |
| Die Freier                                       | Joseph von Eichendorff           |               6 |
| Des Epimenides Erwachen                          | Johann Wolfgang Goethe           |               6 |
| Demetrius                                        | Friedrich Hebbel                 |               6 |
| Freiheit in Krähwinkel                           | Johann Nestroy                   |               6 |
| Moral                                            | Ludwig Thoma                     |               6 |
| Faust                                            | Friedrich Theodor Vischer        |               6 |
| Perdu! oder Dichter, Verleger und Blaustrümpfe   | Annette von Droste-Hülshoff      |               5 |
| Erwin und Elmire                                 | Johann Wolfgang Goethe           |               5 |
| Babel und Bibel                                  | Karl May                         |               5 |
| Magdalena                                        | Ludwig Thoma                     |               5 |
| Die Laune des Verliebten                         | Johann Wolfgang Goethe           |               4 |
| Die Mitschuldigen                                | Johann Wolfgang Goethe           |               4 |
| Satyros oder der vergötterte Waldteufel          | Johann Wolfgang Goethe           |               4 |
| Der Tod Adams                                    | Friedrich Gottlieb Klopstock     |               4 |
| Der Diamant des Geisterkönigs                    | Ferdinand Raimund                |               4 |
| Der Verschwender                                 | Ferdinand Raimund                |               4 |
| Der Kammersänger                                 | Frank Wedekind                   |               4 |
| Hidalla oder Sein und Haben                      | Frank Wedekind                   |               4 |
| Codrus                                           | Johann Friedrich von Cronegk     |               3 |
| Merlin                                           | Karl Immermann                   |               3 |
| Tristan und Isolde                               | Richard Wagner                   |               3 |
| Die Zensur                                       | Frank Wedekind                   |               3 |
| Kaiser Friedrich Barbarossa                      | Christian Dietrich Grabbe        |               2 |
| Uriel Acosta                                     | Karl Gutzkow                     |               2 |
| Gabriel Schillings Flucht                        | Gerhart Hauptmann                |               2 |
| Colberg                                          | Paul Heyse                       |               2 |
| Alkestis                                         | Hugo von Hofmannsthal            |               2 |
| Ein Trauerspiel in Berlin                        | Karl von Holtei                  |               2 |
| Die Koralle                                      | Georg Kaiser                     |               2 |
| Der Kreidekreis                                  | Klabund                          |               2 |
| Der Erbförster                                   | Otto Ludwig                      |               2 |
| Das Haus der Temperamente                        | Johann Nestroy                   |               2 |
| Der Barometermacher auf der Zauberinsel          | Ferdinand Raimund                |               2 |
| Die Piccolomini                                  | Friedrich Schiller               |               2 |
| Der Bettler                                      | Reinhard Sorge                   |               2 |
| Heimat                                           | Hermann Sudermann                |               2 |
| Musik                                            | Frank Wedekind                   |               2 |
| Johann Faust                                     | Paul Weidmann                    |               2 |
| Die Nase des Michelangelo                        | Hugo Ball                        |               1 |
| Der blaue Boll                                   | Ernst Barlach                    |               1 |
| Narziß                                           | Albert Emil Brachvogel           |               1 |
| Brutus                                           | Joachim Wilhelm von Brawe        |               1 |
| Die Frau im Fenster                              | Hugo von Hofmannsthal            |               1 |
| Simsone Grisaldo                                 | Friedrich Maximilian Klinger     |               1 |
| Franz von Sickingen                              | Ferdinand Lassalle               |               1 |
| Die Makkabäer                                    | Otto Ludwig                      |               1 |
| Golo und Genovefa                                | Maler Müller                     |               1 |
| Der Weibsteufel                                  | Karl Schönherr                   |               1 |
| Ernst Herzog von Schwaben                        | Ludwig Uhland                    |               1 |
| Tannhäuser und Der Sängerkrieg auf Wartburg      | Richard Wagner                   |               1 |
| Faust                                            | Hermann Ludwig Wolfram           |               1 |


Although it did not surprise us to find Goethe's Faust on the first
position we probably did not expect that there are an order of
magnitude more interpretations focusing on Faust than on its runner-up
*Dantons Tod* by Büchner. That being said, the followup positions bear
some surprises:


## Per Author

To see whose plays have been interpreted most often, we can group the
result by author and sort them:

| Author                   | Plays | Interpretations | Mean Interpretations per Play |
|--------------------------|-------|-----------------|-------------------------------|
| Johann Wolfgang Goethe   |    22 |            2610 |                           118 |
| Heinrich von Kleist      |     7 |             887 |                           126 |
| Friedrich Schiller       |    11 |             717 |                            65 |
| Gotthold Ephraim Lessing |    12 |             647 |                            53 |
| Hugo von Hofmannsthal    |    17 |             478 |                            28 |
| Georg Büchner            |     2 |             425 |                           212 |
| Franz Grillparzer        |    13 |             247 |                            19 |
| Arthur Schnitzler        |    13 |             218 |                            16 |
| Friedrich Hebbel         |    13 |             163 |                            12 |
| Frank Wedekind           |    12 |             131 |                            10 |

This gives an advantage to prolific authors, since they have more
plays that could be written about. Thus, an alternative is to use the
average number of interpretations per play for each author:

| Author                   | Plays | Interpretations | Mean Interpretations per Play |
|--------------------------|-------|-----------------|-------------------------------|
| Georg Büchner            |     2 |             425 |                           212 |
| Heinrich von Kleist      |     7 |             887 |                           126 |
| Johann Wolfgang Goethe   |    22 |            2610 |                           118 |
| Emanuel Schikaneder      |     1 |              71 |                            71 |
| Friedrich Schiller       |    11 |             717 |                            65 |
| Gotthold Ephraim Lessing |    12 |             647 |                            53 |
| Karl Kraus               |     2 |             100 |                            50 |
| Wolfgang Borchert        |     1 |              45 |                            45 |
| Hugo von Hofmannsthal    |    17 |             478 |                            28 |
| Robert Musil             |     1 |              27 |                            27 |

This shows very clearly in numbers that there have of course been
authors who have made literary history with very few plays (sometimes
only one). However, we must of course take this ranking with a grain of salt.
We see that Georg Büchner is represented by only two works (namely "Leonce and
Lena" and "Danton's Death"). This is because the fragment "Woyzeck" has not yet
been included in GerDraCor. I.e., these results only make statements about the
plays that are part of the corpus.
