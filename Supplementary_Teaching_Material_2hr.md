# Supplementary Learning Material (Student Companion)
## For `HuaweiICT_ResNet50.ipynb` — concepts, deeper explanations, diagrams, and external resources

> **Purpose of this file**  
> This is an **optional learning companion** for students who want deeper understanding beyond the code in the notebook.  
> It explains key knowledge points that are often brief in lab code, such as **ResNet**, **transfer learning**, **evaluation metrics**, and **Grad-CAM**.

---

## How to Use This Supplement
- Read this before/after running each notebook section.
- Use the “Quick Check” questions to self-test.
- Open the external links for visual explanations.
- Revisit the “Common Mistakes” section before assignments.

---

## 1) Big Picture: What Are We Doing in This Lab?

You are building a **medical image classifier** that predicts cervical curvature type from X-ray images.

### End-to-end pipeline (simplified)

```text
Raw X-ray images + Excel labels
            |
            v
Data cleaning / matching image IDs with labels
            |
            v
Train/Validation split (stratified)
            |
            v
Preprocessing + augmentation + normalization
            |
            v
Pretrained ResNet50 fine-tuning
            |
            v
Evaluation (accuracy + confusion matrix + precision/recall/F1)
            |
            v
Interpretability (Grad-CAM heatmaps)
```

### Why this matters in medical AI
- Performance alone is not enough; we also need **reliability** and **interpretability**.
- False negatives can be costly in healthcare.
- Models can learn shortcuts (artifacts/text markers), so we must inspect attention maps.

---

## 2) What is ResNet? (Deeper than notebook comments)

## 2.1 Problem before ResNet
When CNNs became very deep, training got harder because of issues like vanishing gradients and optimization instability.

## 2.2 Core idea of ResNet
ResNet introduces **skip connections** (identity shortcuts): instead of learning a full mapping `H(x)`, the block learns a residual `F(x) = H(x) - x`, so output becomes:

\[
\text{Output} = F(x) + x
\]

This makes deep networks easier to optimize.

### Residual block diagram (conceptual)

```text
Input x
  |------------------------------|
  |                              v
  |                        (identity)
  v
[Conv -> BN -> ReLU -> Conv -> BN] = F(x)
  |
  v
Add: F(x) + x
  |
  v
ReLU -> next block
```

## 2.3 Why ResNet50 specifically?
- Strong baseline for transfer learning.
- Well-tested in research and industry.
- Good trade-off between accuracy and computational cost for many datasets.

### External learning links
- Original ResNet paper (He et al., 2015): https://arxiv.org/abs/1512.03385
- Illustrated CNN/ResNet intuition (Stanford CS231n notes): https://cs231n.github.io/convolutional-networks/
- PyTorch ResNet docs: https://pytorch.org/vision/stable/models/generated/torchvision.models.resnet50.html

### Quick Check
1. Why do skip connections help optimization?  
2. Is ResNet50 always better than smaller models for small medical datasets?

---

## 3) What is Transfer Learning?

Transfer learning means starting from a model pretrained on a large dataset (e.g., ImageNet), then adapting it to your target task.

## 3.1 Why it helps here
- Medical datasets are often small.
- Pretrained models already learn useful low/mid-level visual features.
- Faster convergence and often better generalization.

## 3.2 Two common strategies

```text
A) Feature Extractor
   Freeze backbone -> train only final classifier

B) Fine-tuning (used in your notebook)
   Initialize from pretrained weights -> train some or all layers with small LR
```

## 3.3 Practical rule-of-thumb
- If dataset is very small: start with more frozen layers.
- If dataset is moderate and similar domain cues are needed: fine-tune deeper layers carefully.

### External learning links
- PyTorch transfer learning tutorial: https://pytorch.org/tutorials/beginner/transfer_learning_tutorial.html
- FastAI transfer learning explanation: https://course.fast.ai/

### Quick Check
1. Why do we usually use a smaller learning rate when fine-tuning pretrained models?  
2. What risk appears if all layers are aggressively updated on tiny datasets?

---

## 4) Data Splitting and Imbalance (Why stratified split matters)

If class distribution is imbalanced, random split can create an unrepresentative validation set.

### Example
If one class = 60% in full dataset but only 35% in validation, performance estimation becomes unstable.

### Stratified split
Preserves class ratios in train and validation, giving fairer evaluation.

### External learning links
- scikit-learn train_test_split docs: https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html
- Intro to imbalanced classification (practical): https://machinelearningmastery.com/what-is-imbalanced-classification/

### Quick Check
- Why can high overall accuracy still hide poor minority-class performance?

---

## 5) Data Augmentation in Medical Imaging

Augmentation improves robustness, but must preserve clinical meaning.

## 5.1 Safe vs risky transforms (task-dependent)
- Often safer: slight rotation, small translation, mild brightness/contrast jitter.
- Risky (depending on task): vertical flips, aggressive cropping, large distortions.

## 5.2 Principle
**Clinical semantics first**: any transform that changes medically meaningful structure can hurt label validity.

### External learning links
- Albumentations docs (augmentation reference): https://albumentations.ai/docs/
- MONAI transforms for medical imaging: https://docs.monai.io/en/stable/transforms.html

---

## 6) Training Concepts Students Often Miss

## 6.1 Overfitting
Model memorizes training details but generalizes poorly.

Signals:
- Training loss keeps dropping.
- Validation loss stops improving or increases.

## 6.2 Early Stopping
Stop training when validation metric no longer improves for N epochs (patience).

Benefits:
- Reduces overfitting risk.
- Saves compute.

## 6.3 Weight Decay
Regularization that discourages overly large weights and can improve generalization.

### External learning links
- Overfitting/underfitting (Google ML Crash Course): https://developers.google.com/machine-learning/crash-course/overfitting/overfitting
- Early stopping discussion: https://www.deeplearningbook.org/ (search chapter on regularization/optimization)

---

## 7) Evaluation Metrics: Beyond Accuracy

In medical tasks, single-number accuracy is usually insufficient.

## 7.1 Metric meanings
- **Accuracy**: overall correctness.
- **Precision**: when model predicts class X, how often is it correct?
- **Recall (Sensitivity)**: among true class X, how many detected?
- **F1-score**: harmonic mean of precision and recall.

## 7.2 Why recall matters clinically
Low recall can mean missed cases (false negatives), which may be high-risk in healthcare contexts.

### Confusion matrix diagram

```text
                 Predicted
               |  A |  B |  C |
Actual      A  | TP | .. | .. |
            B  | .. | TP | .. |
            C  | .. | .. | TP |

Diagonal = correct predictions
Off-diagonal = confusions/errors
```

### External learning links
- scikit-learn classification report docs: https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html
- Confusion matrix docs: https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html

---

## 8) Explainability: What is Grad-CAM?

Grad-CAM highlights image regions that most influence a class prediction by using gradients flowing into a chosen convolutional layer.

## 8.1 Why use it
- Check whether model focuses on anatomically relevant regions.
- Detect shortcut learning (text markers/background artifacts).

## 8.2 Interpretation caution
- Helpful, but not proof of causal reasoning.
- Always combine with metric analysis and clinical review.

### Grad-CAM flow diagram (simplified)

```text
Input image -> CNN forward pass -> class score
                     |
                     v
          gradients wrt conv feature maps
                     |
                     v
       weighted sum of feature maps -> heatmap
                     |
                     v
         overlay heatmap on original X-ray
```

### External learning links
- Grad-CAM paper: https://arxiv.org/abs/1610.02391
- PyTorch Grad-CAM library/examples: https://github.com/jacobgil/pytorch-grad-cam

---

## 9) Common Student Mistakes (and Fixes)

1. **Only reporting accuracy**  
   Fix: always include per-class precision/recall/F1 and confusion matrix.

2. **Treating augmentation as always beneficial**  
   Fix: verify transformations preserve clinical structure.

3. **Ignoring data leakage risk**  
   Fix: ensure no patient-level leakage between train/val (if patient IDs exist).

4. **Trusting Grad-CAM blindly**  
   Fix: use Grad-CAM as evidence, not ground truth.

5. **Changing many hyperparameters at once**  
   Fix: run controlled experiments, one main change per run.

---

## 10) Suggested Self-Study Path (Easy to Follow)

### Level 1 (Foundation, 1–2 hours)
- Read Sections 1–4 in this file.
- Re-run notebook and annotate each cell with “why this step exists”.

### Level 2 (Model understanding, 2–3 hours)
- Study ResNet + transfer learning links.
- Compare freezing vs full fine-tuning in one controlled experiment.

### Level 3 (Clinical robustness, 2–4 hours)
- Investigate confusion matrix errors by class.
- Review Grad-CAM examples and document suspicious attention patterns.

---

## 11) Mini Glossary
- **Backbone**: feature extractor network (e.g., ResNet50).
- **Fine-tuning**: updating pretrained weights on new task.
- **Generalization**: performance on unseen data.
- **Recall/Sensitivity**: ability to capture true positives.
- **Heatmap**: visual intensity map showing important regions.

---

## 12) One-Page Revision Sheet

```text
1) Clean labels and image matching first.
2) Use stratified split for fair validation.
3) Apply clinically valid augmentation only.
4) Fine-tune pretrained ResNet50 with small LR.
5) Watch train-vs-val curves for overfitting.
6) Evaluate with confusion matrix + precision/recall/F1, not only accuracy.
7) Use Grad-CAM to audit where the model is looking.
8) Improve model using controlled, hypothesis-driven experiments.
```

---

## 13) Optional Extra Resources (Curated)
- Deep Learning Book (free online): https://www.deeplearningbook.org/
- Dive into Deep Learning: https://d2l.ai/
- Medical imaging AI framework (MONAI): https://monai.io/
- Papers with Code (for model ideas): https://paperswithcode.com/

---

### Note to Students
If you feel the notebook is “too code-heavy,” use this companion as your concept map.  
**Goal:** understand not just *how* to run the model, but *why* each design choice is made.
