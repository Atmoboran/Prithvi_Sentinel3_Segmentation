# 🌍 Fine-Tuning the Prithvi EO Foundation Model on Sentinel-3 Data

This repository demonstrates how to fine-tune the **Prithvi EO 2.0 Foundation Model** (developed by IBM and NASA) using **TerraTorch** ([GitHub link](https://github.com/IBM/terratorch)) on **Sentinel-3 SLSTR** satellite imagery.

The goal is to assess how well Prithvi EO performs when applied to **coarser resolution data**, different from the Sentinel-2 HLS dataset it was originally pre-trained on.

---

## 📌 Project Summary

- **Task**: Binary segmentation — classifying each pixel as either *clear-sky ocean* or *everything else*.
- **Model**: [Prithvi EO 2.0 Foundation Model](https://arxiv.org/abs/2412.02732), fine-tuned with [TerraTorch](https://github.com/ibm/terratorch).
- **Study focus**: Evaluate the performance impact of using the *pre-trained encoder* vs. training the encoder from scratch.
- **Finding**: The pre-trained encoder improved segmentation performance — *even though it was trained on higher resolution, land-only Sentinel-2 data with different spectral bands*.
- **Data**: Sentinel-3 SLSTR patches centered around Spain and Portugal.
- **Input**: 224×224×6 reflectance patches (SLSTR channels 2,2,3,5,5,6 — due to a mistake; originally intended to use channels 1,1,2,3,5,6).
- **Output**: 224×224×1 binary masks for clear-sky ocean (created using a NaiveProb cloud masking algorithm — not included due to restrictions).

---

## 📂 Repository Structure

- `prithvi_S3_CM_datapreproc.ipynb`:  
  Downloads and organizes the dataset from a shared Google Drive link and prepares the data structure required for TerraTorch.

- `prithvi_S3_CM_model_training_eval.ipynb`:  
  Defines the model, trains it on Sentinel-3 data, and evaluates performance.

- `prithvi_S3_investigations_slides.pdf`:  
  A slide deck summarizing methodology, setup, and findings. Includes visuals and metrics for performance comparison.

---

## 📥 Dataset

The dataset is not generated in this repository. It is available for download via Google Drive:

> 📎 **[Dataset Download Link](https://drive.google.com/file/d/1JeY917uXpGrHTyuWLvA5A8n4VG2us8gs/view?usp=sharing)**

⚠️ *Note: The cloud masks were created using a custom NaiveProb algorithm that cannot be redistributed.*

---

## 🧠 Background

This work was conducted by **Boran Frank** during a **three-month internship** at the **Copernicus Programme Office** of **EUMETSAT**, under the supervision of **Anna-Lena Erdmann**. It explores the flexibility of large-scale foundation models like Prithvi EO and how they generalize to different resolutions and sensor types in Earth observation.

---

## 🛠 Requirements

Use of GPU/TPUs. You can run the notebooks directly in [Google Colab](https://colab.research.google.com/) with minimal setup. Go to "Runtime" -> "Change runtime type" -> Select "T4 GPU".

---
