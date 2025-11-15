# Stable Diffusion 3 Inpainting, Text-to-Image, and Image-to-Image Generation in Keras Hub

This repository contains the implementation and report materials for an assignment exploring **Stable Diffusion 3 (SD3)** via **Keras Hub**.  
The work focuses on three main capabilities:

1. **End-to-end inpainting** using the official SD3 inpaint model.  
2. **Prompt flexibility analysis**: how much the inpainted result changes when only the prompt and sampling parameters are modified.  
3. **Text-to-image (T2I)** and **image-to-image (I2I)** generation using SD3 models provided through Keras Hub.

Experiments were run on an **NVIDIA RTX 4090** using **TensorFlow** as the backend.

---

## 🔧 Tasks Covered

- Use the **Stable Diffusion 3 inpaint model** from Keras Hub:  
  <https://keras.io/keras_hub/api/models/stable_diffusion_3/stable_diffusion_3_inpaint/>

- Investigate:
  - How much **prompt wording**
  - **Guidance scale**
  - **Edit strength (noise level)**
  
  affect the final inpainted image, while keeping the input image and mask fixed.

- Use **Stable Diffusion 3 for:**
  - **Image-to-image** generation
  - **Text-to-image** generation  

  following the Keras Hub guide:  
  <https://keras.io/keras_hub/guides/stable_diffusion_3_in_keras_hub/>

---

## 📘 Code Availability

All experiments are implemented in two Google Colab notebooks:

- **Inpainting + Prompt Flexibility Notebook**  
  👉 [Click to open Inpainting Code](https://colab.research.google.com/drive/1EAMp3BEaoMqgIIuyQWwDQ5vJ1wxTUbGa?usp=sharing)

- **Text-to-Image + Image-to-Image Notebook**  
  👉 [Click to open Image-to-Image & Text-to-Image Code](https://colab.research.google.com/drive/1P5UbNPv4bJ4VLns5IHdMf4nNPJAkFrQE?usp=sharing)

---

## 🧠 Methodology (Summary)

### Environment

- **GPU:** NVIDIA RTX 4090  
- **Resolution:** 512 × 512  
- **Precision:** float16 weights for SD3 backbone  
- **Backend:** TensorFlow with Keras / Keras Hub  
- **Models used:**
  - `StableDiffusion3Backbone`
  - `StableDiffusion3Inpaint`
  - `StableDiffusion3TextToImage`
  - `StableDiffusion3ImageToImage`

### Inpainting Pipeline

- Input image: astronaut standing on a tree-lined path  
  - File: `astronaut_input_image.png`  
- Foreground (astronaut) preserved by a **binary mask**.  
  - Masks initially generated via Gemini 2.5 Image, then refined manually.  
- Preprocessing:
  - Resize to **512×512**
  - Normalize to **[-1, 1]**
  - Boolean mask for editable region
- Sampling parameters:
  - Guidance scale ∈ {5.0, 7.5, 10.0}
  - Strength ∈ {0.4, 0.6, 0.8}
  - Diffusion steps: up to **2000** in some runs for higher fidelity.

### 📦 Repository Name
`stable-diffusion3-keras-hub-inpainting-t2i-i2i`

### 📝 Description
Experiments with **Stable Diffusion 3** in **Keras Hub**, including:
- End-to-end **inpainting**
- **Prompt flexibility** analysis
- **Text-to-image** (T2I) generation
- **Image-to-image** (I2I) stylization  
using SD3 backbone, inpaint, and generative pipelines.

---
# 📚 Citation

If you use this repository, any code snippet, or take help from the explanations, **please cite**:

```bibtex
@misc{ameen2025detectingaigeneratedimagesdiffusion,
      title={Detecting AI-Generated Images via Diffusion Snap-Back Reconstruction: A Forensic Approach}, 
      author={Mohd Ruhul Ameen and Akif Islam},
      year={2025},
      eprint={2511.00352},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2511.00352}, 
}
