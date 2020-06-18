---
layout: post
title: "Data-to-Text Generation"
date: 2020-06-16
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

This blog gives a brief overview of **data-to-text generation** tasks in NLG.

<!--more-->

## Natural Language Generation
<!-- <div style="text-align: justify">  -->
Let's start with a small introduction on Natural Language Generation (NLG) before we dive into Automated Obituary Generation. NLG can be broadle categorised into two different clusters: first, <b>text-to-text generation (T2T NLG)</b>; and second, <b>data-to-text generation (D2T NLG)</b>. 
<!-- </div> -->

- <div style="text-align: justify">As the name suggests, in <b>T2T NLG</b> our goal is to generate text from raw textual input. For example, machine translation - here we take a text document in one human language as input and produce the same content in different human language as output (see figure below). </div>

![T2T NLG](/assets/iccbr/t2tnlg.jpg){:width="650px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Text-to-Text Natural Language Generation</b></p>

- <div style="text-align: justify">For <b>D2T NLG</b>, the input is present in more structured format, i.e., tables, graphs or JSON format. With those structured inputs we generate a textual output summarising the input values. For example, summarising an NFL match - given the scores and other details for input, generate a textual summary as the output (see figure below).</div>

<!-- D2T NLG. -->
![D2T NLG](/assets/iccbr/d2tnlg.jpg){:width="650px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>Data-to-Text Natural Language Generation</b></p>

<!-- <div style="text-align: justify">  -->
A lot of things happen in between taking input and producing output, but this is what we need to know at the abstract level to broadly differentiate between types of NLG. 

Generating natural language is difficult because grammar rules are very complex to understand for a computer. Also, it is challenging to automatically evaluate the texts generated from the automated system. Unlike most supervised problems, there's no class knowledge in form of labels to evaluate the performance. Apart from that, the evaluation needs to consider the accuracy, readbility and diversity of the generated texts as well.
<!-- </div> -->


It's been 

## Types of NLG

### T2T NLG

### D2T NLG

## Subtasks in D2T NLG

## Evaluation Metrics

## Public Datasets
