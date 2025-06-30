# Fusarium Head Blight Detection in Wheat Crops using Machine Learning

A deep learning-based classification project to detect **Fusarium Head Blight (FHB)** in wheat crops using **EfficientNet B0**. This work was conducted as part of the course _Crop Protection Chemicals and Technopreneurship Development [EP60046]_ at **IIT Kharagpur**.

## Overview

Fusarium Head Blight (FHB) is a fungal disease that affects wheat crops, causing significant yield loss and posing health risks due to mycotoxins. This project aims to:

- Automate detection of FHB from RGB images of wheat heads.
- Classify images as **Healthy (Class 0)** or **Infected (Class 1)**.
- Implement and train the **EfficientNet B0** architecture for binary classification.

## Literature Review

Previous work on FHB detection has relied on:
- Manual scoring (subjective and labor-intensive)
- Classical ML models (SVM, k-NN, Decision Trees) using handcrafted features
- Recent shift to deep learning (CNNs), especially **EfficientNet**, using RGB images for severity classification

Our project builds on this by implementing **EfficientNet B0** with binary labels.

---

## Methodology

### Dataset

- Source: [Rößle et al. (2023)](https://spj.science.org/doi/abs/10.34133/plantphenomics.0068)
- RGB images from 2021 season, annotated by raters on a scale of 1 to 9
- Preprocessing threshold:
  - Score ≤ 4 → Healthy
  - Score > 4 → Infected

### Preprocessing

- Combined images from different cameras
- Resized all images to **224×224** using OpenCV
- Train-test split: **80%-20%**

### Model Architecture

- Used **EfficientNet B0**
- Input: 224×224 RGB images
- Output: Binary classification (healthy/infected)
- Optimizer: **Adam**
- Loss Function: **Categorical Cross-Entropy**
- Epochs: **20**

### Evaluation Metrics

- **Accuracy**
- **Precision**, **Recall**, **F1-score**
- **Confusion Matrix**

---

## Results

### Accuracy vs Epochs
- The model showed increasing accuracy with training, reaching **~69%**.

### Confusion Matrix

|                | Predicted Healthy | Predicted Infected |
|----------------|-------------------|--------------------|
| **Actual Healthy** | 14                | 96                 |
| **Actual Infected**| 3                 | 206                |

- **High recall** for infected plants
- **Low precision** for healthy plants (many false positives)

### Classification Report

| Class | Precision | Recall | F1-score |
|-------|-----------|--------|----------|
| 0 (Healthy) | 0.82      | 0.13   | 0.22     |
| 1 (Infected)| 0.68      | 0.99   | 0.81     |
| **Accuracy** |           |        | **0.69** |

---

## Discussion

- Strength: Model effectively detects infected plants
- Limitation: Misclassifies many healthy plants
- Future work:
  - Increase dataset size and variety
  - Use data augmentation
  - Expand to multi-class severity classification

---

## Conclusion

This project successfully demonstrates a deep learning pipeline using **EfficientNet B0** for FHB detection. It highlights the potential of image-based crop disease monitoring and sets the foundation for scalable, field-deployable solutions.

---

## References

1. Moustafa Gaber, *Fusarium head blight detection in wheat with deep learning and RGB images*, 2024.
2. Rößle et al., *Efficient Non-Invasive FHB Estimation Using RGB Images from a Novel Multi-Year, Multi-Rater Dataset*, Plant Phenomics, 2023.

---

## 📎 License

This project is for academic and research purposes only.
