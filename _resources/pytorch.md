---
layout: page
title: Setting Up a PyTorch Environment
description: A reproducible setup for PyTorch development on Linux, macOS, and Windows
img: assets/img/pytorch.png
importance: 1
category: Toolsets and Frameworks
related_publications: false
---

This resource walks you through setting up a clean and reproducible **PyTorch development environment**, with support for CUDA (GPU) if on Windows and Linux, or MPS on Mac, Python versioning, and essential libraries for generative AI research.

## ⚙️ Installation Steps

# Step 1: Ensure Python 3.11 or above is installed. 
This guides assumes Python 3.11. Install Python 3.11 according to the instructions in this link: https://www.python.org/downloads/release/python-3110/

# Step 2: Installing PyTorch Locally
After installing Python 3.11, either create a new virtual environment, or start downloading PyTorch to the main environment. 95% of my projects use PyTorch, so I directly installed PyTorch in my main Python environment. Choose which approach depending on your project and coding needs.

## Windows/Linux Install (CUDA):
For a Cuda-based install of PyTorch, make sure to first download and install Cuda. Cuda is a framework that allows GPU communication between machine learning libraries and the code for full GPU utilization. 

Download the Cuda version that is most compatible with your current GPU architecture. Follow the link [here][https://en.wikipedia.org/wiki/CUDA#GPUs_supported] to find the most compatible Cuda version build for your GPU. For instance, my machine has a NVIDIA RTX 4070 and I installed Cuda 11.8.

For further installation instructions and configuration, follow the instructions according to the appropriate Cuda version as seen [here][https://docs.nvidia.com/cuda/index.html] (this link goes to the latest version of Cuda, make sure you are looking at your version of Cuda).

**Note: This step is the most important step for Cuda-based installs. An incorrect driver version or incompatiblity with the GPU can cause issues with PyTorch, or incomplete GPU utilization**

When you have have confirmed that Cuda is installed, go to https://pytorch.org/get-started/locally/ and select the architecture that matches your machine. As soon you visit the page, PyTorch will pick what it thinks is the best bundle for your machine.

Follow the install instructions on the page and install any additional required dependencies needed by architecture. Some Linux builds require installation of specific drivers which can be found in the instructions [here][https://docs.nvidia.com/cuda/index.html]

# macOS Install (MPS Metal): 
Follow the install instructions on this page [here][https://docs.nvidia.com/cuda/index.html] and make sure to pick Mac as the OS.

# Step 3: Verify Installation 
Run the code below to check that PyTorch has successfully installed and can access the GPU


{% raw %}

```python
import torch

# if Windows/Linux
print(torch.cuda.is_available()) # prints True if PyTorch has access to the Cuda GPU

# if macOS
print(torch.backeds.mps.is_available()) # prints True if PyTorch has access to the Mac's metal GPU

```

{% endraw %}
