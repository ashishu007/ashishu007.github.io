---
layout: post
title: "Microsoft's T-NLG: The biggest pre-trained Transformer till now"
date: 2019-02-16
desc: "This blog talks about my views on the future of Transfer Learning in NLP"
keywords: "Blog, NLP, Transfer Learning, Transformers"
categories: [Blog, NLP]
tags: [Blog, NLP]
blog: [Blog]
excerpt_separator: <!--more-->
images: 
    - url: /assets/T-NLG_LM.jpg
icon: icon-html
---

**New Transformer**

Recently, Microsoft announced their new language model named Turing-NLG (T-NLG) with **17 billion parameters**. It's a 78 layers deep Transformer model trained on text from the internet that outperformed state-of-the-arts (SOTA) on various NLP tasks such as Summary Generation and Question Answering. Just for a comparison, previous SOTA (Megatron-LM by Nvidia) has 8B parameters while other recent breakthroughs such as BERT (by Google) and GPT-2 (by Open AI) have 340M and 1.5B parameters respectively.

**T-NLG vs Megatron-LM**

Microsoft's T-NLG used 256 Nvidia GPUs for the training while the time taken for training is not mentioned. Nvidia's Megatron-LM had used 1024 GPUs for training but with few engineering in parallelism helped Microsoft achieve better performance with less GPUs (still 256, each with 32GB memory).

**Scale or Algorithmic Innovation**

The scale of these pre-trained models makes me wonder if, the big factor for performance gain will come from the scale (training data and computing power) or algorithmic innovations. Since the wave of transfer learning in NLP, BERT was one of the most innovating breakthrough to introduce something different for performance gain by using masked language model and sentence pair prediction for pre-training task. Else, other models are based on vanilla Transformers with deeper layers of self-attention and feedforward network trained on more data with extra GPUs.

Here is a comparison of parameters in different pre-trained NLP models used for transfer learning. 

![Figure 1: Parameters in different NLP breakthroughs](/assets/T-NLG_LM.jpg)

Image courtesy: Microsoft.

**Future of Transfer Learning in NLP**

Number of parameters in pre-trained NLP models
All these huge models are developed by big companies in AI research. I wonder what will happen if all of a sudden they start commercialising their models and the pre-trained models are no longer available in public domain. Then what will happen? Will we go back to using less accurate systems or just expect them to keep open-sourcing there findings.

Thoughts?

<a href="https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/">Link to Microsoft's T-NLG blog</a>