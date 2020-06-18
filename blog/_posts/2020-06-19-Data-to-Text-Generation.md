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
    - url: /assets/iccbr/d2tnlg.jpg
    - url: /assets/iccbr/t2tnlg.jpg
icon: icon-html
---

**Under Development**

<!-- This blog gives a brief overview of **data-to-text generation** tasks in NLG.  -->
After wandering around in the vast NLP research field for some time, I finally decided to work towards **data-to-text generation** in my PhD. In this blog, I'll try to provide: a brief overview of the task's requirements; some standard public datasets available; and the evaluation metrics used for measuring the performance on these datasets.

<!--more-->

In my PhD, I have decided to focus on data-to-text generation. The main reason for choosing this topic was the part-time project I was working on in early 2020. It was a project in collaboration with an Aberdeen based startup, where I developed a Case-Based approach to **Automated Obituary Genertion**. For a given set of details about a deceased person in some structured format, the requirement was to automatically generate a natural language text summarising that information. 

By working on this project, I realised that there are many existing problems that can be explored, possibly as a PhD project, and that's how I decided to dive deeper into this topic. I'll briefly describe some of the problems I faced in this project in further sections.

<!-- We published a paper at ICCBR 2020 as an outcome of this project as well. -->


## Natural Language Generation

First, let's start with a small introduction on Natural Language Generation (NLG). In NLG, the requirement is to generate a textual output using some automated system for a given input. 

In general, automatically generating natural language is challenging because **grammar rules** are **very complex**. And also, there can be **several meaning** to **same words** in different context. 

Even after we develop a system for automated generation, it is challenging to automatically evaluate the texts generated from that automated system. Unlike most supervised problems, there's **no class knowledge** in form of labels to evaluate the performance. Here the evaluation metric should be capable of measuring: how accurate; how fluent; and how diverse are generated texts from the automated system.

Based on the input provided to the system, NLG can be broadly categorised into three different clusters: first, **text-to-text generation (T2T NLG)**; and second, **data-to-text generation (D2T NLG)**. 

### T2T NLG
As the name suggests, in **T2T NLG**, our goal is to generate text from unstructured textual input. For example, machine translation, where we take a text document in one natural language as input and produce the same content in different natural language as output.

![T2T NLG](/assets/iccbr/t2tnlg.jpg){:width="650px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Text-to-Text Natural Language Generation (T2T NLG)</b></p>

### D2T NLG
For **D2T NLG**, the input is presented in a structured format, i.e., tablular, graphical or JSON format. With this structured input, we generate a textual output summarising the input values. For example, summarising NBA match where, for given box- and line-scores as input we have to generate a textual summary of the match as the output.

![D2T NLG](/assets/iccbr/d2tnlg.jpg){:width="650px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Data-to-Text Natural Language Generation (D2T NLG)</b></p>

As I'm exploring D2T NLG in my PhD, I'll briefly discuss this task in detail in further sections.

<!-- Apart from all this, the real-world applications (such as the automated obituary generator) suffer from data related problems as well. For starter, you might **not** have **any labelled data** to start building your system. There might be requirement of **a domain expert** to manually label some data, and that may be very expensive. After some-time you might collect some labelled data as a part of your deployment process, that data should be used to refine your system.  -->

<!-- No data -->

## Subtasks in D2T NLG

## Evaluation Metrics

## Public Datasets
