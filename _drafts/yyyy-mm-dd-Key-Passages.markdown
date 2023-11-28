---
title: "TBD"
layout: post
author: [robert, frederik]
comments: true
date: 2023-12-24
---

# Context

In the DFG project [What matters? Key Passages in Literary Works](https://www.projekte.hu-berlin.de/en/schluesselstellen/what-matters-key-passages-in-literary-works) which started with its first phase in 2020 and has been in the second phase, titled [Is Expert Knowledge Key? Scholarly Interpretations as Resource for the Analysis of Literary Texts in Computational Literary Studies](https://www.projekte.hu-berlin.de/en/schluesselstellen/index.html), since August 2023, we set out to identify and characterize key passages in literary works. We understand key passages as passages that are particularly important to expert readers when interpreting texts. In a mixed-methods approach, we primarily want to investigate empirically which textual characteristics of literary genres can be revealed through patterns of citation and quotation.

# Corpus

TBD

# Automatic Identification of Quotations

Scholarly texts contain a number of different types of references. For example, verbatim quotes from short lengths of single words to longer quotations spanning multiple sentences, and indirect quotations in the form of summarizations or re-narrations. In the first phase of the project, we focused on the automatic identification of linking of direct quotations starting with quotations of a length of five or more words. In [Lotte and Annette: And Framwork for Finding and Exploring Key Passages in Literary Works](https://aclanthology.org/2021.nlp4dh-1.7.pdf)[^1], we outline the current landscape for text reuse detection and the development of our tool [Quid](https://hu.berlin/quid). Although there are a number of existing tools, we found that all had limitations for our specific use case. We evaluate Quid and compare it to the  existing tools.

[^1]: Lotte and Annette have since been renamed to Quid and QuidEx, respectively.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="3">Approach</th>
      <th align="center" colspan="3">Die Judenbuche</th>
      <th align="center" colspan="3">Michael Kohlhaas</th>
    </tr>
    <tr>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F1</th>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">BLAST</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">Copyfind</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">SimT</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">Textmatcher</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">Quid</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
  </tbody>
</table>

Considerably more difficult to identify are quotations which are shorter than 5 words. In A Novel Approach for Identification and Linking of Short Quotations in Scholarly Texts and Literary Works, we develop and compare two approaches to tackle this challenge, ProQuo and ProQuoLM. ProQuo is a pipeline consisting of three steps.
>Our main idea behind ProQuo is to use the references corresponding to long quotations as examples to distinguish references corresponding to short quotations from other text in parentheses and other references, for example, Bible references or references to other literary works. We then extract relations between short quotations and references and use that information and the position of long quotations as anchors to link short quotations to the literary work.
The second approach is a more general, language model based approach where we fine-tune a German Bert for classification. For this second approach, we first extract candidates for short quotations and then use a fine-tuned language model to filter the candidates.

<table>
  <thead>
    <tr>
      <th align="center" rowspan="2">Approach</th>
      <th align="center" colspan="3">Die Judenbuche</th>
      <th align="center" colspan="3">Michael Kohlhaas</th>
    </tr>
    <tr>
      <th align="left">Precision</th>
      <th align="left">Recall</th^>
      <th align="left">F1</th>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">Baseline</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">ProQuo</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
    <tr>
      <td align="left">ProQuoML</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
      <td align="right">0</td>
    </tr>
  </tbody>
</table>

# QuidEx - Visualization and Exploration

To allow for exploration of the results, we created [QuidEx](https://hu.berlin/quidex), a visualization and exploration website.
>On the left, a heatmap of the complete literary text shows the distribution of quoted passages. The darker the text, the more often it has been quoted and thus the more important it is assumed to be. Next to the heatmap, the literary work is shown. The grayscale is determined by how many scholarly works quote some part of a key passage. That is, the color is always the same for the whole key passage. The font size is determined by how often a minimal segment is quoted. At the bottom, next to the literary text, a list of all scholarly works is shown.