---
title: "Vossian Antonomasia Extraction Using Pre-Trained Language Models"
layout: post
author: [michel, robert, frank]
comments: true
date: 2022-11-17
---

Hi there, let’s get back to one of our favorite topics: [Vossian
Antonomasia](https://vossanto.weltliteratur.net/) (VA).  In [our 2019
EMNLP-IJCNLP
paper](https://weltliteratur.net/vossian-antonomasia-next-level/), we
tried to detect VA automatically using rule-based methods and a simple
neural network approach. The latter showed very promising results, so
we continued along this line and brought in some heavier machinery –
the Michael Jordans in the field of natural language processing (NLP):
pre-trained language models (PLMs).

Neural networks and especially PLMs like
[BERT](https://aclanthology.org/N19-1423.pdf) have shown that they can
improve a wide range of NLP tasks, especially those for which large
labeled datasets are not available.

The advantage of language models is the pre-training, which is
conducted with large amounts of unlabeled text data. For example, BERT
was trained on the English Wikipedia and
[BooksCorpus](https://arxiv.org/pdf/1506.06724.pdf). In the
pre-training phase, the model learns a basic understanding of language
that can be used further for downstream tasks, for example, named
entity recognition (NER), sentiment analysis, or part-of-speech
tagging.

We decided to try this on Vossian Antonomasia for [our latest paper
published in Frontiers in Artificial
Intelligence](https://doi.org/10.3389/frai.2022.868249).  Instead of
classifying complete sentences, that is, deciding whether a sentence
contains a VA expression or not, we reformulated the task. Now, the
machine learning model is trained to identify all parts of a VA within
a sentence, that is, the source, target and modifier, and distinguish
them from one another. This is called *sequence tagging*.

<table>
  <tr>
    <th>Words:</th>
    <td>A</td>
    <td>Spice</td>
    <td>Girls</td>
    <td>of</td>
    <td>hip-hop</td>
    <td>,</td>
    <td>the</td>
    <td>Wu-Tang</td>
    <td>Clan</td>
    <td>offers</td>
    <td>something</td>
    <td>for</td>
    <td>every</td>
    <td>kind</td>
    <td>of</td>
    <td>rap</td>
    <td>fan</td>
  </tr>
  <tr>
    <th>Tags:</th>
    <td>-</td>
    <td>B-SRC</td>
    <td>I-SRC</td>
    <td>-</td>
    <td>B-MOD</td>
    <td>-</td>
    <td>B-TRG</td>
    <td>I-TRG</td>
    <td>I-TRG</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
    <td>-</td>
  </tr>
</table>

For the training of neural networks, we [annotated our VA
dataset](https://github.com/weltliteratur/vossanto/tree/master/frontiers)
on the word-level, that is we marked for each word in 3,066 sentences
whether it is part of a source, target, or modifier or does not belong
to a VA at all.

We then used the BERT base model and fine-tuned it with the annotated
data. In particular, we added an additional layer on top of the BERT
model that computes a tag for each word of the input sentence. Then
the parameters were re-computed based on the input data.

In addition, we also trained a neural network model from scratch using
a concatenation of [ELMo](https://allenai.org/allennlp/software/elmo)
and [GloVe](https://nlp.stanford.edu/projects/glove/) embeddings and a
bidirectional [long short-term
memory](https://en.wikipedia.org/wiki/Long_short-term_memory) (BLSTM)
neural network with a [conditional random
field](https://en.wikipedia.org/wiki/Conditional_random_field) (CRF)
on top that also tags each word.

<!--
| Task               | Approach    |   Precision |   Recall |      F1 |
| :----------------: | :---------: | :---------: | :------: | :-----: |
|                    | Baseline    |       0.876 |    0.880 |   0.878 |
| Classification     | BLSTM-ATT   |       0.921 |    0.074 |   0.947 |
|                    | BERT-CLF    |       0.971 |    0.977 |   0.974 |
|                    |             |             |          |         |
|                    | BASELINE    |       0.765 |    0.616 |   0.682 |
| Sequence-Tagging   | BLSTM-CRF   |       0.908 |    0.907 |   0.907 |
|                    | BERT-SEQ    |       0.908 |    0.944 |   0.926 |
-->

<table>
  <thead>
    <tr>
      <th align="center">Task</th>
      <th align="center">Approach</th>
      <th align="center">Precision</th>
      <th align="center">Recall</th>
      <th align="center">F1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th align="left" rowspan="3">Classification</th>
      <td align="left">Baseline</td>
      <td align="right">0.876</td>
      <td align="right">0.880</td>
      <td align="right">0.878</td>
    </tr>
    <tr>
      <td align="left">BLSTM-ATT</td>
      <td align="right">0.921</td>
      <td align="right">0.074</td>
      <td align="right">0.947</td>
    </tr>
    <tr>
      <td align="left">BERT-CLF</td>
      <td align="right">0.971</td>
      <td align="right">0.977</td>
      <td align="right">0.974</td>
    </tr>
    <tr>
      <th align="left" rowspan="3">Sequence-Tagging</th>
      <td align="left">BASELINE</td>
      <td align="right">0.765</td>
      <td align="right">0.616</td>
      <td align="right">0.682</td>
    </tr>
    <tr>
      <td align="left">BLSTM-CRF</td>
      <td align="right">0.908</td>
      <td align="right">0.907</td>
      <td align="right">0.907</td>
    </tr>
    <tr>
      <td align="left">BERT-SEQ</td>
      <td align="right">0.908</td>
      <td align="right">0.944</td>
      <td align="right">0.926</td>
    </tr>
  </tbody>
</table>


First, we could improve the sentence classification task by almost 0.1
points in F1 score.  Also, we could achieve strong results (0.93 in F1
score) on the new sequence tagging task, where BERT outperforms the
BLSTM-CRF model.

In addition to the evaluation on our annotated dataset, we conducted a
robustness study on real-world newspaper data. We also studied the
ability of the model to predict new types of VA focussing on new types
of source entities (e.g., organizations, locations, fictional
characters) and on new syntactic variations around the source (e.g.,
“a SOURCE on”, “of SOURCE of”). In total, the model identified around
10,000 VA candidates in the NYT corpus that our previous models were
not able to find. The following table shows the most frequently
predicted source candidates. Due to limited capacity, we only
evaluated samples of these candidates.

| Source Candidates                                      | Count |
| :----------------------------------------------------- | ----: |
| [Holy Grail](https://www.wikidata.org/wiki/Q162808)    |   116 |
| [Cadillac](https://www.wikidata.org/wiki/Q27436)       |    88 |
| [Pied Piper](https://www.wikidata.org/wiki/Q106880435) |    85 |
| [RollsRoyce](https://www.wikidata.org/wiki/Q243278)    |    71 |
| [Paris](https://www.wikidata.org/wiki/Q90)             |    60 |
| [Harvard](https://www.wikidata.org/wiki/Q13371)        |    58 |
| [Microsoft](https://www.wikidata.org/wiki/Q2283)       |    43 |
| [Venice](https://www.wikidata.org/wiki/Q641)           |    42 |
| Demon Barber                                           |    39 |
| [King](https://www.wikidata.org/wiki/Q116)             |    37 |
| [Switzerland](https://www.wikidata.org/wiki/Q39)       |    37 |
| [McDonalds](https://www.wikidata.org/wiki/Q38076)      |    35 |
| [Darth Vader](https://www.wikidata.org/wiki/Q12206942) |    34 |
| [Wild West](https://www.wikidata.org/wiki/Q14947899)   |    33 |
| [Cinderella](https://www.wikidata.org/wiki/Q11841)     |    32 |
| [Goliath](https://www.wikidata.org/wiki/Q192785)       |    29 |
| [Woodstock](https://www.wikidata.org/wiki/Q164815)     |    29 |

In summary, in our newest paper, we developed new models for
extracting VAs on the word-level, that is, the models tag all words
that belong to a VA expression in a sentence.  In addition to the high
evaluation scores on our annotated dataset, we showed in multiple
robustness studies that the best model is able to predict new versions
of VAs regarding syntactic variations and also types of named
entities.

The full annotation and deeper analytics of the predicted candidates
is one of our next projects. If you are interested in participation,
feel free to contact us. Stay tuned!
