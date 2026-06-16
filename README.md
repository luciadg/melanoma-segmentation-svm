# Melanoma Detection via Automatic Segmentation and Supervised Learning

Academic project developed for the Master's in Bioinformatics for Health Sciences (UDC). This repository contains a two-stage automatic pipeline designed to identify melanomas from dermoscopic images using classic Computer Vision techniques and Machine Learning.

## 1. Project Overview

The system operates in two main phases to map dermatological lesions and classify them accurately:

1. **Lesion Segmentation & Validation:**
   * Automatic segmentation of the skin lesion.
   * Pixel-wise validation against expert manual masks (Ground Truth) calculating the Intersection over Union (IoU), mapping False Positives and False Negatives.
3. **Feature Extraction & Classification:**
   * Extraction of 5 specific descriptors based on the clinical ABCDE rule and texture analysis:
     * **Asymmetry:** Computed via geometric bounding box horizontal reflection.
     * **Border (Circularity):** Contour-based irregularity metric.
     * **Color:** Mean and Standard Deviation of the Red (R) channel.
     * **Texture:** GLCM (Gray-Level Co-occurrence Matrix) Contrast.
   * Supervised classification using a Linear Support Vector Machine (SVM) with automated hyperparameter tuning (`trainAuto`).

## 2. Dataset Specifications

The data utilized in this project is a subset of the ISIC (International Skin Imaging Collaboration) 2018 Challenge. To facilitate immediate reproducibility, the dataset and expert manual masks are included in this repository.

* **Source:** ISIC 2018 Archive.
* **Quantity:** 51 dermoscopic images.
* **Class Distribution:** 19 melanomas, 32 benign nevi.
* **Directory Structure:** * `/dataset/images/`: Raw RGB dermoscopic images.
  * `/dataset/masks/`: Expert manual masks for segmentation validation.
  * `/dataset/list.csv`: Ground truth class labels (0 = Benign, 1 = Melanoma).

## 3. Results and Performance Metrics

The model's generalization capability was rigorously evaluated using Leave-One-Out Cross-Validation (LOOCV). The pipeline achieves the following metrics for the provided dataset:

* **Segmentation Average IoU (mIoU):** 82.83%
* **Classification Accuracy:** 90.20%
* **Sensitivity (Melanoma detection):** 84.21%
* **Specificity (Benign detection):** 93.75%

## 4. Technical Documentation

For a comprehensive explanation of the methodology, algorithm design choices, mathematical justification, and an in-depth discussion of clinical limitations, please refer to the full technical report (Spanish):
* [Technical_Report_Melanoma_Detection.pdf](./Technical_Report_Melanoma_Detection.pdf)

## 5. Environment Requirements and Execution

To replicate the environment and execute the pipeline, install the dependencies listed in the `requirements.txt` file. Standard libraries such as `os` and `csv` are native to Python and do not require manual installation.

```bash
pip install -r requirements.txt
