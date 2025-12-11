# Text-Guided Sketch-to-Image Diffusion with LoRA Fine-Tuning and GAN Baselines

This repository contains the code and experiments for:

> **Text-Guided Sketch-to-Image Diffusion with LoRA Fine-Tuning and GAN Baselines**

We combine **Stable Diffusion v1.5** with **LoRA fine-tuning** on sketch datasets and compare it against a **Pix2Pix GAN baseline** on Edges2Shoes.

The project uses:

- **Stable Diffusion v1.5** (text-to-image backbone)
- **LoRA** for parameter-efficient fine-tuning on:
  - SketchyCOCO (object-level)
  - SketchyCOCO (scene-level)
  - FSCOCO
- **Pix2Pix U-Net + PatchGAN** for Edges2Shoes as a GAN baseline
- **FID & Inception Score** for quantitative evaluation

> All core code is in the notebook: **`Gen_ai_final.ipynb`**  
> The project is designed to run primarily on **Google Colab (L4 GPU)**.

---

## 🔍 Overview

We address the task of **sketch-to-image generation** under textual guidance:

- Input: **sketch** (edge drawing or rough sketch) + **text prompt/caption**
- Output: **photorealistic image** consistent with both the sketch and text

We explore:

1. How far **LoRA-fine-tuned Stable Diffusion** can go with sketch conditioning.
2. How it compares against a **GAN baseline (Pix2Pix on Edges2Shoes)**.
3. How performance varies across **three datasets**:
   - **SketchyCOCO** (object & scene subsets)
   - **FSCOCO**
   - **Edges2Shoes**

---

## 📂 Project Structure

A typical structure (you can adapt to your repo) is:

```text
.
├── code.ipynb                # Main end-to-end notebook
├── checkpoints/
│   ├── lora_object_unet/             # SketchyCOCO object LoRA
│   ├── lora_scene_unet/              # SketchyCOCO scene LoRA
│   ├── lora_fscoco_unet/             # FSCOCO LoRA
│   ├── edges2shoes_gan/              # GAN checkpoints (U-Net + PatchGAN)
│   └── edges2shoes_pix2pix/          # Pix2Pix training checkpoints
├── imgs/                             # Optional: sample outputs for README
│   ├── sketchycoco_example.png
│   ├── fscoco_example.png
│   └── edges2shoes_example.png
└── README.md
