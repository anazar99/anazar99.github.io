---
layout: page
title: LLM & ML Architectures — Background Knowledge
description: Foundational concepts and architectures in modern machine learning and generative AI
img: assets/img/llm-architecture.png
importance: 2
category: Introductions
---

Understanding the architectural foundations behind Large Language Models (LLMs) and other modern deep learning systems is essential for working with generative AI. This page summarizes key models, techniques, and landmark papers that have shaped the field — from attention mechanisms to transformer backbones and multi-modal fusion networks.

---

## 🧠 Core Concepts to Understand

Before diving into complex generative systems, it’s important to be grounded in the following fundamental architectures and techniques:


### **Feedforward Neural Networks (FNNs)**  
The simplest form of neural network where data flows in one direction — from input to output — through fully connected layers. Each neuron applies a weighted sum followed by a non-linear activation (e.g., ReLU). FNNs are foundational but limited in handling spatial or sequential data.


### **Convolutional Neural Networks (CNNs)**  
Primarily used for image and spatial data. CNNs apply filters (kernels) that scan across input features to detect local patterns (e.g., edges, textures). They reduce dimensionality while preserving spatial hierarchies and are widely used in vision-based generative models (like GANs or image-conditioned transformers).



### **Recurrent Neural Networks (RNNs) & Long Short-Term Memory Networks (LSTMs)**  
Designed for sequential data such as time series or language. RNNs maintain a hidden state that updates as input progresses through time. LSTMs (Long Short-Term Memory networks) enhance RNNs by incorporating gates that regulate memory, solving the vanishing gradient problem and enabling longer-term dependencies.



### **Transformers**  
The current foundation of most modern generative AI systems, including LLMs. Transformers use **self-attention** to process all input tokens in parallel (not sequentially) while still modeling dependencies. Their encoder-decoder structure enables powerful sequence modeling, both for understanding (e.g., BERT) and generation (e.g., GPT).



### **Self-Attention Mechanisms**  
A technique that lets a model dynamically weight the importance of different parts of the input relative to each token. For example, in a sentence, a word like “it” may attend to “car” to resolve reference. Self-attention allows models to capture contextual relationships at any distance.



### **Positional Encoding**  
Since transformers process sequences in parallel, they need a way to encode **order**. Positional encodings inject sequence position information into input embeddings (using sinusoidal functions or learned vectors) so that the model understands "what comes first" or "what follows what."


### **Fine-tuning and Transfer Learning**  
Instead of training from scratch, models pre-trained on large corpora are adapted to specific tasks by fine-tuning. This enables efficient learning with smaller datasets and improves generalization. Transfer learning is a key enabler of modern LLM applications in new domains.



### **Prompt Engineering and Instruction Tuning**  
For LLMs, performance can be shaped by the way inputs (prompts) are structured. Prompt engineering involves crafting inputs that guide the model to desirable outputs. Instruction tuning further enhances this by fine-tuning models on prompt–response pairs that follow task instructions — enabling more robust, zero-shot behavior.

---

## 📚 Foundational & Emerging Papers

| Title | Authors | Summary |
|-------|---------|---------|
| [Attention Is All You Need (2017)](https://arxiv.org/abs/1706.03762) | Vaswani et al. | Introduced the Transformer architecture using self-attention, the foundation for all major LLMs. |
| [BERT (2018)](https://arxiv.org/abs/1810.04805) | Devlin et al. | Proposed masked language modeling and bidirectional context encoding. |
| [GPT-3 (2020)](https://arxiv.org/abs/2005.14165) | Brown et al. | Demonstrated that large transformer models can perform few-shot tasks with minimal tuning. |
| [Perceiver IO (2021)](https://arxiv.org/abs/2107.14795) | Jaegle et al. | General-purpose model for arbitrary modality inputs. |
| [Segment Anything (2023)](https://arxiv.org/abs/2304.02643) | Kirillov et al. | Vision foundation model for universal image segmentation. |
| [Large Language Models: A Survey (2023)](https://arxiv.org/abs/2402.06196) | Minaee et al. | A general survey on LLMs. |
| [A Cognitive Review of LLMs (2023)](https://osf.io/preprints/osf/m6gcn) | Akyürek et al. | Reviews LLM capabilities through a cognitive science lens, covering reasoning, memory, and abstraction. |
| [Igniting Language Intelligence: The Hitchhiker's Guide From Chain-of-Thought Reasoning to Language Agents (2023)](https://arxiv.org/abs/2311.11797) | Zhang et al. | Survey of LLMs with Chain-of-Thought Reasoning and Language Agents. |
| [Generative Agents: Interactive Simulacra of Human Behavior (2023)](https://arxiv.org/abs/2311.05232) | Park et al. | Demonstrates multi-agent simulation with memory and planning, showing emergent social behavior from LLMs. |
| [Evaluating Large Language Models: A Comprehensive Survey](https://arxiv.org/abs/2310.19736) | Guo et al | Survey on evaluation techniques of LLMs | 
| [Large Language Models Meet Computer Vision: A Brief Survey (2023)](https://arxiv.org/abs/2311.16673) |  Hamadi | Survey on Visual LLMs | 
|[At the Dawn of Generative AI Era: A Tutorial-cum-Survey on New Frontiers in 6G Wireless Intelligence (2024)](https://arxiv.org/abs/2402.18587) | Celik et al. | Comprehensive survey on generative AI models and architectures.
| [Introducing Visual Perception Token into Multimodal Large Language Model (2025)](https://arxiv.org/abs/2502.17425) | Yu et al. | Enhancing visual mutlimodal LLMs with a visual token | 

---

## 🔍 Architectures at a Glance

<div class="row">
  <div class="col-sm mt-1 mt-md-0">
    {% include figure.liquid path="assets/img/transformer-block.png" title="Transformer Encoder-Decoder" class="img-fluid rounded z-depth-1" %}
  </div>
</div>

<div class="caption">
  LLM architecture with transformer block and self-attention schematice.
</div>

---
