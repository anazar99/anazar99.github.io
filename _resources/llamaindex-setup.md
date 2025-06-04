---
layout: page
title: Setting Up LlamaIndex with Hugging Face and Ollama
description: A unified setup for local and cloud-based LLMs using LlamaIndex
img: assets/img/llamaindex-logo.png
importance: 5
category: Toolsets and Frameworks
---

**LlamaIndex** (formerly GPT Index) is a powerful framework that bridges external data sources (e.g., PDFs, databases, APIs) with LLMs. It supports local models (like **Ollama**) and cloud-hosted models (like those on **Hugging Face**) via unified interfaces.

This guide walks through setting up LlamaIndex for both **Hugging Face LLMs** and **local Ollama models**, ending with a full code example.

## 🧠 Why Use LlamaIndex?

LlamaIndex is a powerful and modular framework for building LLM-based systems that require structured reasoning, document retrieval, or agent orchestration. It stands out because of its **granular control**, **clean abstractions**, and **seamless support for both local and hosted models**.

Here are key reasons to use LlamaIndex in your generative AI workflows:

---

### ✅ Fine-Grained Control over Prompting & Logic

LlamaIndex offers high **granularity** over how prompts are constructed, executed, and chained. You can:

- Customize **prompt templates** for specific submodules (e.g., summarization, synthesis, query generation)
- Adjust **token limits**, **inference parameters**, and **intermediate steps** without leaving the high-level framework
- Debug or trace reasoning pipelines at the **sub-prompt level**, which is harder with end-to-end LLM frameworks

---

### 🤖 Built-In Agent Management

LlamaIndex has a straightforward yet extensible **agent management system**:

- Define task-specific agents (e.g., planner, retriever, responder)
- Integrate tools, memory, and logic routing in a few lines
- Ideal for building modular, multi-agent environments without writing scaffolding code from scratch

It’s an excellent fit for **research workflows**, **academic prototypes**, and **production-grade agents** alike.

---

### 🔍 Powerful RAG (Retrieval-Augmented Generation)

LlamaIndex was originally designed for **document-indexed LLMs** and excels in:

- Ingesting and indexing structured/unstructured data (e.g., PDFs, databases, APIs)
- Building retrieval pipelines using vector stores like FAISS, Qdrant, Weaviate
- Injecting context into LLMs at runtime via clean abstractions (`QueryEngine`, `Retriever`, `Index`)

Whether you're querying large corpora or chaining retrieval with reasoning, LlamaIndex gives you full control.

---

### 🔁 Backend Agnostic (Ollama, OpenAI, Hugging Face, etc.)

You can swap backends without rewriting logic:

- Run **Ollama** locally for privacy and speed
- Use **Hugging Face** models for open-source access
- Integrate **OpenAI** or **Anthropic** for production-grade LLMs

Everything works under a unified API.

---

### 📐 Extensibility and Modularity

LlamaIndex is easy to extend:
- Plug in your own retrievers, tools, tools, memory modules
- Compose advanced behaviors using **runnable chains**, **callbacks**, and **multi-modal interfaces**

---

### 🚀 TL;DR: Why LlamaIndex?

| Feature                  | Benefit                                                 |
|--------------------------|----------------------------------------------------------|
| Granular prompt control  | Customize how each part of the system reasons            |
| Easy agent setup         | Create modular, explainable agent workflows              |
| RAG pipelines            | State-of-the-art retrieval and context injection         |
| Backend flexibility      | Use local or hosted models with the same codebase        |
| Developer friendly       | Ideal for experimentation, debugging, and fast iteration |



---

## 📦 Step 1: Install LlamaIndex

Use pip to install the base library and Ollama + Hugging Face extensions:

```
pip install llama-index llama-index-llms-ollama llama-index-llms-huggingface llama-index-embeddings-huggingface
```

If you're using vector stores or file loaders, you may also want:

```
pip install llama-index-readers-file llama-index-vector-stores-faiss llama-index-vector-stores-chroma
```

## 🐏 Step 2a: Use Ollama-Backed LLMs Locally
Ensure that Ollama is installed and running ([see the Ollama setup page](https://anazar99.github.io/resources/ollama-setup/)). Then use:

```python
from llama_index.llms.ollama import Ollama

llm = Ollama(model="llama3.2", request_timeout=120.0)
```

You can substitute "llama3.2" with any model supported by Ollama, such as "mistral" or "gemma".

## 🧠 Step 2b: Set Up Hugging Face API Key
If using hosted models from Hugging Face (e.g., Falcon, Mistral, LLaMA 2), create a HuggingFace accoount and generate an access token to place in your environment (.env) file (optional) to be used to pull specific models directly from HuggingFace if you choose to follow that route. You can get your token from [HuggingFace](https://huggingface.co/settings/tokens).

```python
from llama_index.llms.huggingface import HuggingFaceLLM

llm = HuggingFaceLLM(
    model_name="tiiuae/falcon-7b-instruct",
    context_window=2048,
    max_new_tokens=256,
    generate_kwargs={"temperature": 0.7},
)
```

## 🧪 Step 4: Creating a Prompt Template and Calling the LLM

Here’s a full example of defining a custom prompt and invoking the LLM:


```python
from llama_index.llms.ollama import Ollama
from llama_index.prompts import PromptTemplate

# Instantiate the model (local)
llm = Ollama(model="llama3", request_timeout=120.0)

# Define a custom prompt template
template = """
{Add your system template here that instructs the LLM on how to answer given the specific context and domain}

### Question: {input}
"""

prompt_template = PromptTemplate(template)

# Use the LLM
response = llm.complete(prompt_template.format(input="What is retrieval-augmented generation?"))
print(response)
```