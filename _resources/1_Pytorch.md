---
layout: page
title: Setting Up a PyTorch Environment
description: A reproducible setup for PyTorch development on Linux, macOS, and Windows
img: assets/img/12.png
importance: 1
category: resources
related_publications: false
---

This resource walks you through setting up a clean and reproducible **PyTorch development environment**, with support for CUDA (GPU) if on Windows and Linux, or MPS on Mac, Python versioning, and essential libraries for generative AI research.

---

## 🧰 Recommended Setup Tools

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/anaconda-logo.png" title="Anaconda (Windows/Linux)" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/mac.png" title="Nightly Build (MacOS)" class="img-fluid rounded z-depth-1" %}
  </div>
</div>

---

## ⚙️ Installation Steps

# Step 1: Ensure Python 3.10 or above is installed. This guides assumes Python 3.10 

# Step 2 (Windows/Linux):

# Step 2 (macOS):

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
