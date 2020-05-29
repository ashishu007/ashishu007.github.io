---
layout: post
title: "Case-Based Approach to Automated Natural Language Generation for Obituaries"
date: 2020-04-08
desc: "This blog is a brief explanation of my recently accepted paper at ICCBR 2020"
keywords: "Blog, NLG, Papers, Textual CBR"
categories: [Blog, NLP, TCBR, NLG]
tags: [Blog, NLP, TCBR]
blog: [Blog]
excerpt_separator: <!--more-->
images: 
    - url: /assets/iccbr/annot.png
    - url: /assets/iccbr/d2tnlg.png
    - url: /assets/iccbr/t2tnlg.png
    - url: /assets/iccbr/obit.jpg
icon: icon-html
---

<div style="text-align: justify"> 
Recently, my paper titled <b>Case-Based Approach to Automated Natural Language Generation for Obituaries</b> got accepted for oral presentation at ICCBR 2020. The paper presents a case-based approach to automatically generate obituary of a deceased person from the information of that person given as structured input. 
</div>

**(This blog is under development)**

<!--more-->

### Problem
<div style="text-align: justify"> 
The problem statement is to automatically generate the obituary of a deceased person from given a set of features, i.e., details about that person. Here, the input is a structured representation given in <i>attribute --> value</i> pair and the output is a raw text document/paragraph summarising the input. The paper presents a Case-Based approach that dynamically generate several templates based on the features given for a target problem. The templates are extracted from a case-base developed from similar problems stored in a <i>>problem-solution</i> pair.
</div>

### Natural Language Generation
<div style="text-align: justify"> 
Let's start with a small introduction on Natural Language Generation (NLG) before we dive into Automated Obituary Generation. NLG can be broadle categorised into two different clusters: first, <b>text-to-text generation (T2T NLG)</b>; and second, <b>data-to-text generation (D2T NLG)</b>. 
</div>

- <div style="text-align: justify">As the name suggests, in <b>T2T NLG</b> our goal is to generate text from raw textual input. For example, machine translation - here we take a text document in one human language as input and produce the same content in different human language as output (see figure below). </div>

![Figure 1: T2T NLG](/assets/iccbr/t2tnlg.png)
<p style="text-align: center;"><b>Text-to-Text Natural Language Generation</b></p>

- <div style="text-align: justify">For <b>D2T NLG</b>, the input is present in more structured format, i.e., tables, graphs or JSON format. With those structured inputs we generate a textual output summarising the input values. For example, summarising an NFL match - given the scores and other details for input, generate a textual summary as the output (see figure below).</div>

<!-- D2T NLG. -->
![Figure 2: D2T NLG](/assets/iccbr/d2tnlg.png)
<p style="text-align: center;"><b>Data-to-Text Natural Language Generation</b></p>

<div style="text-align: justify"> 
A lot of things happen in between taking input and producing output, but this is what we need to know on at the abstract level to broadly differentiate between types of NLG. Generating natural language is difficult because grammar rules are very complex to understand for a computer. Also, it is challenging to automatically evaluate the texts generated from the automated system. Unlike most supervised problems, there's no class knowledge in form of labels to evaluate the performance. Apart from that, the evaluation needs to consider the accuracy, readbility and diversity of the generated texts as well.
</div>

## Introduction
<div style="text-align: justify"> 
The problem statement for this paper - automated obituary generation comes under the umbrella of <i>D2T NLG</i>. The input is a set of <i>attribute --> value</i> pairs given in JSON format and the ouput is a raw text both proivding the information about a deceased person.
</div>

![Figure 3: An Obituary](/assets/iccbr/obit.jpg){:width="500px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>An obituary</b></p>

<div style="text-align: justify"> The most basic idea for obituary generation can be a pre-defined generic template with all the attributes available as slots to be filled. But having a single template for every problem is difficult to construct for complex scenarios and result in very repetitive text outputs. On the other hand, Deep Learning (DL) based neural methods will require huge amount of labelled datasets to learn the relation between data and text for good generation. In these applications, labelled datasets can be very expensive and time consuming as they require domain experts to manually annotate the data. Moreover, DL techniques prefer readbility over accuracy and often hallucinate by producing misleading texts which are not supported by the information provided in input data <cite>[1][#1]</cite>.
</div>

<div style="text-align: justify"> 
In this case, <b>Textual Case-Based Reasoning (TCBR)</b> provides a perfect alternative to generate dynamic templates from smaller datasets (stored in a case-base in <i>problem --> solution</i> pairs) which are capable of producing diverse as well as accurate texts from the structured inputs. The TCBR cycle can be easily explained by the popular 4Rs [[2]](#2):
</div>

- In first phase, we **retrieve** similar cases to the target problem from a case-base.
- Then, we **reuse** the solution from similar cases and propose a solution for the target problem.
- Then, we **revise** the generated solution according to the requirement of target problem.
- And finally, we **retain** the newly proposed solution with the target problem in the case-base.

<!-- So after analysing a lot of obituaries from the website [Funeral-Notices](https://funeral-notices.co.uk/national) and discussing with different professionals I manually labelled 100 samples of obituaries with identified 40+ features. Since, I have only 100 labelled data that too with 40+ features, even a begineer will suggest me not to use deep learning for a generation problem (ofcourse, without transfer learning).  -->

## Proposed Framework
### Case Representation

![Figure 3: Annotated Case](/assets/iccbr/annot.png){:width="500px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>An annotated obituary</b></p>

### Similarity Measure for Retrieval

### Text Reuse

### Solution Adaptation

## Experimental Evaluation
### Case-Alignment

### Average Attribute Error

### Other Metrics
#### BLEU
#### Cosine Similarity

## Result
### Different Results

### Pearson Co-efficient

## Conclusion

## References

<a id="1">[1]</a> 
Ehudreiter: Does deep learning prefer readability over accuracy? (Jan 2019), [https://ehudreiter.com/2019/01/08/deep-learning-prefer-readability/](https://ehudreiter.com/2019/01/08/deep-learning-prefer-readability/).

<a id="2">[2]</a> 
Aamodt, Agnar, and Enric Plaza. "Case-based reasoning: Foundational issues, methodological variations, and system approaches." AI communications 7.1 (1994): 39-59.