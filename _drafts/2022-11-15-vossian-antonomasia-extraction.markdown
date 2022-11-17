---
title: "Vossian Antonomasia Extraction: Let's use big guns"
layout: post
author: [michel, robert, frank]
comments: true
date: 2022-11-15
---

Hi there, let’s get back to one of our favorite topics: [Vossian
Antonomasia](https://vossanto.weltliteratur.net/) (VA).  In [our last
paper](https://weltliteratur.net/vossian-antonomasia-next-level/), we
tried to detect VA automatically using rule-based methods and a simple
neural network approach. The latter showed very promising results, so
we continued along this line and pulled out the big guns, the Michael
Jordans in the field of natural language processing: pre-trained
language models.

Neural networks and especially pretrained language models (PLMs) like
[BERT](https://aclanthology.org/N19-1423.pdf) have shown that they can
improve a wide range of NLP tasks, especially those for which large
labeled datasets are not available.

The advantage of language models is the pre-training, which is
conducted with large amounts of unlabeled text data. For example, BERT
was trained on the English Wikipedia and
[BooksCorpus](https://arxiv.org/pdf/1506.06724.pdf). In the
pre-training phase, the model learns a basic understanding of language
that can be used further for downstream tasks, e.g. named entity
recognition (NER), sentiment analysis, or part-of-speech tagging.

Thus, we decided to let loose these “big guns” on our VAs. Instead of
classifying complete sentences, that is, deciding whether a sentence
contains a VA expression or not, we reformulated the task. Now, the
machine learning model is trained to identify all parts of a VA within
a sentence, that is, the source, target and modifier, and distinguish
them from one another. This is called *sequence tagging*.

| Words | A | Spice | Girls | of  | hip- hop | , |  the  | Wu- Tang |  Clan | offers | something | for | every  | kind | of | rap  | fan |
|  Tags | - | B-SRC | I-SRC |  -  |   B-MOD  | - | B-TRG |   I-TRG  | I-TRG |    -   |     -     |  -  |    -   |   -  |  - |   -  |  -  |

For the training of neural networks, we [annotated our VA
dataset](https://github.com/weltliteratur/vossanto/tree/master/frontiers)
on the word-level, that is we marked for each word in 3,066 sentences
whether it is part of source, target, or modifier or does not belong
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

|       Task       |  Approach | Precision | Recall |   F1  |
|:----------------:|:---------:|:---------:|:------:|:-----:|
|                  | Baseline  |     0.876 |  0.880 | 0.878 |
| Classification   | BLSTM-ATT |     0.921 |  0.074 | 0.947 |
|                  | BERT-CLF  |     0.971 |  0.977 | 0.974 |
|:----------------:|:---------:|:---------:|:------:|:-----:|
|                  | BASELINE  |     0.765 |  0.616 | 0.682 |
| Sequence-Tagging | BLSTM-CRF |     0.908 |  0.907 | 0.907 |
|                  | BERT-SEQ  |     0.908 |  0.944 | 0.926 |

First, we could improve the sentence classification task by almost 0.1
points in F1 score.  Also, we could achieve strong results (0.93 in F1
score) on the new sequence tagging task, where BERT outperforms the
BLSTM-CRF model.

In addition to the performance on our annotated dataset, we conducted
a robustness study on real-world newspaper data. We also studied the
ability of the model to predict new types of VA focussing on new types
of source entities (e.g., organizations, locations, fictional
characters) and on new syntactic variations around the source (e.g.,
“a SOURCE on”, “of SOURCE of”). In total, the model identified around
10,000 VA candidates in the NYT corpus that our previous models were
not able to find. Table 2 shows the most frequently predicted source
candidates. Due to limited capacities, we only evaluated samples of
these candidates.

| source candidates | Count |
|-------------------|-------|
| Holy Grail        |   116 |
| Cadillac          |    88 |
| Pied Piper        |    85 |
| RollsRoyce        |    71 |
| Paris             |    60 |
| Harvard           |    58 |
| Microsoft         |    43 |
| Venice            |    42 |
| Demon Barber      |    39 |
| King              |    37 |
| Switzerland       |    37 |
| McDonalds         |    35 |
| Darth Vader       |    34 |
| Wild West         |    33 |
| Cinderella        |    32 |
| Goliath           |    29 |
| Woodstock         |    29 |
| Athens            |    28 |
| Mecca             |    28 |
| Taj Mahal         |    28 |


Summing it up, in our newest paper, we developed new models for
extracting VAs on the word-level, that is, the models tag all words
that belong to a VA expression in a sentence.  In addition to the high
evaluation scores on our annotated dataset, we showed in multiple
robustness studies that the best model is able to predict new versions
of VAs regarding syntactic variations and also types of named
entities.

The full annotation and deeper analytics of the predicted candidates
is one of our next projects. If you are interested in participation,
feel free to contact us. Stay tuned!
