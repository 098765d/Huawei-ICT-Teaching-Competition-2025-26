# Medical Image Classification with ResNet-50 on Huawei Cloud ModelArts ☁️🩺
# 基于华为云 ModelArts 的 ResNet-50 医学影像分类教学项目 ☁️🩺

![Platform](https://img.shields.io/badge/Platform-Huawei_Cloud_ModelArts-red)
![Model](https://img.shields.io/badge/Model-ResNet--50-blue)
![Task](https://img.shields.io/badge/Task-Medical_Image_Classification-green)
![Explainability](https://img.shields.io/badge/XAI-Grad--CAM-purple)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

> **EN:** A cloud-native teaching lab for undergraduate deep learning practice with real cervical spine X-ray data.  
> **中：** 一个面向本科教学的云原生深度学习实验项目，使用真实颈椎 X 光数据开展实践训练。

> **EN:** Developed for the **Huawei ICT Teaching Competition 2025–26** as a reusable instructional case on transfer learning, model evaluation, and responsible GenAI-assisted reflection.  
> **中：** 本仓库为 **Huawei ICT Teaching Competition 2025–26** 开发，聚焦迁移学习、模型评估与负责任的 GenAI 辅助反思教学。

---

## Table of Contents | 目录

- [Project Overview | 项目概览](#project-overview--项目概览)
- [Learning Objectives | 学习目标](#learning-objectives--学习目标)
- [Project Demo | 演示视频](#project-demo--演示视频)
- [Main Teaching Materials | 教学材料](#main-teaching-materials--教学材料)
- [Pedagogical Design | 教学设计](#pedagogical-design--教学设计)
- [Dataset & Task | 数据集与任务](#dataset--task--数据集与任务)
- [Evaluation Philosophy | 评估理念](#evaluation-philosophy--评估理念)
- [Environment & Quick Start | 环境与快速开始](#environment--quick-start--环境与快速开始)
- [Repository Structure | 仓库结构](#repository-structure--仓库结构)
- [Limitations & Scope | 边界与限制](#limitations--scope--边界与限制)
- [References | 参考文献](#references--参考文献)
- [License | 许可证](#license--许可证)

---

## Project Overview | 项目概览

**EN:** Most beginner tutorials use toy datasets (e.g., MNIST/CIFAR-10). This project intentionally places students in a more realistic workflow: fine-tuning a pretrained **ResNet-50** to classify cervical spine curvature from X-ray images.  
**中：** 许多入门教程使用 MNIST/CIFAR-10 等玩具数据集。本项目刻意采用更真实的流程：微调预训练 **ResNet-50**，完成颈椎曲度 X 光图像分类任务。

> **Educational scope | 教学用途声明**  
> **EN:** For education and research training only. Not a clinical diagnostic system.  
> **中：** 仅用于教学与科研训练，不构成临床诊断系统。

---

## Learning Objectives | 学习目标

By completing this lab, students will learn to:  
完成本实验后，学生将能够：

1. Use a GPU notebook environment on Huawei Cloud ModelArts. / 在华为云 ModelArts 上使用 GPU Notebook 环境。
2. Build a PyTorch data pipeline with medical images and Excel labels. / 基于医学图像与 Excel 标签构建 PyTorch 数据流水线。
3. Apply transfer learning using pretrained ResNet-50. / 使用预训练 ResNet-50 实现迁移学习。
4. Use early stopping and LR scheduling for small datasets. / 在小样本场景中使用早停与学习率调度降低过拟合。
5. Evaluate with accuracy, precision, recall, F1, and confusion matrix. / 使用准确率、精确率、召回率、F1 与混淆矩阵评估模型。
6. Interpret predictions with Grad-CAM heatmaps. / 使用 Grad-CAM 热力图解释模型预测。
7. Propose one evidence-based improvement after reflection. / 在反思后提出一项有证据支持的改进方案。

---

## Project Demo | 演示视频

- **EN:** Instructional demonstration and pedagogical explanation:  
- **中：** 教学演示与设计讲解：  
  [▶️ ResNet-50 Cervical Spine Classification Lab](https://www.bilibili.com/video/BV1ZP6BBvEgU/?share_source=copy_web&vd_source=f23fdab1cf57871b257305ebe143b9c2)

---

## Main Teaching Materials | 教学材料

| Resource | Description |
|---|---|
| [Lab Note.pdf](./Lab%20Note.pdf) | EN: Polished two-hour student lab note. / 中：面向学生的两小时实验讲义。 |
| [HuaweiICT_ResNet50.ipynb](./HuaweiICT_ResNet50.ipynb) | EN: End-to-end notebook for training, evaluation, and Grad-CAM. / 中：覆盖训练、评估与 Grad-CAM 的完整 Notebook。 |
| [After-Class Inquiry Report](./anonymous_student_after_class_inquiry_task_report.pdf) | EN: Example GenAI-supported reflection report. / 中：GenAI 辅助课后探究报告示例。 |
| [Kaggle Notebook](https://www.kaggle.com/code/ddatad/spine-xray-curvature-classification-resnet50) | EN: Online notebook reference. / 中：在线 Notebook 参考。 |
| [CSXA Dataset on Kaggle](https://www.kaggle.com/datasets/ddatad/cervical-x-ray/data) | EN: Dataset used in this lab. / 中：本实验使用的数据集。 |

---

## Pedagogical Design | 教学设计

**EN:** The lab uses a two-phase scaffolded design.  
**中：** 本实验采用“两阶段支架式”教学设计。

### Phase 1: In-Class Guided Implementation | 第一阶段：课内引导实现

**EN:** Students reproduce a baseline pipeline under instructor guidance.  
**中：** 学生在教师指导下复现实验基线流程。

### Phase 2: After-Class Inquiry Task | 第二阶段：课后探究任务

**EN:** Students act as lead engineers and improve the baseline with controlled experiments.  
**中：** 学生以“主程工程师”角色，通过可控实验改进基线模型。

Required inquiry loop / 必做探究闭环：

```text
Observe problem
→ Ask GenAI for possible strategies
→ Critique the suggestions
→ Select one strategy
→ Implement on ModelArts
→ Compare against baseline
→ Write evidence-based reflection
```

Design rationale / 设计动机：

| Approach | Issue |
|---|---|
| Ban GenAI | EN: Unrealistic for modern learning contexts. / 中：与真实学习环境脱节。 |
| Unrestricted GenAI | EN: Risks copy-paste behavior without understanding. / 中：容易导致“复制粘贴式学习”。 |
| Reflective GenAI use | EN: Promotes critique, accountability, and evidence-based learning. / 中：促进批判思维、责任意识与证据驱动学习。 |

---

## Dataset & Task | 数据集与任务

**EN:** This lab uses the **Cervical Spine X-ray Atlas (CSXA)** dataset (Ran et al., 2024). For teaching, 999 images are used to form a four-class classification task.  
**中：** 本实验使用 **Cervical Spine X-ray Atlas (CSXA)** 数据集（Ran et al., 2024），教学中选用 999 张图像构建四分类任务。

| Class | Clinical Label |
|---|---|
| 1 | Lordotic |
| 2 | Straight |
| 3 | Sigmoid |
| 4 | Kyphotic |

---

## Evaluation Philosophy | 评估理念

**EN:** Global accuracy alone is insufficient for medical AI tasks. In the baseline run, validation accuracy is about **75.5%**, but class-level analysis shows lower recall for the **Sigmoid** class.  
**中：** 医学 AI 任务不能只看总体准确率。基线实验验证准确率约 **75.5%**，但分类别分析显示 **Sigmoid** 类召回率明显偏低。

> **EN:** A model can look acceptable on headline metrics while failing on a clinically meaningful minority class.  
> **中：** 模型可能在“总指标”上看起来可用，但在临床意义重要的小类上表现不足。

---

## Environment & Quick Start | 环境与快速开始

### Environment | 运行环境

- **EN:** Huawei Cloud ModelArts Notebook (GPU-enabled).  
- **中：** 华为云 ModelArts Notebook（启用 GPU）。
- **EN:** Framework: PyTorch + TorchVision (versions follow the notebook environment).  
- **中：** 框架：PyTorch + TorchVision（版本以 Notebook 环境为准）。

### Quick Start | 快速开始

```bash
# 1) Clone repository
# 1）克隆仓库
git clone <your-repo-url>
cd Huawei-ICT-Teaching-Competition-2025-26

# 2) Open the notebook in ModelArts or Jupyter
# 2）在 ModelArts 或 Jupyter 中打开 Notebook
# File: HuaweiICT_ResNet50.ipynb

# 3) Prepare dataset and label paths according to notebook cells
# 3）按 Notebook 单元配置数据集与标签路径

# 4) Run all cells in order: training -> evaluation -> Grad-CAM
# 4）按顺序执行所有单元：训练 -> 评估 -> Grad-CAM
```

> **Note | 说明**  
> **EN:** Path configuration depends on your mounted dataset location in ModelArts/Kaggle/local Jupyter.  
> **中：** 路径配置取决于你在 ModelArts/Kaggle/本地 Jupyter 中的数据挂载位置。

---

## Repository Structure | 仓库结构

```text
.
├── README.md
├── HuaweiICT_ResNet50.ipynb
├── Lab Note.pdf
├── anonymous_student_after_class_inquiry_task_report.pdf
└── LICENSE
```

---

## Limitations & Scope | 边界与限制

- **EN:** This repository is designed for teaching and training, not for real-world clinical deployment.  
  **中：** 本仓库用于教学训练，不用于真实临床部署。
- **EN:** The baseline result (~75.5% validation accuracy) is dataset/task-specific and should not be generalized without external validation.  
  **中：** 基线结果（约 75.5% 验证准确率）仅适用于当前数据与任务，未经外部验证不可泛化。
- **EN:** Class imbalance or class-specific weaknesses (e.g., Sigmoid recall) require targeted follow-up experiments.  
  **中：** 类别不均衡或类别弱项（如 Sigmoid 召回）需要针对性后续实验。

---

## References | 参考文献

### Core Dataset

- Ran, Y., Qin, W., Qin, C., et al. (2024). *A high-quality dataset featuring classified and annotated cervical spine X-ray atlas*. Scientific Data, 11, 625.  
  https://www.nature.com/articles/s41597-024-03383-0

### Deep Learning

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

## License | 许可证

- **EN:** This project is released under the MIT License (see `LICENSE`).  
- **中：** 本项目采用 MIT 许可证（见 `LICENSE` 文件）。
