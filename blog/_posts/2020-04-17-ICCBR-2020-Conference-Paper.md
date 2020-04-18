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
    - url: /assets/wec.png
    - url: /assets/acc.png
    - url: /assets/mf1.png
icon: icon-html
---

Recently, my paper titled **Case-Based Approach to Automated Natural Language Generation for Obituaries** got accepted for oral presentation at ICCBR 2020. 

**(This blog is under development)**

<!--more-->

## Introduction
The paper presents is an outcome of the project I am working as RA during my PhD. Luckily, the project closely aligns to my PhD goal as well. The problem statement in this project is that given a set of features, i.e., details about the deceased person, automatically generate the obituary of that person. Here, the input is a structured representation given in *attribute --> value* pair and the output is a text document/paragraph summarising the input.

The paper presents a Case-Based approach that generates dynamic template based on the required of a target problem. The templates are extracted from a case-base (or knowledge-base) developed from previous information in stored in *cases* or *problem-solution* pair.

## Why CBR
Now-a-days, we are seeing a huge shift in AI tasks where every problem is being solved by novel neural methods. NLG is no exeception! There has been a lot of developments in the direction of using neural methods for text generation from tabular representations. But the main drawback that comes with these deep learning techniques is the huge requirement of labelled datasets. In case of such real-world applications, getting labelled dataset is very expensive as they are domain specific (not any public dataset used in academic research) and require domain experts to label the data. 

So after analysing a lot of obituaries from the website [Funeral-Notices](https://funeral-notices.co.uk/national) and discussing with different professionals I manually labelled 100 samples of obituaries with identified 40+ features. Since, I have only 100 labelled data that too with 40+ features, even a begineer will suggest me not to use deep learning for a generation problem (ofcourse, without transfer learning). 

## Proposed Framework
### Case-Base

### Retrieval Method

### Similarity Measure

## Experimental Evaluation
### Case-Alignment

### Average Attribute Error

## Result
