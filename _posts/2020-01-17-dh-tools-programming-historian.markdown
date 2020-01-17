---
title: 'DH Tools Mentioned in "The Programming Historian"'
layout: post
author: [frank, yoann]
comments: true
date: 2020-01-17
---

This is a little follow-up to our blog post [**"Which DH Tools Are Actually Used in Research?"**](/dh-tools-used-in-research/) – The idea is to get a general overview of tool mentionings in the fabulous lectures of [**"The Programming Historian"**](https://programminghistorian.org/) (PH). We again used our [ToolXtractor](https://github.com/lehkost/ToolXtractor/) to extract tool names from PH's 87 (English-language) lectures to date (including 7 retired ones), directly from [their Markdown source files](https://github.com/programminghistorian/jekyll/tree/gh-pages/en/lessons). Like last time, we used [TAPoR's](http://tapor.ca/home) database as positive list (for ToolXtractor relies on simple string matching). Any tool we failed to extract was not in TAPoR (yet), e.g., "Unity", "Notepad++", or "Atom" – an obvious shortcoming of this approach.

We also created a co-occurence graph (tools mentioned in the same lesson):

<figure style="text-align:left;">
  <img src="/images/proghist-co-occurrence-graph.png" alt="co-occurrence graph for tools mentioned in ProgHist lessons" style="width:1024px;" />
</figure>

You can spot Python, R, Excel, GitHub and Zotero at the core of teaching in the Digital Humanities. Publishing tools are grouped on the left, network tools on the upper right side. GIS tools are on the bottom right-hand side, text analysis tools are located right above the centre, etc. (The graph was generated in a heartbeat with our tool [ezlinavis](https://ezlinavis.dracor.org) and embellished with Gephi.)

No further analysis, just this overview:

## [jupyter-notebooks](https://programminghistorian.org/en/lessons/jupyter-notebooks) (11)
* GitHub
* Google Drive
* JavaScript
* Omeka
* OpenRefine
* Python
* R
* Ruby
* Twitter
* Voyant Tools
* Zenodo

## [building-static-sites-with-jekyll-github-pages](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages) (9)
* Blogger
* Drupal
* Jekyll
* Omeka
* Ruby
* Slack
* Tumblr
* Twitter
* WordPress

## [mapping-with-python-leaflet](https://programminghistorian.org/en/lessons/mapping-with-python-leaflet) (9)
* ArcGIS
* C
* GeoNames
* GitHub
* Google Maps
* Leaflet
* Nominatim
* OpenStreetMap
* Python

## [using-javascript-to-create-maps](https://programminghistorian.org/en/lessons/using-javascript-to-create-maps) (9)
* Excel
* Gephi
* Google Maps
* GPS Visualizer
* JavaScript
* Leaflet
* MapBox
* Palladio
* Zotero

## [corpus-analysis-with-antconc](https://programminghistorian.org/en/lessons/corpus-analysis-with-antconc) (8)
* AntConc
* Beautiful Soup
* KWIC
* Natural Language Toolkit · NLTK
* OpenRefine
* Python
* R
* Voyant Tools

## [creating-network-diagrams-from-historical-sources](https://programminghistorian.org/en/lessons/creating-network-diagrams-from-historical-sources) (8)
* Gephi
* nodegoat
* NodeXL
* Pajek
* Palladio
* Python
* UCINET
* VennMaker

## [geoparsing-text-with-edinburgh](https://programminghistorian.org/en/lessons/geoparsing-text-with-edinburgh) (7)
* Excel
* Firefox
* GapVis
* GeoNames
* Google Maps
* QGIS
* Twitter

## [text-mining-with-extracted-features](https://programminghistorian.org/en/lessons/text-mining-with-extracted-features) (7)
* HT-Bookworm
* Excel
* GitHub
* HathiTrust
* Matlab
* Python
* R

## [beginners-guide-to-twitter-data](https://programminghistorian.org/en/lessons/beginners-guide-to-twitter-data) (6)
* Cytoscape
* Excel
* Gephi
* Palladio
* Tableau
* Twitter

## [creating-apis-with-python-and-flask](https://programminghistorian.org/en/lessons/creating-apis-with-python-and-flask) (6)
* BBEdit
* Firefox
* JavaScript
* MediaWiki
* Python
* Twitter

## [introduction-to-ffmpeg](https://programminghistorian.org/en/lessons/introduction-to-ffmpeg) (6)
* Audacity
* Chrome
* Excel
* plot.ly
* RAW
* Twitter

## [sonification](https://programminghistorian.org/en/lessons/sonification) (6)
* Excel
* GitHub
* Pandoc
* Python
* R
* Ruby

## [visualizing-with-bokeh](https://programminghistorian.org/en/lessons/visualizing-with-bokeh) (6)
* Bokeh
* CartoDB
* Excel
* Leaflet
* Python
* QGIS

## [exploring-and-analyzing-network-data-with-python](https://programminghistorian.org/en/lessons/exploring-and-analyzing-network-data-with-python) (5)
* Gephi
* NetworkX
* Palladio
* Python
* R

## [geocoding-qgis](https://programminghistorian.org/en/lessons/geocoding-qgis) (5)
* ArcGIS
* Excel
* Google Maps
* OpenStreetMap
* QGIS

## [getting-started-with-github-desktop](https://programminghistorian.org/en/lessons/retired/getting-started-with-github-desktop) (retired) (5)
* Dropbox
* Google Drive
* Jekyll
* Pandoc
* Python

## [getting-started-with-mysql-using-r](https://programminghistorian.org/en/lessons/getting-started-with-mysql-using-r) (5)
* MySQL
* Python
* R
* RStudio
* SQL Server

## [googlemaps-googleearth](https://programminghistorian.org/en/lessons/googlemaps-googleearth) (5)
* ArcGIS
* Excel
* Google Maps
* QGIS
* Twitter

## [introduction-to-populating-a-website-with-api-data](https://programminghistorian.org/en/lessons/introduction-to-populating-a-website-with-api-data) (5)
* Chrome
* Firefox
* GeoNames
* JavaScript
* Skype

## [introduction-to-stylometry-with-python](https://programminghistorian.org/en/lessons/introduction-to-stylometry-with-python) (5)
* Natural Language Toolkit · NLTK
* Python
* R
* stylo
* Zotero

## [json-and-jq](https://programminghistorian.org/en/lessons/json-and-jq) (5)
* Excel
* JavaScript
* Python
* R
* Twitter

## [qgis-layers](https://programminghistorian.org/en/lessons/qgis-layers) (5)
* ArcGIS
* GDAL
* OpenLayers
* Python
* QGIS

## [sustainable-authorship-in-plain-text-using-pandoc-and-markdown](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown) (5)
* Google Docs
* Jekyll
* Pandoc
* WordPress
* Zotero

## [temporal-network-analysis-with-r](https://programminghistorian.org/en/lessons/temporal-network-analysis-with-r) (5)
* Gephi
* NetworkX
* Python
* R
* RStudio

## [analyzing-documents-with-tfidf](https://programminghistorian.org/en/lessons/analyzing-documents-with-tfidf) (4)
* Bokeh
* Excel
* Overview
* Python

## [extracting-illustrated-pages](https://programminghistorian.org/en/lessons/extracting-illustrated-pages) (4)
* HathiTrust
* Python
* R
* Tesseract

## [extracting-keywords](https://programminghistorian.org/en/lessons/extracting-keywords) (4)
* Excel
* OpenRefine
* Python
* QGIS

## [fetch-and-parse-data-with-openrefine](https://programminghistorian.org/en/lessons/fetch-and-parse-data-with-openrefine) (4)
* Excel
* Natural Language Toolkit · NLTK
* OpenRefine
* Python

## [graph-databases-and-SPARQL](https://programminghistorian.org/en/lessons/retired/graph-databases-and-SPARQL) (retired) (4)
* Excel
* GeoNames
* Palladio
* plot.ly

## [intro-to-twitterbots](https://programminghistorian.org/en/lessons/intro-to-twitterbots) (4)
* GitHub
* Python
* Slack
* Twitter

## [keywords-in-context-using-n-grams](https://programminghistorian.org/en/lessons/keywords-in-context-using-n-grams) (4)
* Firefox
* KWIC
* Python
* Zotero

## [sentiment-analysis](https://programminghistorian.org/en/lessons/sentiment-analysis) (4)
* GitHub
* Natural Language Toolkit · NLTK
* Python
* Twitter

## [transforming-xml-with-xsl](https://programminghistorian.org/en/lessons/transforming-xml-with-xsl) (4)
* Chrome
* Excel
* Firefox
* GitHub

## [counting-frequencies-from-zotero-items](https://programminghistorian.org/en/lessons/retired/counting-frequencies-from-zotero-items) (retired) (3)
* Google Books
* Python
* Zotero

## [creating-and-viewing-html-files-with-python](https://programminghistorian.org/en/lessons/creating-and-viewing-html-files-with-python) (3)
* Firefox
* Python
* Zotero

## [data-mining-the-internet-archive](https://programminghistorian.org/en/lessons/data-mining-the-internet-archive) (3)
* Google Maps
* Python
* Wordle

## [data_wrangling_and_management_in_R](https://programminghistorian.org/en/lessons/data_wrangling_and_management_in_R) (3)
* Python
* R
* RStudio

## [generating-an-ordered-data-set-from-an-OCR-text-file](https://programminghistorian.org/en/lessons/generating-an-ordered-data-set-from-an-OCR-text-file) (3)
* JavaScript
* Perl
* Python

## [georeferencing-qgis](https://programminghistorian.org/en/lessons/georeferencing-qgis) (3)
* GDAL
* Google Maps
* QGIS

## [geospatial-data-analysis](https://programminghistorian.org/en/lessons/geospatial-data-analysis) (3)
* Google Maps
* plot.ly
* R

## [gravity-model](https://programminghistorian.org/en/lessons/gravity-model) (3)
* Excel
* R
* RStudio

## [installing-omeka](https://programminghistorian.org/en/lessons/installing-omeka) (3)
* MySQL
* Omeka
* WordPress

## [intro-to-powershell](https://programminghistorian.org/en/lessons/intro-to-powershell) (3)
* Mallet
* Pandoc
* Python

## [introduction-and-installation](https://programminghistorian.org/en/lessons/introduction-and-installation) (3)
* Beautiful Soup
* Dropbox
* Python

## [output-data-as-html-file](https://programminghistorian.org/en/lessons/output-data-as-html-file) (3)
* Firefox
* Python
* Zotero

## [output-keywords-in-context-in-html-file](https://programminghistorian.org/en/lessons/output-keywords-in-context-in-html-file) (3)
* Firefox
* KWIC
* Python

## [topic-modeling-and-mallet](https://programminghistorian.org/en/lessons/topic-modeling-and-mallet) (3)
* Excel
* Mallet
* Voyant Tools

## [automated-downloading-with-wget](https://programminghistorian.org/en/lessons/automated-downloading-with-wget) (2)
* Python
* Ruby

## [basic-text-processing-in-r](https://programminghistorian.org/en/lessons/basic-text-processing-in-r) (2)
* R
* RStudio

## [cleaning-data-with-openrefine](https://programminghistorian.org/en/lessons/cleaning-data-with-openrefine) (2)
* Excel
* OpenRefine

## [cleaning-ocrd-text-with-regular-expressions](https://programminghistorian.org/en/lessons/cleaning-ocrd-text-with-regular-expressions) (2)
* Excel
* Python

## [correspondence-analysis-in-R](https://programminghistorian.org/en/lessons/correspondence-analysis-in-R) (2)
* R
* Zenodo

## [creating-new-items-in-zotero](https://programminghistorian.org/en/lessons/retired/creating-new-items-in-zotero) (retired) (2)
* Python
* Zotero

## [dealing-with-big-data-and-network-analysis-using-neo4j](https://programminghistorian.org/en/lessons/dealing-with-big-data-and-network-analysis-using-neo4j) (2)
* Excel
* Python

## [editing-audio-with-audacity](https://programminghistorian.org/en/lessons/editing-audio-with-audacity) (2)
* Audacity
* Soundflower

## [getting-started-with-markdown](https://programminghistorian.org/en/lessons/getting-started-with-markdown) (2)
* Pandoc
* Perl

## [intro-to-beautiful-soup](https://programminghistorian.org/en/lessons/intro-to-beautiful-soup) (2)
* Beautiful Soup
* Python

## [intro-to-the-zotero-api](https://programminghistorian.org/en/lessons/retired/intro-to-the-zotero-api) (retired) (2)
* Python
* Zotero

## [mac-installation](https://programminghistorian.org/en/lessons/mac-installation) (2)
* Beautiful Soup
* Python

## [naive-bayesian](https://programminghistorian.org/en/lessons/naive-bayesian) (2)
* Beautiful Soup
* Python

## [OCR-with-Tesseract-and-ScanTailor](https://programminghistorian.org/en/lessons/retired/OCR-with-Tesseract-and-ScanTailor) (retired) (2)
* Tesseract
* Zotero

## [preserving-your-research-data](https://programminghistorian.org/en/lessons/preserving-your-research-data) (2)
* Excel
* WordPress

## [r-basics-with-tabular-data](https://programminghistorian.org/en/lessons/r-basics-with-tabular-data) (2)
* Excel
* R

## [transliterating](https://programminghistorian.org/en/lessons/transliterating) (2)
* Beautiful Soup
* Python

## [understanding-regular-expressions](https://programminghistorian.org/en/lessons/understanding-regular-expressions) (2)
* Python
* Ruby

## [vector-layers-qgis](https://programminghistorian.org/en/lessons/vector-layers-qgis) (2)
* Google Maps
* QGIS

## [working-with-web-pages](https://programminghistorian.org/en/lessons/working-with-web-pages) (2)
* Firefox
* Python

## [applied-archival-downloading-with-wget](https://programminghistorian.org/en/lessons/applied-archival-downloading-with-wget) (1)
* Python

## [code-reuse-and-modularity](https://programminghistorian.org/en/lessons/code-reuse-and-modularity) (1)
* Python

## [counting-frequencies](https://programminghistorian.org/en/lessons/counting-frequencies) (1)
* Python

## [creating-an-omeka-exhibit](https://programminghistorian.org/en/lessons/creating-an-omeka-exhibit) (1)
* Omeka

## [creating-mobile-augmented-reality-experiences-in-unity](https://programminghistorian.org/en/lessons/creating-mobile-augmented-reality-experiences-in-unity) (1)
* C

## [downloading-multiple-records-using-query-strings](https://programminghistorian.org/en/lessons/downloading-multiple-records-using-query-strings) (1)
* Python

## [from-html-to-list-of-words-1](https://programminghistorian.org/en/lessons/from-html-to-list-of-words-1) (1)
* Python

## [from-html-to-list-of-words-2](https://programminghistorian.org/en/lessons/from-html-to-list-of-words-2) (1)
* Python

## [installing-python-modules-pip](https://programminghistorian.org/en/lessons/installing-python-modules-pip) (1)
* Python

## [intro-to-bash](https://programminghistorian.org/en/lessons/intro-to-bash) (1)
* Pandoc

## [intro-to-linked-data](https://programminghistorian.org/en/lessons/intro-to-linked-data) (1)
* GeoNames

## [linux-installation](https://programminghistorian.org/en/lessons/linux-installation) (1)
* Python

## [manipulating-strings-in-python](https://programminghistorian.org/en/lessons/manipulating-strings-in-python) (1)
* Python

## [normalizing-data](https://programminghistorian.org/en/lessons/normalizing-data) (1)
* Python

## [research-data-with-unix](https://programminghistorian.org/en/lessons/research-data-with-unix) (1)
* Excel

## [up-and-running-with-omeka](https://programminghistorian.org/en/lessons/up-and-running-with-omeka) (1)
* Omeka

## [viewing-html-files](https://programminghistorian.org/en/lessons/viewing-html-files) (1)
* Firefox

## [windows-installation](https://programminghistorian.org/en/lessons/windows-installation) (1)
* Python

## [working-with-text-files](https://programminghistorian.org/en/lessons/working-with-text-files) (1)
* Python

## [intro-to-augmented-reality-with-unity](https://programminghistorian.org/en/lessons/retired/intro-to-augmented-reality-with-unity) (retired) (0)
* (none)
