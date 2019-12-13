---
title: "Which DH Tools Are Actually Used in Research?"
layout: post
author: [laure, frank, yoann, ivan]
comments: true
date: 2019-12-06
---

Not that we didn't know that, but Gephi is the most popular DH tool actually used in research work. Followed by Omeka, stylo, MALLET, Excel, D3.js, the NLTK, WordPress, Drupal, TextGrid, CollateX, GeoNames, TXM, Solr and Voyant Tools.

We know this because we did some counting. So let's explain:

The longest-standing tool directory in the Digital Humanities, the Canadian portal [TAPoR](http://tapor.ca/home) led by Geoffrey Rockwell, has around 1.500 DH tools in its database (including historic ones). We were wondering how this richness of means and utilities in our field is manifested in actual research work. To gain some first insights, we decided to extract the names of tools from TAPoR (which is easy thanks to their API) and match them with the proceedings of the largest and broadest event series in the Digital Humanities, ADHO's annual DH conferences. The proceedings from DH2015 to DH2019 are [freely available](https://github.com/ADHO/) (licensed under CC BY 4.0, thx to Fabio Ciotti for giving us early access to the DH2019 data), so that was our chosen source:

* DH2015, Sydney
* DH2016, Kraków
* DH2017, Montréal
* DH2018, Ciudad de México
* DH2019, Utrecht

Altogether, **238 tools** were mentioned at least once in these five years, and we counted **1.498 mentions** of tools altogether in all the proceedings. To extract this kind of data, we wrote a little Java tool called [**ToolXtractor**](https://github.com/lehkost/ToolXtractor/), which you can run yourself with alternative source material if you like and also with different lists of tools. Since this is simple string matching, we had to throw out some false positives manually (not too many, though).

We set up another website providing a complete list of all mentioned tools including a link to corresponding conference abstracts for verification: ["Tools mentioned in the proceedings of the annual ADHO conferences (2015–2019)"](https://lehkost.github.io/tools-dh-proceedings/index.html)

Please also check the [**ranking**](#ranking) of all tools at the very bottom of this blog post for further insights.

## 40 Most Used Tools

Here are the 40 tools with most mentions (an interactive version is here: [https://datawrapper.dwcdn.net/L96xg/](https://datawrapper.dwcdn.net/L96xg/)):

<figure style="text-align:left;">
  <img src="/images/dh-tools-used-in-research/40-most-used-tools.png" alt="40 most used tools (via Datawrapper)" style="width:1000px;" />
</figure>

(**Ed.** We know that this line chart visually suggests a connection between tools that isn't there. We still consider this type of display to be beneficial – especially in the [interactive version](https://datawrapper.dwcdn.net/L96xg/) – since you can compare occurrences per tool per year. By hovering over the lines you will see that, e.g., 2016 was the year of **stylo** and **TextGrid**, 2017 the year of **Leaflet**, 2018 the year of **Omeka** and 2019 the year of **GeoNames** and **Transkribus**. – Big thx to Jan Horstmann for bringing this up.)

## Known Issues

Before we continue with more visualisations, some caveats:

* Of course, this is not a complete list of all tools mentioned in the proceedings, only of those tools comprised in the TAPoR database (the vast majority should be covered, though).
* We decided to leave programming languages like Python or JavaScript in, just like social networks (Twitter) and other things that are not DH tools in a narrower sense. Given that we published the data, it is easy to take them out to get a clearer view at actual DH tools.
* We had to use a stopword list containing tools with names that are also frequent terms, like ["Processing"](https://processing.org/), and we also left out one-letter programming languages, like R and C. Especially R is quite popular in our community and it would be great to compare it to its biggest contender: Python. But this would be future work. (Stopword list etc. to be found in the [ToolXtractor repo](https://github.com/lehkost/ToolXtractor/).)

Btw, everyone is welcome to do their own viz, [the dataset is freely available (in CSV format)](https://lehkost.github.io/tools-dh-proceedings/tools-dh-proceedings.csv).

## Streamgraph

This graph shows all tools and their mentions per year (but rather than staring at the graph below you should check out the interactive version of it featuring dynamic captions: [https://rpubs.com/Pozdniakov/stream_dh](https://rpubs.com/Pozdniakov/stream_dh)):

<figure style="text-align:left;">
  <img src="/images/dh-tools-used-in-research/streamgraph.png" alt="Streamgraph" style="width:925px;" />
</figure>

## Line Chart and Bar Plot (Top-10 Tools)

<figure style="text-align:left;">
  <img src="/images/dh-tools-used-in-research/linechart-top-10-tools.png" alt="" style="width:490px;" />
  <img src="/images/dh-tools-used-in-research/bar-plot-top-10-tools.png" alt="" style="width:490px;" />
</figure>

## Bar Plot and Stacked Area (All Tools)

<figure style="text-align:left;">
  <img src="/images/dh-tools-used-in-research/bar-plot-all-tools.png" alt="" style="width:490px;" />
  <img src="/images/dh-tools-used-in-research/stacked-area-all-tools.png" alt="" style="width:490px;" />
</figure>

## Ranking

All 238 tools mentioned with number of occurrences 2015–2019:

1. Python (125)
2. Twitter (82)
3. Gephi (60)
4. JavaScript (59)
5. Omeka (44)
6. GitHub (40)
7. HathiTrust (37)
8. stylo (35)
9. MALLET (33)
10. Google Books (31)
11. Excel (30)
12. MySQL (27)
13. D3.js (23)
14. Natural Language Toolkit · NLTK (23)
15. WordPress (20)
16. Drupal (19)
17. TextGrid (19)
18. CollateX (18)
19. GeoNames (18)
20. TXM (18)
21. Solr (17)
22. Voyant Tools (17)
23. EEBO-TCP (15)
24. Palladio (15)
25. PostgreSQL (15)
26. Bootstrap (14)
27. Leaflet (14)
28. OpenRefine (14)
29. Zotero (14)
30. eXist-db (13)
31. Google Maps (13)
32. Tesseract (13)
33. ArcGIS (12)
34. Music Encoding Initiative (12)
35. Transkribus (12)
36. Carto · CartoDB (11)
37. Juxta (10)
38. KWIC (10)
39. Perl (10)
40. Neatline (9)
41. GAMS (8)
42. Hypothes.is (8)
43. Jekyll (8)
44. MediaWiki (8)
45. Recogito (8)
46. Ruby · Ruby on Rails (8)
47. Tableau · Tableau Public (8)
48. AntConc (7)
49. Chrome (7)
50. Firefox (7)
51. Lucene (7)
52. OpenStreetMap (7)
53. Pundit (7)
54. Tesserae (7)
55. TRACER (7)
56. Zenodo (7)
57. Annotation Studio (6)
58. Cytoscape (6)
59. GATE (6)
60. Lexos (6)
61. Neo4j (6)
62. Photogrammar (6)
63. TEI Boilerplate (6)
64. WebLicht (6)
65. WorldCat (6)
66. CATMA (5)
67. Google Scholar (5)
68. LIWC · Linguistic Inquiry and Word Count (5)
69. QGIS (5)
70. Blacklight (4)
71. Bookworm (4)
72. Dropbox (4)
73. Freebase (4)
74. Google Ngram Viewer (4)
75. JGAAP (4)
76. nodegoat (4)
77. Oral History Metadata Synchronizer (4)
78. Protégé (4)
79. Textual Communities (4)
80. Tumblr (4)
81. VARD · VARD 2 (4)
82. Weka (4)
83. Wordle (4)
84. WordSmith (4)
85. Blender (3)
86. Commons In A Box (3)
87. CQPweb (3)
88. ELAN (3)
89. Google Drive (3)
90. NetworkX (3)
91. NodeXL (3)
92. OxGarage (3)
93. PhiloLine (3)
94. RStudio (3)
95. Skype (3)
96. TILE (3)
97. TileMill (3)
98. Tropy (3)
99. Versioning Machine (3)
100. ABBYY FineReader (2)
101. ANNIS (2)
102. Archive-It (2)
103. arts-humanities.net (2)
104. ATLAS.ti (2)
105. Bokeh (2)
106. Dataverse (2)
107. DiRT Directory (2)
108. Diva.js (2)
109. DSpace (2)
110. EATS (2)
111. ediarum (2)
112. Fedora Commons (2)
113. FromThePage (2)
114. Gamera (2)
115. igraph (2)
116. ImageJ (2)
117. Inkscape (2)
118. Islandora (2)
119. Joomla (2)
120. Map Warper (2)
121. Matlab (2)
122. MAXQDA (2)
123. MorphAdorner (2)
124. oXygen (2)
125. Pandoc (2)
126. Paper Machines (2)
127. PhiloLogic (2)
128. Protovis (2)
129. RelFinder (2)
130. RoSE (2)
131. Slack (2)
132. Spotify (2)
133. SylvaDB (2)
134. T-PEN (2)
135. TAPoR (2)
136. TRAViz (2)
137. TypeWright (2)
138. UIMA (2)
139. VSim (2)
140. Abbot (1)
141. Academia.edu (1)
142. Adobe After Effects (1)
143. Adobe Flash (1)
144. Adobe Illustrator (1)
145. Adobe InDesign (1)
146. Advene (1)
147. Alpheios (1)
148. Alveo (1)
149. Annotorious (1)
150. Anthologize (1)
151. Anvil (1)
152. AskSam (1)
153. Audacity (1)
154. AustESE (1)
155. Basecamp (1)
156. Beautiful Soup (1)
157. BuddyPress (1)
158. Chart.js (1)
159. Chronos Timeline (1)
160. COBOL (1)
161. Collex (1)
162. ColorBrewer (1)
163. Confluence (1)
164. CONTENTdm (1)
165. Dedoose (1)
166. DH Press (1)
167. eLaborate (1)
168. EndNote (1)
169. Evernote (1)
170. EVI-LINHD (1)
171. Exhibit 3.0 (1)
172. ezlinavis (1)
173. FAIMS Mobile Platform (1)
174. Finale (1)
175. GapVis (1)
176. GeoTemCo (1)
177. gFacet (1)
178. Google Docs (1)
179. Graphviz (1)
180. H-Net (1)
181. HyperImage (1)
182. HyperPo (1)
183. Icon (1)
184. ImagePlot (1)
185. IRaMuTeQ (1)
186. IsaViz (1)
187. jsLDA (1)
188. Koha (1)
189. KORA (1)
190. Lexomics (1)
191. LilyPond (1)
192. LimeSurvey (1)
193. LodLive (1)
194. Mediathread (1)
195. Mendeley (1)
196. Mukurtu CMS (1)
197. MuseScore (1)
198. music21 (1)
199. NeOn Toolkit (1)
200. NetDraw (1)
201. NVivo (1)
202. Old Maps Online (1)
203. OmniPage (1)
204. OntoViz (1)
205. OpenLayers (1)
206. Pliny (1)
207. Prefuse (1)
208. Prism (1)
209. Pro Tools (1)
210. ProcessingJS (1)
211. Project Quincy (1)
212. Prolog (1)
213. PyDelta (1)
214. RDF Gravity (1)
215. SARIT (1)
216. Scripto (1)
217. SemLens (1)
218. Serendip (1)
219. Serendip-o-matic (1)
220. Sibelius (1)
221. StoryMapJS (1)
222. Textable (1)
223. Textal (1)
224. Textexture (1)
225. TextRazor (1)
226. tFacet (1)
227. Transana (1)
228. Trello (1)
229. TUSTEP (1)
230. VexFlow (1)
231. Visual Browser (1)
232. VisualEyes (1)
233. VIVO (1)
234. Wavesurfer (1)
235. Wiki Map Project (1)
236. WordCruncher (1)
237. WordHoard (1)
238. YAGO (1)
