+++
date = '2025-02-18T00:17:51-06:00'
draft = false
title = 'RAG and &#34;Agentic AI&#34;'
description = "Checking-in on two hot areas of AI in 2025..."
type = 'post'
tags = ["ai", "tech", "devops", "enterprise-it"]
+++
[Retrieval Augmented Generation](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) (RAG) and [Agentic AI](https://en.wikipedia.org/wiki/Agentic_AI) (sometimes referred to as “*autonomous agents*”) are two prominent trends in the AI landscape that I keep getting asked questions about from colleagues. These things build on established large [language model](https://en.wikipedia.org/wiki/Large_language_model) (LLM) techniques, but add new dimensions of capabilities and behavior. Below is an overview of each concept and how they’re being used or may be used in real-world scenarios.   

## Retrieval Augmented Generation (RAG)

All RAG is, at its core, is [generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence) being used with External Data: RAG pairs large language models (like GPT-3.5, GPT-4, etc.) with an external data retrieval step. Instead of *only* relying on the language model’s internal parameters (its “memorized” knowledge), RAG “*looks up*” data from external databases, document stores, APIs, or web-based sources.  

This results in reduced "[hallucinations](https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence))", because RAG can mitigate fabrication of details by LLM models.  By anchoring responses off of actual documents or data sources, you improve the quality of LLM responses. You can also tailor the AI to a *specific domain* without retraining the entire model. For example, if you have a proprietary knowledge base for a legal firm, you can store that in a vector database (e.g., [Pinecone](https://www.pinecone.io), [FAISS](https://github.com/facebookresearch/faiss), etc.) or a search index (e.g., ElasticSearch) and have the model retrieve from it on-demand.  

Perhaps the biggest "get" with RAG solutions is that information the LLM is using is more *up-to-date*.  Large language models are typically trained on data up to a certain cutoff date in the past. RAG can tap into real-time sources—like current news or documents—to provide timely answers.  

## Agentic AI

Agentic AI involves moving from Simple Chatbots to Autonomous “*Agents*”: it goes beyond just answering questions or generating text. It acts as a proxy, or “*Agent*”, capable of making decisions or taking actions based on goals or instructions. This is especially useful for multi-step tasks, as Agents can plan how to achieve a goal (e.g., “Research X, then write a summary, then send an email with the results”) and then break that down into a sequence of tasks. They might even iterate and refine steps using feedback loops.  This gives AI users an opportunity to automate complex workflows.

Where traditional LLM chatbots might provide only a single response, *Agentic AI* tries to accomplish an objective by calling external tools or APIs as-needed—such as scheduling a meeting, sending an email, or querying a database—often without constant human oversight.  This also means that older "*Virtual Assistants*" solutions (such as Siri, Alexa, etc) can get smarter.  Traditional Virtual Assistants to-date have just answered questions or could only play media; however, an agentic AI might proactively plan your day, prioritize tasks, book appointments, or reorder supplies, making decisions based on your preferences and calendar constraints.  This is why Apple, Google, and Amazon are moving to integrate *Agentic AI* features into their Virtual Assistants.  

Still other *Agentic AI* possibilities include data analysis "Agents" performing trending analysis, or logging reviews, to identify anomalies and trigger specific alerts.  In DevOps and cloud infrastructure, these kinds of *Agentic AIs* could monitor system metrics and even react via pre-approved *self-healing* actions that it's authorized to take (e.g. restarting a service, applying a configuration change, etc) in order to resolve the issue without waiting on manual intervention.  

## The Takeaway

A lot is going to happen here in 2025 in the further development of RAG and *Agentic AI* concepts, and ethical and safety risks should continue to be a part of the conversation (as well as human-in-the-loop considerations); however, we're [already seeing](https://openai.com/index/introducing-operator/) solutions arrive that leverage these things together with recent reasoning LLMs that leverage [chain-of-thought](https://en.wikipedia.org/wiki/Prompt_engineering#Chain-of-thought) (CoT) in their operations.  

As these technologies advance this year, expect to see more AI-driven tools seamlessly retrieving information from specialized sources and autonomously navigating complex tasks. The combination of RAG and agentic capabilities opens new avenues for streamlined workflows, productivity gains, and (eventually) sophisticated “*virtual teammates*” across industries. However, it also underscores the importance of robust data governance, safety checks, and oversight so that organizations (and society at large) gain the benefits without exposing themselves to undue risk.  

I know the response to AI in my own industry of devops and IT spans the range, from excitement to worry. But I would advise my colleagues near and far: continue learning about this stuff. because it's [like I wrote here last year](https://julianwest.me/Blog/thoughts-on-ai-dec/): "***It's not AI that will take your job: it's people leveraging AI that will take your job***."