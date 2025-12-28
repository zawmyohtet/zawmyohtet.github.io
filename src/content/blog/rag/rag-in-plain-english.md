---
title: "RAG in plain english"
description: 'I will try to explain Retrieval-Augmented Generation(RAG) using very simple terms for beginners and non-technical people'
publishDate: 2025-07-16 20:30:00
language: 'English' 
tags: ['LLM', "RAG", "Naive RAG", "Agentic RAG"]
comment: false
---
I hope this article will be helpful for beginners trying to understand, and non-technical people looking to learn about what RAG is and how it can be helpful for their organization.

Assume

1. You and your friend are sitting together
2. Your friend ask you a question
3. You don’t know the answer yet!
4. You browse the internet and get information.
5. Based on the information you get from the internet, you answer the question in your own way!

**Yes, it is RAG.**

In this case,

- LLM(Large Language Model) = Your Brain
- Information from Internet = Knowledge
- Browsing Internet = Retrieve Knowledge

You feed the knowledge from internet to your brain. Your brain has the ability to process and generate an answer for you and your friend.

## Why we need RAG?

LLMs are trained on a large amount of data, but this data is from the past. By providing updated information, LLMs can use this information in their thinking process and give you more **relevant answers**. It will also reduce **hallucination**.

On the other hand, LLM will not know about your particular organization's internal documents, customer data, or industry-specific information.  By providing this information, it's kind of like hiring a smart person for your organization to help you with your daily chores.

## Doesn’t fine tuning work? 

Typically, it will but tt requires time and specific skillset. It may not be relevance for every organization to build a team who are capable to do so. It is an expensive job. LLMs today are already smart enough; they just require external knowledge to help in their thinking process.

## What is the basic requirement to build a RAG system?

Data is the main factor. If you feed good data, you will get better results. It is also important to choose the right model according to your need. Not all organizations require the best and most expensive models to use. Choosing the right model based on your needs will save both your compute resources and budget. Last but not least, choosing the right orchestration framework is also important. 

## Example use case

**Study partner:** Instead of just searching a broad internet, a RAG-powered AI application, based on specific course materials, could act as an intelligent tutor. Students could ask it detailed questions, get explanations tailored to specific curriculum, and even have interactive discussions to deepen understanding of the subject matter.

**Organization Internal knowledge base system:** Think about all the internal documents, procedures, and customer data within a company. Instead of sifting through countless files or struggling to remember where specific information is stored, a RAG-powered AI application could centralise this knowledge. Employees could simply ask natural language questions ("What's the updated process for submitting expense reports?" or "What are the common customer issues for Product X?"). The RAG system would quickly retrieve the most relevant information from your internal documents and provide precise answers, enabling faster decision-making and better access to institutional knowledge.

Hope this helpful!