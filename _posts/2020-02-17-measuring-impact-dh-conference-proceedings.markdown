---
title: 'Measuring the Impact of DH Conference Abstracts: The Case of DH2016'
layout: post
author: frank
comments: true
date: 2020-02-17
---

We are still toying around with the proceedings of [ADHO conferences](https://adho.org/conference). This time we are interested in the measurability of the scientific impact of published abstracts.

Long story short, since no other meaningful metrics are at hand (or are there?), we have chosen **Google Scholar**'s citation counts. As a test case we decided to go with the **abstracts from DH2016** in Kraków, because 1. they are well covered in Google Scholar and 2. it has been three and a half years since the conference, so that enough time has passed to actually have an impact and attract citations.

Our starting point was the fabulous **[DBLP](https://en.wikipedia.org/wiki/DBLP)**, a giant computer science bibliography founded at University of Trier. Fortunately they also cover ADHO conferences since some time, so here are all contributions to DH2016 in a concise and interoperable form: [https://dblp1.uni-trier.de/db/conf/dihu/dh2016.html](https://dblp1.uni-trier.de/db/conf/dihu/dh2016.html).

Before we dive into the data, some known issues:
- Google Scholar is ["notoriously hard to mine"](https://www.nature.com/articles/d41586-018-04190-5), there's no API and access is limited (if you don't want to deal with CAPTCHAs and "We're sorry, but your computer network may be sending automated queries" you will have to apply some IP address magic).
- Google Scholar works pretty well, but there might be some incorrectly assigned citations – since their search algorithm is proprietary, we can't really know why things go wrong if they do.
- It is also unclear what exactly is monitored by Google Scholar, so there are definitely missing citations.
- When counting and ranking citations we don't check if they are mainly self-citations.
- Given the above points, please take the following with a grain of salt.

Out of 435 accepted abstracts at DH2016 (plenary lectures, panels, long and short papers, posters, pre-conference workshops and tutorials), 158 are cited at least once according to Google Scholar, **as of 15 February 2020** (= 3,5 years after the conference).

Here are our resulting data sets in case you wanna explore them yourself (CSV format):
1. [DH2016 citations according to Google Scholar](/data/impact-dh2016-abstracts/dh2016-citations-google-scholar.csv) (158 abstracts)
2. [DSH Special DH2016 Issue citations according to Google Scholar](/data/impact-dh2016-abstracts/dh2016-dsh-special-issue-citations-google-scholar.csv) (15 papers)
3. [DH2016 follow-up papers published elsewhere (selection)](/data/impact-dh2016-abstracts/dh2016-papers-published-elsewhere-citations-google-scholar.csv) (3 papers)

What follows are some rankings based on these data sets (plus some general thoughts at the bottom of this blog post):

## 1. Most cited abstracts from DH2016 (as of 15 February 2020)

There are 28 abstracts with at least 4 citations collected by Google Scholar:

* Eetu Mäkelä, Thea Lindquist, Eero Hyvönen: <br />CORE - A Contextual Reader based on Linked Data – Long Paper – **15** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/MakelaLH16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=7822185147793572398))
* Esko Ikkala, Jouni Tuominen, Eero Hyvönen: <br />Contextualizing Historical Places in a Gazetteer by Using Historical Maps and Linked Data – Short Paper – **11** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/IkkalaTH16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=15673204855311481131))
* Terhi Nurmikko-Fuller, Jacob Jett, Timothy W. Cole, Chris Maden, Kevin R. Page, J. Stephen Downie: <br />A Comparative Analysis of Bibliographic Ontologies: Implications for Digital Humanities – Short Paper – **10** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/Nurmikko-Fuller16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=8048646481335919612))
* Peer Trilcke, Frank Fischer, Mathias Göbel, Dario Kampkaspar: <br />Theatre Plays as 'Small Worlds'? Network Data on the History and Typology of German Drama, 1730-1930 – Long Paper – **8** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/TrilckeFGK16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=3941180453510624475))
* Aris Xanthos, Isaac Pante, Yannick Rochat, Martin Grandjean: <br />Visualising the Dynamics of Character Networks – Long Paper – **8** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/XanthosPRG16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=14174769823231486276))
* Manuel Burghardt, Lukas Lamm, David Lechler, Matthias Schneider, Tobias Semmelmann: <br />Tool-based Identification of Melodic Patterns in MusicXML Documents – Short Paper – **8** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/BurghardtLLSS16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=14025672038740466450))
* Fotis Jannidis, Isabella Reger, Markus Krug, Lukas Weimer, Luisa Macharowsky, Frank Puppe: <br />Comparison of Methods for the Identification of Main Characters in German Novels – Short Paper – **8** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/JannidisRKWMP16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=1541757619442963302))
* Roman Klinger, Surayya Samat Suliya, Nils Reiter: <br />Automatic Emotion Detection for Quantitative Literary Studies – Poster – **8** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/KlingerSR16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=3544129917977527749))
* Maciej Maryl, Maciej Piasecki, Ksenia Mlynarczyk: <br />Where Close and Distant Readings Meet: Text Clustering Methods in Literary Analysis of Weblog Genres – Long Paper – **7** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/MarylPM16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=16480967516874896595,8343475867642195584))
* Manuel Burghardt, Michael Kao, Christian Wolff: <br />Beyond Shot Lengths - Using Language Data and Color Information as Additional Parameters for Quantitative Movie Analysis – Poster – **7** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/BurghardtKW16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=11783808221396105186))
* Christof Schöch, Daniel Schlör, Stefanie Popp, Annelen Brunner, Ulrike Henny, José Calvo Tello: <br />Straight Talk! Automatic Recognition of Direct Speech in Nineteenth-Century French Novels – Long Paper – **6** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/SchochSPBHT16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=5739210873641308458))
* Johannes Hellrich, Udo Hahn: <br />Measuring the Dynamics of Lexico-Semantic Change Since the German Romantic Period – Short Paper – **6** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/HellrichH16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=431654030027025291))
* Fahad Khan, Francesca Frontini, Federico Boschetti, Monica Monachini: <br />Converting the Liddell Scott Greek-English Lexicon into Linked Open Data using lemon – Short Paper – **6** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/KhanFBM16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=17882901537315793857))
* Federico Nanni, Pablo Ruiz Fabo: <br />Entities as topic labels: improving topic interpretability and evaluability combining Entity Linking and Labeled LDA – Short Paper – **6** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/NanniF16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=6365131429834412760))
* Susan Brown, Tanya E. Clement, Laura Mandell, Deb Verhoeven, Jacque Wernimont: <br />Creating Feminist Infrastructure in the Digital Humanities – Panel – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/BrownCMVW16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=1060823707180841281))
* Alexander Czmiel: <br />Sustainable publishing - Standardization possibilities for Digital Scholarly Edition technology – Long Paper – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/Czmiel16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=1358527880657138486))
* Isabella di Lenardo, Benoit Seguin, Frédéric Kaplan: <br />Visual Patterns Discovery in Large Databases of Paintings – Long Paper – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/LenardoSK16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=8651297274583880104))
* Francesca Frontini, Carmen Brando, Jean-Gabriel Ganascia: <br />REDEN ONLINE: Disambiguation, Linking and Visualisation of References in TEI Digital Editions – Long Paper – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/FrontiniBG16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=11539777205701010405))
* Kim Jautze, Andreas van Cranenburgh, Corina Koolen: <br />Topic Modeling Literary Quality – Long Paper – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/JautzeCK16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=17014469150281250445))
* Mikko Tolonen, Niko Ilomäki, Hege Roivainen, Leo Lahti: <br />Printing in a Periphery: a Quantitative Study of Finnish Knowledge Production, 1640-1828 – Long Paper – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/TolonenIRL16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=2912387019136768846))
* Peter Robinson, Barbara Bordalejo: <br />Textual Communities – Poster – **5** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/0003B16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=5322581207885764479))
* Alexander Dunst, Rita Hartel, Sven Hohenstein, Jochen Laubrock: <br />Corpus Analyses of Multimodal Narrative: The Example of Graphic Novels – Long Paper – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/DunstHHL16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=13172547380672638477))
* Maciej Eder, Jan Rybicki: <br />Go Set A Watchman while we Kill the Mockingbird in Cold Blood, with Cats and Other People – Long Paper – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/EderR16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=5596591169426158931))
* Chao-Lin Liu: <br />Quantitative Analyses of Chinese Poetry of Tang and Song Dynasties: Using Changing Colors and Innovative Terms as Examples – Long Paper – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/Liu16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=12111986076156693804))
* Alexandre Rigal, Dario Rodighiero, Loup Cellard: <br />The Trajectories Tool: Amplifying Network Visualization Complexity – Long Paper – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/RigalRC16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=9763356290816258798))
* Valérie Beaudouin, Zeynep Pehlivan: <br />The Great War on the Web: the Making of Citing and Referencing by Amateurs – Short Paper – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/BeaudouinP16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=5116065516112527925))
* Angelo Mario Del Grosso, Davide Albanesi, Emiliano Giovannetti, Simone Marchi: <br />Defining the Core Entities of an Environment for Textual Processing in Literary Computing – Poster – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/GrossoAGM16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=17440349976870797986))
* Martin Reckziegel, Stefan Jänicke, Gerik Scheuermann: <br />CTRaCE: Canonical Text Reader and Citation Exporter – Poster – **4** citations <br />([DBLP](https://dblp.org/rec/conf/dihu/ReckziegelJS16)) ([Google Scholar](https://scholar.google.com/scholar?cluster=1700136619339017477))

## 2. Citation counts for follow-up articles published in the DSH special conference issue

EADH's journal "Digital Scholarship in the Humanities" (DSH) published a special edition with 15 selected articles from the DH2016 conference ([Volume 32, Issue suppl_2, December 2017](https://academic.oup.com/dsh/issue/32/suppl_2)). Here are their citation counts (titles sometimes differ from the original abstracts):

* Stefan Evert, Thomas Proisl, Fotis Jannidis, Isabella Reger, Steffen Pielström, Christof Schöch, Thorsten Vitt: <br />[Understanding and explaining Delta measures for authorship attribution](https://doi.org/10.1093/llc/fqx023) – **22** citations (original abstract: 2) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=5709367929062932294))
* Heather Richards-Rissetto: <br />[An iterative 3D GIS analysis of the role of visibility in ancient Maya landscapes: A case study from Copan, Honduras](https://doi.org/10.1093/llc/fqx014) – **10** (2) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=2176558170048823529))
* Stefan Jänicke, David Joseph Wrisley: <br />[Visualizing Mouvance: Toward a visual analysis of variant medieval text traditions](https://doi.org/10.1093/llc/fqx033) – **9** (3) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=7973381259497772230))
* Grace Muzny, Mark Algee-Hewitt, Dan Jurafsky: <br />[Dialogism in the novel: A computational model of the dialogic nature of narration and quotations](https://doi.org/10.1093/llc/fqx031) – **8** (2) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=5269169457931415184))
* Elena González-Blanco, Clara Martínez Cantón, Gimena del Rio Riande, Salvador Ros, Rafael Pastor, Antonio Robles-Gómez, Agustín Caminero, María Luisa Díez Platas, Álvaro del Olmo, Miguel Urízar: <br />[EVI-LINHD, a virtual research environment for the Spanish-speaking community](https://doi.org/10.1093/llc/fqx025) – **5** (2) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=4672347431723511486))
* Arianna Ciula: <br />[Digital palaeography: What is digital about it?](https://doi.org/10.1093/llc/fqx042) – **4** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=1251668675601027055))
* Katarzyna Bazarnik, Jakub Wróblewski: <br />[First We Feel Then We Fall: James Joyce’s Finnegans Wake as an interactive video application](https://doi.org/10.1093/llc/fqx027) – **4** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=3232051797453798596))
* David L Hoover: <br />[The microanalysis of style variation](https://doi.org/10.1093/llc/fqx022) – **3** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=6780436031879293349))
* James O Gawley, A Caitlin Diddams: <br />[Comparing the intertextuality of multiple authors using Tesserae: A new technique for normalization](https://doi.org/10.1093/llc/fqx038) – **3** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=13830734924028487386))
* Marine Riguet, Suzanne Mpouli: <br />[At the crossroads between the scientific and the literary discourse: Comparison as a figure of dialogism](https://doi.org/10.1093/llc/fqx026) – **3** (3) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=4270286382363276284))
* Martijn Kleppe, Marco Otte: <br />[Analysing and understanding news consumption patterns by tracking online user behaviour with a multimodal research design](https://doi.org/10.1093/llc/fqx030) – **3** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=3515976435227019090))
* Claire Warwick: <br />[Beauty is truth: Multi-sensory input and the challenge of designing aesthetically pleasing digital resources](https://doi.org/10.1093/llc/fqx036) – **1** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=7794905959483244893))
* Taylor Arnold, Peter Leonard, Lauren Tilton: <br />[Knowledge creation through recommender systems](https://doi.org/10.1093/llc/fqx035) – **1** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=18225641954619045804))
* Rui Hu, Carlos Pallán Gayol, Jean-Marc Odobez, Daniel Gatica-Perez: <br />[Analyzing and visualizing ancient Maya hieroglyphics using shape: From computer vision to Digital Humanities](https://doi.org/10.1093/llc/fqx028) – **1** (2) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=16064761551397513000))
* Joris J van Zundert, Tara L Andrews: <br />[Qu’est-ce qu’un texte numérique?—A new rationale for the digital representation of text](https://doi.org/10.1093/llc/fqx039) – **0** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=17718895804126846238))

## 3. Articles published elsewhere

As it is not always possible to say whether a full paper is really the elaborated version of a conference abstract, we can't provide an exhaustive list. We only list here the three papers that go by the same titles as the original abstracts:

* Melissa Terras, James Baker, James Hetherington, David Beavan, Martin Zaltz Austwick, Anne Welsh, Helen O'Neill, Will Finley, Oliver Duke-Williams, Adam Farquhar: <br />[Enabling complex analysis of large-scale digital collections: humanities research, high-performance computing, and transforming access to British Library digital collections](https://doi.org/10.1093/llc/fqx020) (DSH 33.2, June 2018) – **12** citations (original abstract: 0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=11682747324791540734))
* Yuta Hashimoto, Yoichi Iikura, Yukio Hisada, SungKook Kang, Tomoyo Arisawa, Daniel Kobayashi-Better: <br />[The Kuzushiji Project: Developing a Mobile Learning Application for Reading Early Modern Japanese Books](http://www.digitalhumanities.org/dhq/vol/11/1/000281/000281.html) (DHQ 11.1, 2017) – **8** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=13178070444385478730))
* Pelle Snickars, Roger Mähler: <br />[SpotiBot-Turing testing Spotify](http://www.digitalhumanities.org/dhq/vol/12/1/000373/000373.html) (DHQ 12.1, 2018) – **7** (0) <br />([Google Scholar](https://scholar.google.com/scholar?cluster=6199034850415843370))

## Some Thoughts

- ADHO conference abstracts do have a measurable scientific impact in the community.
- Publishing a reworked conference abstract in a journal can (but doesn't have to) increase your impact.
- It would be nice to have a more stable, sustainable, citable format for ADHO conference proceedings (think DOIs maybe?).
- Case in point: proceedings of DH2015 in Sydney seem to have vanished into the internet ether, there are only a bunch of unrendered XML files left somewhere, not really citable.
- DOIs for books of abstracts are already a step in the right direction (see, e.g., DOI:[10.5281/zenodo.2596095](https://doi.org/10.5281/zenodo.2596095) for DHd2019).
- Working with Google Scholar is still tedious. There are some Python libraries that are supposed to make it easier to work with it, but they don't cover the full range of Google Scholar functions, and the proprietary mechanism can change at any time without warning and render these libraries unusable.

Anyway, so much for this little experiment. It's a beautiful day in Moscow, time to visit the ice rink in Gorky Park! ❄️
