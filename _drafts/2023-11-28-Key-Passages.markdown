---
title: "Working Title: Key Passages in Literary Works"
layout: post
author: [robert, frederik]
comments: true
date: 2023-11-28
---

# Context

In the DFG project [What matters? Key Passages in Literary Works](https://www.projekte.hu-berlin.de/en/schluesselstellen/what-matters-key-passages-in-literary-works) which started with its first phase in 2020 and has been in the second phase, titled [Is Expert Knowledge Key? Scholarly Interpretations as Resource for the Analysis of Literary Texts in Computational Literary Studies](https://www.projekte.hu-berlin.de/en/schluesselstellen/index.html), since August 2023, we set out to identify and characterize key passages in literary works. We understand key passages as passages that are particularly important to expert readers when interpreting texts. In a mixed-methods approach, we primarily want to investigate empirically which textual characteristics of literary genres can be revealed through patterns of citation and quotation.

# Corpus

Our main corpus in the first project phase consisted of two literary works _Die Judenbuche_ by Annette von Droste-Hülshoff and _Michael Kohlhaas_ by Heinrich von Kleist with 44 and 49 scholarly articles, respectively. Fortunately, we could build on the previous work of the [ArguLIT project](https://gepris.dfg.de/gepris/projekt/372804438?language=en) and their annotations of all direct quotations.

# Automatic Identification of Quotations

Scholarly texts contain a number of different types of quotations. For example, verbatim quotes from short lengths of single words to longer quotations spanning multiple sentences, and indirect quotations in the form of summarizations or re-narrations. In the first phase of the project, we focused on the automatic identification of linking of direct quotations starting with quotations of a length of five or more words. In [Lotte and Annette: A Framework for Finding and Exploring Key Passages in Literary Works](https://aclanthology.org/2021.nlp4dh-1.7.pdf)[^1], we outline the current landscape for text reuse detection and the development of our tool [Quid](https://hu.berlin/quid). Although there are a number of existing tools, we found that all had limitations for our specific use case. We evaluated Quid and compared it to the existing tools.

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
      <th align="left">F<sub>1</sub></th>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F<sub>1</sub></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">BLAST</td>
      <td align="right">0.59</td>
      <td align="right">0.61</td>
      <td align="right">0.60</td>
      <td align="right">0.37</td>
      <td align="right">0.59</td>
      <td align="right">0.45</td>
    </tr>
    <tr>
      <td align="left">Copyfind</td>
      <td align="right">0.85</td>
      <td align="right">0.75</td>
      <td align="right">0.79</td>
      <td align="right">0.76</td>
      <td align="right">0.79</td>
      <td align="right">0.78</td>
    </tr>
    <tr>
      <td align="left">SimT</td>
      <td align="right"><strong>0.91</strong></td>
      <td align="right">0.64</td>
      <td align="right">0.76</td>
      <td align="right"><strong>0.83</strong></td>
      <td align="right">0.74</td>
      <td align="right"><strong>0.79</strong></td>
    </tr>
    <tr>
      <td align="left">Textmatcher</td>
      <td align="right">0.69</td>
      <td align="right">0.37</td>
      <td align="right">0.48</td>
      <td align="right">0.68</td>
      <td align="right">0.42</td>
      <td align="right">0.52</td>
    </tr>
    <tr>
      <td align="left">Quid</td>
      <td align="right">0.82</td>
      <td align="right"><strong>0.90</strong></td>
      <td align="right"><strong>0.86</strong></td>
      <td align="right">0.70</td>
      <td align="right"><strong>0.90</strong></td>
      <td align="right">0.78</td>
    </tr>
  </tbody>
</table>

Considerably more difficult to identify are quotations which are shorter than 5 words. In A Novel Approach for Identification and Linking of Short Quotations in Scholarly Texts and Literary Works, we develop and compare two approaches to tackle this challenge, _ProQuo_ and _ProQuoLM_.
>Our main idea behind ProQuo is to use the references corresponding to long quotations as examples to distinguish references corresponding to short quotations from other text in parentheses and other references, for example, Bible references or references to other literary works. We then extract relations between short quotations and references and use that information and the position of long quotations as anchors to link short quotations to the literary work.
>
>The second approach is a more general, language model based approach where we fine-tune a German Bert for classification. For this second approach, we first extract candidates for short quotations and then use a fine-tuned language model to filter the candidates.

&mdash; Arnold & Jäschke 2023

<table>
  <thead>
    <tr>
      <th align="center" rowspan="2">Approach</th>
      <th align="center" colspan="3">Die Judenbuche</th>
      <th align="center" colspan="3">Michael Kohlhaas</th>
    </tr>
    <tr>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F<sub>1</sub></th>
      <th align="left">Precision</th>
      <th align="left">Recall</th>
      <th align="left">F<sub>1</sub></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="left">Baseline</td>
      <td align="right">0.65</td>
      <td align="right"><strong>0.78</strong></td>
      <td align="right">0.71</td>
      <td align="right">0.59</td>
      <td align="right"><strong>0.75</strong></td>
      <td align="right">0.66</td>
    </tr>
    <tr>
      <td align="left">ProQuo</td>
      <td align="right">0.87</td>
      <td align="right">0.72</td>
      <td align="right">0.79</td>
      <td align="right"><strong>0.87</strong></td>
      <td align="right">0.66</td>
      <td align="right">0.75</td>
    </tr>
    <tr>
      <td align="left">ProQuoML</td>
      <td align="right"><strong>0.88</strong></td>
      <td align="right">0.75</td>
      <td align="right"><strong>0.81</strong></td>
      <td align="right"><strong>0.87</strong></td>
      <td align="right">0.69</td>
      <td align="right"><strong>0.77</strong></td>
    </tr>
  </tbody>
</table>

# QuidEx - Visualization and Exploration

To allow for exploration of the results, we created [QuidEx](https://hu.berlin/quidex), a visualization and exploration website.
>On the left, a heatmap of the complete literary text shows the distribution of quoted passages. The darker the text, the more often it has been quoted and thus the more important it is assumed to be. Next to the heatmap, the literary work is shown. The grayscale is determined by how many scholarly works quote some part of a key passage. That is, the color is always the same for the whole key passage. The font size is determined by how often a minimal segment is quoted. At the bottom, next to the literary text, a list of all scholarly works is shown.

&mdash; [Arnold & Jäschke 2021](https://aclanthology.org/2021.nlp4dh-1.7.pdf)

<figure style="text-align:center;">
  <img src="/images/key-passages-website.jpg" alt="Key passages, website" style="width:900px; border: 1px solid transparent; border-color: black;" />
</figure>

In summary, TBD