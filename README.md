# Medical Image Classification with ResNet-50 on Huawei Cloud ModelArts ☁️🩺

![Platform](https://img.shields.io/badge/Platform-Huawei_Cloud_ModelArts-red)
![Model](https://img.shields.io/badge/Model-ResNet--50-blue)
![Task](https://img.shields.io/badge/Task-Medical_Image_Classification-green)
![Explainability](https://img.shields.io/badge/XAI-Grad--CAM-purple)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

A cloud-native, hands-on teaching laboratory for introducing undergraduate students to practical deep learning using authentic cervical spine X-ray data.

This repository was developed for the **Huawei ICT Teaching Competition 2025–26** as a reusable instructional case on medical image classification, transfer learning, holistic model evaluation, and responsible GenAI-supported reflection.

---

## 📌 Project Overview

Most beginner deep learning tutorials use clean toy datasets such as MNIST or CIFAR-10. This project deliberately moves students into a more realistic setting:
The lab task is to fine-tune a pretrained **ResNet-50** model to classify cervical spine curvature types from X-ray images.

> **Educational scope:** This project is designed for teaching and research training only. It is not a clinical diagnostic system and must not be used for patient care.

---

## 🎯 Learning Objectives

By completing this lab, students will learn to:

1. Operate a GPU-powered notebook environment on Huawei Cloud ModelArts.
2. Build a PyTorch data pipeline using clinical images and Excel-based labels.
3. Apply transfer learning with a pretrained ResNet-50 model.
4. Use early stopping and learning rate scheduling to reduce overfitting on small medical datasets.
5. Evaluate performance using accuracy, precision, recall, F1-score, and confusion matrices.
6. Interpret model predictions using Grad-CAM heatmaps.
7. Reflect on model limitations and propose one evidence-based improvement after the lab.

---

## 📺 Project Demo

Watch the instructional demonstration and pedagogical explanation:

[▶️ Watch: ResNet-50 Cervical Spine Classification Lab](https://www.bilibili.com/video/BV1ZP6BBvEgU/?share_source=copy_web&vd_source=f23fdab1cf57871b257305ebe143b9c2)

---

## 📄 Main Teaching Materials

| Resource | Description |
|---|---|
| [Lab Note.pdf](./Lab%20Note.pdf) | Polished two-hour student-facing lab note |
| [HuaweiICT_ResNet50.ipynb](./HuaweiICT_ResNet50.ipynb) | Complete Jupyter notebook for training, evaluation, and Grad-CAM |
| [After-Class Inquiry Report](./anonymous_student_after_class_inquiry_task_report.pdf) | Example of GenAI-supported student reflection |
| [Kaggle Notebook](https://www.kaggle.com/code/ddatad/spine-xray-curvature-classification-resnet50) | Online notebook reference |
| [CSXA Dataset on Kaggle](https://www.kaggle.com/datasets/ddatad/cervical-x-ray/data) | Cervical spine X-ray dataset used in this lab |

---

## 🧠 Pedagogical Design

The lab follows a two-phase scaffolded learning design.

### Phase 1: In-Class Guided Implementation

Students first reproduce a complete baseline pipeline under instructor guidance.

### Phase 2: After-Class Inquiry Task

Students then act as lead engineers and improve the baseline model through a controlled experiment.

The required inquiry loop is:

```text
Observe problem
→ Ask GenAI for possible strategies
→ Critique the suggestions
→ Select one strategy
→ Implement on ModelArts
→ Compare against baseline
→ Write evidence-based reflection
```

The design intentionally avoids both extremes:

| Approach | Problem |
|---|---|
| Banning GenAI | Ignores students' real learning environment |
| Unrestricted GenAI use | Encourages copy-paste without understanding |
| Reflective GenAI use | Encourages brainstorming, critique, and responsibility |

---

## 🩻 Dataset and Classification Task

This lab uses the **Cervical Spine X-ray Atlas (CSXA)** dataset introduced by Ran et al. (2024).

For teaching purposes, we use 999 cervical spine X-ray images and formulate the task as a four-class classification problem:

| Class | Clinical label |
|---|---|
| 1 | Lordotic |
| 2 | Straight |
| 3 | Sigmoid |
| 4 | Kyphotic |

---


## 📊 Evaluation Philosophy

The lab emphasizes that **global accuracy is not enough for medical AI**.

In the baseline run, the model reaches approximately **75.5% validation accuracy**, but class-level analysis reveals a critical weakness: the Sigmoid class has much lower recall than the other classes.

This is the central teaching point:

> A model can look acceptable from one headline metric while still failing on a clinically meaningful minority class.


---

## 📚 References and Further Reading

### Core Dataset

- Ran, Y., Qin, W., Qin, C., et al. (2024). *A high-quality dataset featuring classified and annotated cervical spine X-ray atlas*. Scientific Data, 11, 625.  
  https://www.nature.com/articles/s41597-024-03383-0

### Deep Learning Concepts

- He, K., Zhang, X., Ren, S., & Sun, J. (2015). *Deep Residual Learning for Image Recognition*.  
  https://arxiv.org/abs/1512.03385

- PyTorch Official Tutorial: *Transfer Learning for Computer Vision*.  
  https://docs.pytorch.org/tutorials/beginner/transfer_learning_tutorial.html

- TorchVision ResNet-50 Documentation.  
  https://docs.pytorch.org/vision/main/models/generated/torchvision.models.resnet50.html

### Explainable AI

- Selvaraju, R. R., Cogswell, M., Das, A., Vedantam, R., Parikh, D., & Batra, D. (2017). *Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization*.  
  https://arxiv.org/abs/1610.02391

---

