---
layout: post
title: "Data-to-Text Generation"
date: 2020-06-19
desc: "Brief overview of Data-to-Text Generation"
keywords: "Blog, NLG, Data-to-Text, NLP"
categories: [Blog, NLP, NLG, D2T]
tags: [Blog, NLP, D2T]
blog: [Blog]
excerpt_separator: <!--more-->
images: 
    - url: /assets/d2t/tasks.jpg
    - url: /assets/d2t/d2tnlg.jpg
    - url: /assets/d2t/t2tnlg.jpg
icon: icon-html
---

<!-- **Under Development** -->

<!-- This blog gives a brief overview of **data-to-text generation** tasks in NLG.  -->
After wandering around in the vast NLP research field for some time, I finally decided to work towards **data-to-text generation** in my PhD. In this blog, I'll try to provide: a brief overview of the task's requirements; some standard public datasets available; and the evaluation metrics used for measuring the performance on these datasets.

<!--more-->

<!-- The main reason for choosing this topic was the part-time project I was working on in early 2020. It was a project in collaboration with an Aberdeen based startup, where I developed a Case-Based approach to **Automated Obituary Genertion**. For a given set of details about a deceased person in some structured format, the requirement was to automatically generate a natural language text summarising that information. 

By working on this project, I realised that there are many existing problems that can be explored, possibly as a PhD project, and that's how I decided to dive deeper into this topic. I'll briefly describe some of the problems I faced in this project in further sections. -->

<!-- We published a paper at ICCBR 2020 as an outcome of this project as well. -->

## Table of Contents

- [Natural Language Generation](#natural-language-generation)
  * [T2T NLG](#t2t-nlg)
  * [D2T NLG](#d2t-nlg)
- [Subtasks in D2T NLG](#subtasks-in-d2t-nlg)
- [Public Datasets & Evaluation Metrics](#public-datasets---evaluation-metrics)
  * [RotoWire](#rotowire)
  * [WebNLG](#webnlg)
  * [Meaning Representations](#meaning-representations)
<!-- - [References](#references) -->

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

## Natural Language Generation

First, let's start with a small introduction on Natural Language Generation (NLG). In NLG, the requirement is to generate a textual output using some automated system for a given input. 

Based on the input provided to the system, NLG can be broadly categorised into three different clusters: first, **text-to-text generation (T2T NLG)**; and second, **data-to-text generation (D2T NLG)**. 

### T2T NLG
As the name suggests, in **T2T NLG**, our goal is to generate text from unstructured textual input. For example, machine translation, where we take a text document in one natural language as input and produce the same content in different natural language as output.

![T2T NLG](/assets/d2t/t2tnlg.jpg){:width="850px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Text-to-Text Natural Language Generation (T2T NLG)</b></p>

### D2T NLG
For **D2T NLG**, the input is presented in a structured format, i.e., tablular, graphical or JSON format. With this structured input, we generate a textual output summarising the input values. For example, summarising NBA match where, for given box- and line-scores as input we have to generate a textual summary of the match as the output.

![D2T NLG](/assets/d2t/d2tnlg.jpg){:width="850px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Data-to-Text Natural Language Generation (D2T NLG)</b></p>

As I'm exploring D2T NLG in my PhD, I'll briefly discuss this task in detail in further sections.

In general, automatically generating natural language is challenging because **grammar rules** are **very complex**. And also, there can be **several meaning** to **same words** in different context. 

Even after we develop a system for automated generation, it is challenging to automatically evaluate the texts generated from that automated system. Unlike most supervised problems, there's **no class knowledge** in form of labels to evaluate the performance. Here the evaluation metric should be capable of measuring: how accurate; how fluent; and how diverse are generated texts from the automated system.

<!-- Apart from all this, the real-world applications (such as the automated obituary generator) suffer from data related problems as well. For starter, you might **not** have **any labelled data** to start building your system. There might be requirement of **a domain expert** to manually label some data, and that may be very expensive. After some-time you might collect some labelled data as a part of your deployment process, that data should be used to refine your system.  -->

<!-- No data -->

## Subtasks in D2T NLG

Let's talk about the subtasks involved in D2T NLG, which can be divided into six different subtasks:

1. ***Content Determination***: deciding which information from the input will be included in the final text;

2. ***Text Structuring***: select the ordering of the selected information in the final text output;

3. ***Sentence Aggregation***: selecting which information to be presented in a separate sentence and which two (or more) information can be presented in the same sentence;

4. ***Lexicalisation***: finding the correct words and phrases to express the information in a sentence;

5. ***Referring Expression Generation***: selecting domain-specific words and phrases; and

6. ***Realisation***: Combining all the words and phrases into well-formed sentences.

![D2T NLG](/assets/d2t/tasks.jpg){:width="850px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Subtasks in D2T NLG</b></p>

Sub-tasks in D2T NLG is illustrated with a simplied example from the neonatal intensive care domain in the above figure. First the system has to decide what the important events are in the data (a,content determination), in this case, occurrences of low heart rate (bradycardias). Then it has to decide in which order it wants to present data to the reader (b, text structuring) and how to express these in individual sentence plans (c, aggregation, lexicalisation, reference). Finally, the resulting sentences are generated (d, linguistic realisation).

## Public Datasets & Evaluation Metrics

Here I mention some of the publicly available standard datasets and the evaluation metrics used to measure the performance of different methods.

### RotoWire
The [dataset](https://github.com/harvardnlp/boxscore-data/blob/master/rotowire.tar.bz2) consists of articles summarizing NBA basketball games, paired with their corresponding box- and line-score tables. It is professionally written, medium length game summaries targeted at fantasy basketball fans. The writing is colloquial, but structured, and targets an audience primarily interested in game statistics <sup>[[2]](#myfootnote2)</sup>.

The performance is evaluated on two different automated metrics: first, **BLEU score**; and second, a family of **Extractive Evaluations (EE)**. EE contains three different submetrics evaluating three different aspects of the generation:

1. **Content Selection (CS)**: precision (P%) and recall (R%) of unique relations extracted from generated text that are also extracted from golden text. This measures how well the generated document matches the gold document in terms of selecting which records to generate.

2. **Relation Generation (RG)**: precision (P%) and number of unique relations (#) extracted from generated text that also appear in structured input provided. This measures how well the system is able to generate text containing factual (i.e., correct) records.

3. **Content Ordering (CO)**: normalized Damerau-Levenshtein Distance (DLD%) between the sequences of records extracted from golden text and that extracted from generated text. This measures how well the system orders the records it chooses to discuss.

| **Model**           | **BLEU** | **CS (P% & R%)** | **RG (P% & #)** | **CO (DLD%)** |  **Paper / Source** | **Code** |
| ------------- | :-----: | :-----: | :-----: | :-----:| --- | --- |
| **Rebuffel, Clément, et al. (2020)** <sup>[[4]](#myfootnote4)</sup> | 17.50 | 39.47 & 51.64 | 89.46 & 21.17 | 18.90 | [A Hierarchical Model for Data-to-Text Generation](https://link.springer.com/chapter/10.1007/978-3-030-45439-5_5) |[Official](https://github.com/KaijuML/data-to-text-hierarchical) |
| **Puduppully et al. (2019)** <sup>[[3]](#myfootnote3)</sup> | 16.50 | 34.18 & 51.22 | 87.47 & 34.28 | 18.58 | [Data-to-text generation with content selection and planning](https://www.aaai.org/ojs/index.php/AAAI/article/view/4668) |[Official](https://github.com/ratishsp/data2text-plan-py) |
| **Wiseman et al. (2017)** <sup>[[2]](#myfootnote2)</sup> | 14.49 | 22.17 & 27.16 | 71.82 & 12.82 | 8.68 | [Challenges in Data-to-Document Generation](https://www.aclweb.org/anthology/D17-1239.pdf) |[Official](https://github.com/harvardnlp/data2text) |

### WebNLG
The [WebNLG challenge](https://webnlg-challenge.loria.fr/) consists in mapping data to text. The training data consists of Data/Text pairs where the data is a set of triples extracted from DBpedia and the text is a verbalisation of these triples. For example, given the three DBpedia triples (as shown in [a]), the aim is to generate a text (as shown in [b]):

* **[a]**. (John_E_Blaha birthDate 1942_08_26) (John_E_Blaha birthPlace San_Antonio) (John_E_Blaha occupation Fighter_pilot)

* **[b]**. John E Blaha, born in San Antonio on 1942-08-26, worked as a fighter pilot.

The performance is evaluated on the basis of **BLEU, METEOR and TER scores**. The data from WebNLG Challenge 2017 can be downloaded [here](https://gitlab.com/shimorina/webnlg-dataset).

| **Model**           | **BLEU** | **METEOR** | **TER** |  **Paper / Source** | **Code** |
| ------------- | :-----: | :-----: | :-----: | --- | --- |
| **Kale, Mihir. (2020)** <sup>[[9]](#myfootnote9)</sup> | 57.1 | 0.44 |  | [Text-to-Text Pre-Training for Data-to-Text Tasks](https://arxiv.org/pdf/2005.10433v2.pdf) |  |
| **Moryossef et al. (2019)** <sup>[[5]](#myfootnote5)</sup> | 47.4 | 0.391 | 0.631 | [Step-by-Step: Separating Planning from Realization in Neural Data-to-Text Generation](https://www.aclweb.org/anthology/N19-1236.pdf) | [Official](https://github.com/AmitMY/chimera) |
| **Baseline** | 33.24 | 0.235436 | 0.613080 | [Baseline system provided during the challenge](https://webnlg-challenge.loria.fr/challenge_2017/#webnlg-baseline-system) |[Official](https://gitlab.com/webnlg/webnlg-baseline) |

**P.S.**: The **test dataset** of WebNLG consists of **total 15 categories**, out of which 10 (**seen**) catgories are used for training while 5 (**unseen**) are not. The results reported here are those obtained on overall test data, i.e., all 15 categories.

### Meaning Representations

The dataset was first provided for the [E2E Challenge](http://www.macs.hw.ac.uk/InteractionLab/E2E/) in 2017. It is a crowd-sourced data set of 50k instances in the restaurant domain.Each instance consist of a dialogue act-based meaning representations (MR) and up to 5 references in natural language (NL). For example:

* **MR**: name[The Eagle], eatType[coffee shop], food[French], priceRange[moderate], customerRating[3/5], area[riverside], kidsFriendly[yes], near[Burger King]

* **NL**: “The three star coffee shop, The Eagle, gives families a mid-priced dining experience featuring a variety of wines and cheeses. Find The Eagle near Burger King.”

The performance is evaluated using **BLEU, NIST, METEOR, ROUGE-L, CIDEr scores**. The data from E2E Challenge 2017 can be downloaded [here](https://github.com/tuetschek/e2e-dataset/releases/download/v1.0.0/e2e-dataset.zip).

| **Model**           | **BLEU** | **NIST** | **METEOR** | **ROUGE-L** | **CIDEr** |  **Paper / Source** | **Code** |
| ------------- | :-----: | :-----: |:-----: |:-----: | :-----: | --- | --- |
| **Shen, Sheng, et al. (2019)** <sup>[[7]](#myfootnote6)</sup> | 68.60 | 8.73 | 45.25 | 70.82 | 2.37 | [Pragmatically Informative Text Generation](https://www.aclweb.org/anthology/N19-1410.pdf) |[Official](https://github.com/sIncerass/prag_generation) |
| **Elder, Henry, et al. (2019)** <sup>[[8]](#myfootnote8)</sup> | 67.38 | 8.7277 | 45.72 | 71.52 | 2.2995 | [Designing a Symbolic Intermediate Representation for Neural Surface Realization](https://www.aclweb.org/anthology/W19-2308.pdf) | |
| **Gehrmann, Sebastian, et al. (2018)** <sup>[[6]](#myfootnote7)</sup> | 66.2 | 8.60 | 45.7 | 70.4 | 2.34 | [End-to-End Content and Plan Selection for Data-to-Text Generation](https://www.aclweb.org/anthology/W18-6505.pdf) |[Official](https://github.com/sebastianGehrmann/diverse_ensembling) |
| **Baseline** | 65.93 | 8.61 | 44.83 | 68.50 | 2.23 | [Baseline system provided during the challenge](http://www.macs.hw.ac.uk/InteractionLab/E2E/#baseline) |[Official](https://github.com/UFAL-DSG/tgen/tree/master/e2e-challenge) |

## References
<a name="myfootnote1">[1]</a> Albert Gatt and Emiel Krahmer. 2018. [Survey of the state of the art in natural language generation: core tasks, applications and evaluation](https://www.jair.org/index.php/jair/article/download/11173/26378/). J. Artif. Int. Res. 61, 1 (January 2018), 65–170.

<a name="myfootnote2">[2]</a> Wiseman, Sam, Stuart M. Shieber, and Alexander M. Rush. "[Challenges in Data-to-Document Generation](https://www.aclweb.org/anthology/D17-1239.pdf)." Proceedings of the 2017 Conference on Empirical Methods in Natural Language Processing. 2017.

<a name="myfootnote3">[3]</a> Puduppully, Ratish, Li Dong, and Mirella Lapata. "[Data-to-text generation with content selection and planning](https://www.aaai.org/ojs/index.php/AAAI/article/view/4668)." Proceedings of the AAAI Conference on Artificial Intelligence. Vol. 33. 2019.

<a name="myfootnote4">[4]</a> Rebuffel, Clément, et al. "[A Hierarchical Model for Data-to-Text Generation](https://link.springer.com/chapter/10.1007/978-3-030-45439-5_5)." European Conference on Information Retrieval. Springer, Cham, 2020.

<a name="myfootnote5">[5]</a> Moryossef, Amit, Yoav Goldberg, and Ido Dagan. "[Step-by-Step: Separating Planning from Realization in Neural Data-to-Text Generation](https://www.aclweb.org/anthology/N19-1236.pdf)." Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers). 2019.

<a name="myfootnote6">[6]</a> Gehrmann, Sebastian, et al. "[End-to-End Content and Plan Selection for Data-to-Text Generation](https://www.aclweb.org/anthology/W18-6505.pdf)." Proceedings of the 11th International Conference on Natural Language Generation. 2018.

<a name="myfootnote7">[7]</a> Shen, Sheng, et al. "[Pragmatically Informative Text Generation](https://www.aclweb.org/anthology/N19-1410.pdf)." Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long and Short Papers). 2019.

<a name="myfootnote8">[8]</a> Elder, Henry, et al. "[Designing a Symbolic Intermediate Representation for Neural Surface Realization](https://www.aclweb.org/anthology/W19-2308.pdf)." Proceedings of the Workshop on Methods for Optimizing and Evaluating Neural Language Generation. 2019.

<a name="myfootnote9">[9]</a> Kale, Mihir. "[Text-to-Text Pre-Training for Data-to-Text Tasks](https://arxiv.org/pdf/2005.10433v2.pdf)" arXiv preprint arXiv:2005.10433 (2020).

