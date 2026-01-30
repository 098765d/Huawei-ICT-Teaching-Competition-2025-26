# Cloud-Native Deep Learning with Authentic Medical Data ☁️🩺

![Platform](https://img.shields.io/badge/Platform-Huawei_Cloud_ModelArts-red)
![Task](https://img.shields.io/badge/Task-Medical_Image_Classification-blue)
![GenAI](https://img.shields.io/badge/GenAI-Reflective_Partner-purple)

> **Huawei ICT Teaching Competition 2025-26 Entry**
>
> An industry-aligned laboratory curriculum designed to transition students from "toy" datasets to real-world cloud engineering.

## 📺 Project Demo

Click the link below to watch the full instructional demonstration and pedagogical breakdown:

**[▶️ Watch: ResNet-50 Cervical Spine Classification Lab](https://www.bilibili.com/video/BV1ZP6BBvEgU/?share_source=copy_web&vd_source=f23fdab1cf57871b257305ebe143b9c2)**

---

## 📖 About This Project

This repository bridges the gap between academic theory and industrial reality. Instead of relying on simplified "toy" datasets, this laboratory challenges learners to engineer a complete Deep Learning pipeline on **Huawei Cloud ModelArts** using raw, imbalanced medical data.

**Core Objectives:**
* **Authenticity:** Shifting from clean academic data to noisy clinical X-rays.
* **Cloud Proficiency:** Migrating execution from local CPUs to distributed cloud GPUs.
* **AI Literacy:** Utilizing Generative AI strictly as a Socratic reflective partner, not a code generator.

---

## 🧠 Curriculum Architecture

The laboratory follows a two-phase scaffolded design:

### Phase 1: Guided Implementation (In-Class)
Learners establish a baseline model using a standard industrial workflow.
* **Infrastructure:** PyTorch pipeline setup on Tesla V100 GPUs.
* **Training:** Fine-tuning **ResNet-50** on the target dataset.
* **Validation:** Error analysis using Confusion Matrices and Grad-CAM heatmaps.

### Phase 2: The Inquiry Loop (Post-Class)
An independent optimization task to foster critical thinking.
* **The Constraint:** Learners modify exactly **one** variable (e.g., learning rate, augmentation).
* **The Loop:** Hypothesis → GenAI Consultation → Cloud Execution → Evidence-Based Reflection.

---

## 📂 Technical Details

### The Dataset: Cervical Spine X-ray Atlas (CSXA)
This project utilizes the **CSXA Dataset** to present real-world engineering hurdles. Unlike balanced academic sets, this data contains severe class imbalance.

**[🔗 Access the Dataset on Kaggle](https://www.kaggle.com/datasets/ddatad/cervical-x-ray/data)**

**Classes:**
1.  **Lordotic** (Normal)
2.  **Straight** (Loss of curvature/"Tech Neck")
3.  **Sigmoid**
4.  **Kyphotic** (Pathological/Rare)

### The Model
* **Backbone:** ResNet-50 (Pretrained on ImageNet)
* **Optimization:** SGD with step-based decay.
* **Explainability:** Gradient-weighted Class Activation Mapping (Grad-CAM).

---

## 📄 Repository Content

* **`HuaweiICT_ResNet50.ipynb`**: The complete Jupyter Notebook containing the end-to-end pipeline, from data ingestion to explainability visualization.
