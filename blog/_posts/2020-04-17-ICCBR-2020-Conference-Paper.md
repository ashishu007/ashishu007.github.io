---
layout: post
title: "Automated Obituary Generation"
date: 2020-04-08
desc: "This blog is a brief explanation of my recently accepted paper at ICCBR 2020"
keywords: "Blog, NLG, Papers, Textual CBR"
categories: [Blog, NLP, TCBR, NLG]
tags: [Blog, NLP, TCBR]
blog: [Blog]
excerpt_separator: <!--more-->
images: 
    - url: /assets/iccbr/annot.jpg
    - url: /assets/iccbr/atts1.jpg
    - url: /assets/iccbr/d2tnlg.jpg
    - url: /assets/iccbr/t2tnlg.jpg
    - url: /assets/iccbr/obit.jpg
icon: icon-html
---

<!-- <div style="text-align: justify">  -->
Recently, my paper titled <b>Case-Based Approach to Automated Natural Language Generation for Obituaries</b> got accepted for oral presentation at ICCBR 2020. The paper presents a case-based approach to automatically generate obituary of a deceased person from the information of that person given as structured input. 
<!-- </div> -->

**(This blog is under development)**

<!--more-->

### Problem
<!-- <div style="text-align: justify">  -->
The problem statement is to automatically generate the obituary of a deceased person from given a set of features, i.e., details about that person. Here, the input is a structured representation given in <i>attribute --> value</i> pair and the output is a raw text document/paragraph summarising the input. The paper presents a Case-Based approach that dynamically generate several templates based on the features given for a target problem. The templates are extracted from a case-base developed from similar problems stored in a <i>problem-solution</i> pair.
<!-- </div> -->

### Natural Language Generation
<!-- <div style="text-align: justify">  -->
Let's start with a small introduction on Natural Language Generation (NLG) before we dive into Automated Obituary Generation. NLG can be broadle categorised into two different clusters: first, <b>text-to-text generation (T2T NLG)</b>; and second, <b>data-to-text generation (D2T NLG)</b>. 
<!-- </div> -->

- <div style="text-align: justify">As the name suggests, in <b>T2T NLG</b> our goal is to generate text from raw textual input. For example, machine translation - here we take a text document in one human language as input and produce the same content in different human language as output (see figure below). </div>

![Figure 1: T2T NLG](/assets/iccbr/t2tnlg.jpg)
<p style="text-align: center;"><b>Text-to-Text Natural Language Generation</b></p>

- <div style="text-align: justify">For <b>D2T NLG</b>, the input is present in more structured format, i.e., tables, graphs or JSON format. With those structured inputs we generate a textual output summarising the input values. For example, summarising an NFL match - given the scores and other details for input, generate a textual summary as the output (see figure below).</div>

<!-- D2T NLG. -->
![Figure 2: D2T NLG](/assets/iccbr/d2tnlg.jpg)
<p style="text-align: center;"><b>Data-to-Text Natural Language Generation</b></p>

<!-- <div style="text-align: justify">  -->
A lot of things happen in between taking input and producing output, but this is what we need to know on at the abstract level to broadly differentiate between types of NLG. Generating natural language is difficult because grammar rules are very complex to understand for a computer. Also, it is challenging to automatically evaluate the texts generated from the automated system. Unlike most supervised problems, there's no class knowledge in form of labels to evaluate the performance. Apart from that, the evaluation needs to consider the accuracy, readbility and diversity of the generated texts as well.
<!-- </div> -->

## Introduction
<!-- <div style="text-align: justify">  -->
The problem statement for this paper - automated obituary generation comes under the umbrella of <i>D2T NLG</i>. The input is a set of <i>attribute --> value</i> pairs given in JSON format and the ouput is a raw text both proivding the information about a deceased person.
<!-- </div> -->

![Figure 3: An Obituary](/assets/iccbr/obit.jpg){:width="500px" style="display:block;margin-left:auto;margin-right:auto;"}
<p style="text-align: center;"><b>An obituary</b></p>

<!-- <div style="text-align: justify">  -->
The most basic idea for obituary generation can be a pre-defined generic template with all the attributes available as slots to be filled. But having a single template for every problem is difficult to construct for complex scenarios and result in very repetitive text outputs. On the other hand, Deep Learning (DL) based neural methods will require huge amount of labelled datasets to learn the relation between data and text for good generation. In these applications, labelled datasets can be very expensive and time consuming as they require domain experts to manually annotate the data. Moreover, DL techniques prefer readbility over accuracy and often hallucinate by producing misleading texts which are not supported by the information provided in input data [[1]](#1).
<!-- </div> -->

<!-- <div style="text-align: justify">  -->
In this case, <b>Textual Case-Based Reasoning (TCBR)</b> provides a perfect alternative to generate dynamic templates from smaller datasets (stored in a case-base in <i>problem --> solution</i> pairs) which are capable of producing diverse as well as accurate texts from the structured inputs. The TCBR cycle can be easily explained by the popular 4Rs [[2]](#2):
<!-- </div> -->

- In first phase, we **retrieve** similar cases to the target problem from a case-base.
- Then, we **reuse** the solution from similar cases and propose a solution for the target problem.
- Then, we **revise** the generated solution according to the requirement of target problem.
- And finally, we **retain** the newly proposed solution with the target problem in the case-base.

<!-- So after analysing a lot of obituaries from the website [Funeral-Notices](https://funeral-notices.co.uk/national) and discussing with different professionals I manually labelled 100 samples of obituaries with identified 40+ features. Since, I have only 100 labelled data that too with 40+ features, even a begineer will suggest me not to use deep learning for a generation problem (ofcourse, without transfer learning).  -->

## Proposed Framework
<!-- <div style="text-align: justify"> -->
Let's discuss the proposed TCBR framework in detail now. First, I'll explain the case-base: what it contains; and how it is generated. Then, I'll explain how the solution for a new target problem is proposed. 
<!-- </div> -->

### Case Representation
<!-- <div style="text-align: justify"> -->
Our case-base contains <b>100 manually annotated</b> cases organised in problem-solution pairs. For each case: in the problem side, the information is stored in JSON format with attribute-values; and in the solution-side, the marked-up obituary is stored. The figure below shows the solution-side of a case, for problem-side you can take the tag-name as attribute and string between the tag will be the value for that attribute.
<!-- </div> -->

![Figure 3: Annotated Case](/assets/iccbr/annot.jpg)
<p style="text-align: center;"><b>An annotated obituary</b></p>

<!-- <div style="text-align: justify"> -->
These obituaries were extracted from [Funeral-Notices](https://funeral-notices.co.uk/), one of the most famous obituary publishing websites in the UK. After reading multiple obituaries, I identified around 40 features to represent an obituary and then annotated around 100 obituaries with those features. The list of identified features is shown in the figure below.
<!-- </div> -->

![Figure 3: Annotated Case](/assets/iccbr/atts1.jpg)
<p style="text-align: center;"><b>Features identified for representation of an obituary</b></p>

### Similarity Measure for Retrieval
<!-- <div style="text-align: justify"> -->
Now that we have a case-base containing some previous experience, we will apply a nearest neighbour retrieval to get the solution for similar problems solved in past. CBR works on a basic principle - <b>"similar problems have similar solutions"</b>. Like in real life when we encounter a new problem, we search our memory for the similar problems encountered in past and then we use the solution for that problem to solve the new one. Similarly, we will search for the most similar case in case-base to the new target problem using the problem-side representation. Then we will use the solution side obituary of the most similar case by replacing the tags' values with new target case values.
<!-- </div> -->

<!-- <div style="text-align: justify"> -->
Thus, for the retrieval of similar cases - we need to have a measure of similarity between cases. The first approach is straight-forward, here we match the number of features in the target problem with number of features in each case from the case-base. The first similarity measure (sim<sub>1</sub>) is defined by the equation below:
<!-- </div> -->

<!-- <img src="http://www.sciweavers.org/tex2img.php?eq=sim_%7B1%7D%20%3D%20%7Cq%20%5Cbigcap%20c%7C&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0" style="text-align: center;" border="0" alt="sim_{1} = |q \bigcap c|" width="118" height="29" /> -->

<div style="text-align: center;">
<span class="math">sim<sub>1</sub> = |q &#8898; c|</span>
</div>

<!-- <div style="text-align: justify;"> -->
where <i>q</i> is the list of attributes in target problem and <i>c</i> is the list of attributes in each case from case-base.
<!-- </div> -->

<!-- <div style="text-align: justify;"> -->
There can be a problem with the above equation where the target case has fewer features than the case retrieved from the case-base. Let's take an example where the target case has only 10 attributes out of a possible 40. In that scenario, cases with more than the 10 attributes will also have the same similarity score as cases with the exact 10 features. To counter this problem, we use a different similarity measure (sim<sub>2</sub>), which is the <b>Jaccard Similarity Coefficient (J)</b> described below:
<!-- </div> -->

<div style="text-align: center;">
<span class="math">sim<sub>2</sub> = J(q, c) = |q &#8898; c| &frasl; |q &#8899; c| </span>
</div>

### Text Reuse
<!-- <div style="text-align: justify;"> -->
Now that we can rank all the cases in case-base according to their similarity to target problem, we will use their solution to propose new solution for the target problem. Here, we propose two alternate case-representation methods for the retrieval of cases:
<!-- </div> -->

- **Basic**: retrieving the whole case as one entity; and
- **Component**: retrieving cases as 3 different components.

<!-- <div style="text-align: justify;"> -->
From the figure above showing annotated obituary, we can see that the three components are marked-up with separate "component tags". For basic retrieval, whole obituary is retrieved as one entity thus ignoring the component tags. While for component retrieval, all three components are retrieved separately. Then the retrieved case's text is reused by replacing the each attribute's value with the attribute's value from the target problem. The new modified text is the solution generated by CBR system. In case of component retrieval, we combine the texts generated for each component separately to propose the final solution.
<!-- </div> -->

### Solution Adaptation
<!-- <div style="text-align: justify;"> -->
The proposed solution may contain some general mistakes such as: referring to the deceased person with male pronoun even if the gender of the person is female or vice-versa; or adding an attribute which is not given in the target problem. These kinds of error occur because of the fact that the proposed solution is generated by simply reusing the text from solution-side of the retrieved case after replacing the attributes' values.
<!-- </div> -->

<!-- <div style="text-align: justify;"> -->
To tackle the gender problem, we apply a rule-based adaptation process where each generated text is checked against the gender of the deceased person. If a pronoun with different gender is found in the text, it is replaced with the same pronoun of the deceased person's gender. For the extra attributes problem, we simply replace the attribute's value with a blank for any attribute which is not given in the target problem.
<!-- </div> -->

<!-- ## Experimental Evaluation
### Case-Alignment

### Average Attribute Error

### Other Metrics
#### BLEU
#### Cosine Similarity -->

## Result
<!-- ### Different Results -->

<!-- ### Pearson Co-efficient -->
Since, we have two different similarity measure with two different case-representations for the retrieval of similar cases - we have total four versions of our CBR system. A nomeclature of these four systems is shown in the table below:

|  | **Basic** | **Component** |
| :---         |     :---:      |          ---: |
| <span class="math">sim<sub>1</sub></span> | BS1   | CS1   |
| <span class="math">sim<sub>1</sub></span> | BS2   | CS2   |

## Conclusion

## References

<a id="1">[1]</a> 
Ehudreiter: Does deep learning prefer readability over accuracy? (Jan 2019), [https://ehudreiter.com/2019/01/08/deep-learning-prefer-readability/](https://ehudreiter.com/2019/01/08/deep-learning-prefer-readability/).

<a id="2">[2]</a> 
Aamodt, Agnar, and Enric Plaza. "Case-based reasoning: Foundational issues, methodological variations, and system approaches." AI communications 7.1 (1994): 39-59.