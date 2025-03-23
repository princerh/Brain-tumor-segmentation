# 🧠 NeuroUNet: Brain Tumor Segmentation & Diagnosis using ResUNet

## 📌 Project Overview
NeuroUNet is an advanced deep-learning model designed for **brain tumor classification and segmentation** using the **ResUNet architecture**. This project aims to accurately detect brain tumors and highlight affected regions in MRI scans.

## 📂 Dataset
The dataset consists of **3,929 images**, a mix of tumor and tumor-free MRI scans, stored in a CSV file with the following entries:
- `patient_id`: Unique identifier for each patient.
- `image_path`: Path to the MRI image.
- `mask_path`: Path to the corresponding tumor segmentation mask.
- `mask`: **0** for no tumor, **1** for tumor detected.

## 🏥 Classification Task
We classify images into **tumor** or **tumor-free** categories:
- **Data Split:**
  - **85%** for training & validation.
  - **15%** for testing.
- **Model Details:**
  - ResNet-based classifier with **25 million parameters**.
  - Model size: **98.23 MB**.
  - Optimizer: **AdamW** with **LR=0.0001** and **weight decay=0.0001**.
  - **Early stopping** & **checkpointing** to monitor validation loss.
- **Performance Metrics:**
  - **Training Accuracy:** 99.36%
  - **Validation Accuracy:** 98.08%
  - **Test Accuracy:** 95.42%

### 📊 Confusion Matrix & Metrics
The model misclassified only **27 out of 576 test images**.

| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|-----------|---------|
| **0 (No Tumor)** | 0.94 | 0.99 | 0.96 | 362 |
| **1 (Tumor)** | 0.99 | 0.88 | 0.93 | 214 |
| **Micro Avg** | 0.95 | 0.95 | 0.95 | 576 |
| **Macro Avg** | 0.96 | 0.94 | 0.95 | 576 |
| **Weighted Avg** | 0.96 | 0.95 | 0.95 | 576 |

## 🖼️ Segmentation Task
For tumor segmentation, we focused only on MRI scans with **existing tumor masks** (~1,373 images). 

- **Data Split:** Train/Validation/Test.
- **Model Details:**
  - **ResUNet** architecture with **1.2 million parameters**.
  - Model size: **4.62 MB**.
  - Optimizer: **Adam** with **LR=0.0001**.
- **Performance Metrics:**
  - **Training Accuracy:** 99.81%
  - **Dice Coefficient:** 0.9684
  - **Loss:** 0.0604
  - **Tversky Index:** 0.9763
  - **Validation Accuracy:** 99.44%
  - **Validation Dice Coefficient:** 0.9050
  - **Validation Loss:** 0.1617
  - **Validation Tversky Index:** 0.9117

## 🔬 Model Integration & Comparison
Finally, we combined the **classification** and **segmentation** models:
- Created a **dataframe** containing:
  - **Predicted class label (tumor/no tumor).**
  - **Predicted segmentation mask.**
- **Visualization:**
  - Original masks overlapped on images.
  - Predicted masks overlapped on images for comparison.

## 📌 Conclusion
NeuroUNet demonstrates a **highly accurate** and **lightweight** deep learning model for brain tumor detection and segmentation. The combination of **ResNet-based classification** and **ResUNet-based segmentation** ensures precise tumor localization and diagnosis.
