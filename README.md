# AAI-521 Team 6 Final Project  
**Face Reconstruction from Partially Leaked Facial Embeddings**  
**Privacy Risk Assessment using MFR2 Dataset**

[![Colab Badge](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1JDhrlSn_LkE7rInYY54dnTzgUVGFB2dq)  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Team 6** – Sridhar Surapaneni, Sai Navyesh Pamarthi, Rohit Andani  
> **Course:** AAI-521 – Advanced Computer Vision  
> **Date:** December 2025

---

### 🚨 Key Finding (TL;DR)
Even if an attacker steals **only 30%** of a 512-dimensional facial embedding (153 numbers), they can reconstruct a face that **100% fools any face recognition system** (mAP@1 = 1.0).  
We also discovered a **simple, free defense** (+8% privacy improvement) by masking low-variance dimensions first.

---

### Project Overview

We prove that **raw facial embeddings are NOT privacy-safe**.  
Using the public **MFR2 dataset** and **InceptionResNetV1 (VGGFace2)**, we:
1. Filter full-face images with ConvNeXt (99.61% mask detection accuracy)
2. Generate 512D embeddings (intra-ID cosine gap = **0.8202**)
3. Simulate leakage by zero-masking 10%, 30%, and 50% of dimensions
4. Train a transposed-convolutional autoencoder to reconstruct 128×128 faces
5. Show perfect identity recovery even at 50% leakage
6. Propose and validate **targeted low-variance masking** as an effective defense


