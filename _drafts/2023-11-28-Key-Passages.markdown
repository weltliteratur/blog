---
title: "Working Title: Key Passages in Literary Works"
layout: post
author: [frederik, robert]
comments: true
date: 2023-11-28
---

# Context

In the
[DFG-funded](https://gepris.dfg.de/gepris/projekt/424207720?language=en)
project [What matters? Key Passages in Literary
Works](https://www.projekte.hu-berlin.de/en/schluesselstellen/what-matters-key-passages-in-literary-works)
(which is part of the special priority programm [Computational
Literary Studies](https://dfg-spp-cls.github.io/)) we set out to
identify and characterize key passages in literary works.

We understand key passages as passages that are particularly important
to expert readers when interpreting texts. In a mixed-methods
approach, we investigate empirically which textual characteristics of
literary genres can be revealed through patterns of citation and
quotation.

# Corpus

Our main corpus consists of two literary works [Die
Judenbuche](https://en.wikipedia.org/wiki/Die_Judenbuche) by Annette
von Droste-Hülshoff and [Michael
Kohlhaas](https://en.wikipedia.org/wiki/Michael_Kohlhaas) by Heinrich
von Kleist with 44 and 49 scholarly articles,
respectively. Fortunately, we could build on the previous work of the
[ArguLIT
project](https://gepris.dfg.de/gepris/projekt/372804438?language=en)
and their annotation of all direct quotations.

# Automatic Identification of Quotations

Scholarly texts contain different types of quotations. For example,
verbatim quotes of single words to longer quotations spanning multiple
sentences, and indirect quotations in the form of summarizations or
re-narrations. In the first phase of the project, we focused on the
automatic identification and linking of direct quotations starting
with quotations of a length of five or more words. In [Lotte and
Annette: A Framework for Finding and Exploring Key Passages in
Literary Works](https://aclanthology.org/2021.nlp4dh-1.7.pdf)[^1], we
outline the current landscape for text reuse detection and the
development of our tool [Quid](https://hu.berlin/quid). Although there
are a number of existing tools, we found that all had limitations for
our specific use case. We evaluated Quid and compared it to the
existing tools.

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

**diese Tabelle kurz erklären**

Considerably more difficult to identify are quotations which are
shorter than 5 words. In _A Novel Approach for Identification and
Linking of Short Quotations in Scholarly Texts and Literary
Works_[^2], we develop and compare two approaches to tackle this
challenge, _ProQuo_ and _ProQuoLM_.

[^2]: Accepted at JCLS 2023 and soon to be published.

For ProQuo, we use the (page) references for long quotations as
examples to tell apart (page) references for short quotations from
other text in parenthesis. This includes references like those to the
Bible or other literary works. We then relate short quotes to their
source in the literary work by figuring out the relationships between
the quotes and references. We also use the positions of long quotes as
guides to link short quotations to the correct passage of the literary
work.

For our second approach, ProQuoLM, we fine-tune a German BERT
**verlinken** for classification. First, we identify potential short
quotes, and then use the fine-tuned model to filter them.

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

**Tabelle erklären**

# QuidEx – Visualization and Exploration

We created [QuidEx](https://hu.berlin/quidex), a website for
visualization and exploration of the results, which is shown in this
screenshot:

<figure style="text-align:center;">
  <img src="/images/key-passages-website.jpg" alt="Key passages, website" style="width:900px; border: 1px solid transparent; border-color: black;" />
</figure>

On the left, there's a heatmap that displays the distribution of
quoted passages in the entire literary work. The darker the area, the
more frequently it has been quoted, suggesting its significance. Right
beside the heatmap is the literary work itself. The grayscale
indicates how many scholarly works quote any part of a crucial
passage. This means the level of gray remains constant for the entire
key passage. The font size is adjusted based on how often a minimal
segment is quoted. At the bottom, alongside the literary text, there's
a list of all scholarly works.

**hier noch kurz andere Use-Case zeigen/verlinken? Uni Stuttgart?**

**Quellcode-Repo verlinken?!**

**Repo des SPP-CLS verlinken?**

**Foto vom Banner (Würzburg? HU Hauptgeb? DOR26? oder gleich eine Dreiercollage?)**

# Summary and Outlook

In the first phase of the project, we developed tools to identify,
link, visualize, and explore direct quotations of all lengths.  In
August 2023, the project went into its second phase, titled [Is Expert
Knowledge Key? Scholarly Interpretations as Resource for the Analysis
of Literary Texts in Computational Literary
Studies](https://www.projekte.hu-berlin.de/en/schluesselstellen/).
One important task we are currently working on, is the identification
and linking of indirect quotations, that is, summarizations and
re-narrations.

For daily key passages, follow us on
[Bluesky](https://bsky.app/profile/fredr0id.bsky.social) or try Quid
online with our [web interface](https://hu.berlin/quidweb).
