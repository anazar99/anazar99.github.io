---
layout: page
title: Setting Up Ollama
description: Installing and running Ollama locally for fast access to open-source LLMs
img: assets/img/ollama-logo.png
importance: 4
category: Toolsets and Frameworks
---

**Ollama** is a lightweight tool that lets you run open-source large language models (LLMs) locally on your machine — with a single command. It's designed for easy deployment of models like LLaMA, Mistral, and others without needing to manually handle environments or dependencies.

This guide walks you through the setup process and basic usage of Ollama for local experimentation and integration into multi-modal systems or RAG pipelines.

---

## 💻 Step 1: Install Ollama

Ollama supports macOS, Linux, and Windows. Visit the official install page or follow one of the platform-specific instructions below:

- **macOS and Windows**  
Follow the instructions on [the Ollama website](https://ollama.com/download/).

- **Linux**
Run the following command on terminal.

```
curl -fsSL https://ollama.com/install.sh | sh
```
### Setup Notes:
Be aware that Ollama autoruns on your machine's startup, if you don’t want that then turn off its Autostart on the task manager on Windows, startup apps on Linux, and Ollama preferences on macOS.


## Step 2: Run Ollama
On successful install, open a terminal window or CMD prompt and type 
```
ollama -v
```
which should output the installed version of Ollama

Then run 
```
ollama serve
```
which starts the Ollama server if it has not already been started by the app runner. 

## Step 3: Pulling a Model
### Step 3a: Pulling from Ollama's Repository
The list of available models that can be pulled from Ollama's repository are found [here](https://ollama.com/search), where you can type the command below followed by the model you would like to use. In this example, I am pulling LLaMa3.2-3b. To specify specific versions of the LLM you want to use, look at the model card on the Ollama repository.

```
ollama pull llama3.2
```


### Step 3b: Pulling from HugginFace's Repository
If a model you want to try is not on Ollama's repository, you can also pull models from HuggingFace. To pull a model from HuggingFace, you must look for the **GGUF quantization version** otherwise it cannot be used by Ollama. For instance, I will be pulling the Saka 14B Arabic LLM, which is available on HuggingFace in this [model card](https://huggingface.co/tensorblock/Saka-14B-GGUF).
```
ollama pull hf.co/tensorblock/Saka-14B-GGUF:Saka-14B-Q3_K_M.gguf
```


## Step 4: Running and Testing the Model:

To run a model pulled, simply run the command below and have fun testing the LLM!

```
ollama run <pulled_model_name_from_step_3>
```

For example:
``` 
ollama run llama3.2
# OR if you want a HuggingFace model
ollama run hf.co/tensorblock/Saka-14B-GGUF:Saka-14B-Q3_K_M.gguf
```