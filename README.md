# Brain Tumor MRI Classification

This project builds a multiclass brain tumor MRI classifier using a combination of traditional computer vision features and deep learning-based feature extraction. The model classifies brain MRI scans into four categories: glioma, meningioma, pituitary tumor, and no tumor.

The main contribution of this project is a feature fusion approach that combines handcrafted image descriptors, including HOG and LBP, with pretrained ResNet embeddings to improve classification performance.

## Project Overview

Brain tumor classification from MRI scans is an important computer vision task with potential applications in clinical decision support. In this project, we compare multiple modeling approaches for MRI image classification, including:

- A CNN baseline model
- Handcrafted computer vision features
- Pretrained ResNet-based feature extraction
- Feature fusion using HOG, LBP, and ResNet embeddings
- SVM classification on fused feature representations

The final approach uses fused feature vectors to capture complementary information from MRI scans. HOG captures edge and shape structure, LBP captures local texture patterns, and ResNet embeddings capture higher-level visual representations learned from deep neural networks.

## Dataset

The project uses the Brain Tumor MRI Dataset from Kaggle, which contains MRI images across four classes:

- Glioma
- Meningioma
- Pituitary tumor
- No tumor

The full dataset is not included in this repository due to size constraints. To reproduce the project, download the dataset separately from Kaggle and place it in the expected local data directory.

## Methods

### 1. Preprocessing

Images were loaded, resized, and normalized before feature extraction and modeling. The project also includes exploratory analysis of image dimensions, class distributions, and sample MRI scans.

### 2. CNN Baseline

A convolutional neural network baseline was trained to establish a deep learning benchmark for the classification task.

### 3. Handcrafted Features

Two traditional computer vision feature extractors were used:

- **HOG (Histogram of Oriented Gradients):** captures edge direction and shape structure
- **LBP (Local Binary Patterns):** captures local texture information

These features provide interpretable representations of MRI image patterns.

### 4. Deep Feature Extraction

A pretrained ResNet model was used as a fixed feature extractor. Instead of training a deep network from scratch, image embeddings were extracted from the pretrained model and used for downstream classification.

### 5. Feature Fusion

The strongest model combined HOG, LBP, and ResNet features into a single fused feature vector. An SVM classifier was then trained on the fused representation.

This approach allowed the model to benefit from both handcrafted image descriptors and deep visual embeddings.

## Results

The feature fusion model achieved the strongest overall performance.

| Model / Approach | Summary |
|---|---|
| CNN baseline | Used as a deep learning benchmark |
| HOG features | Captured shape and edge information |
| LBP features | Captured local texture patterns |
| ResNet features | Captured high-level deep visual representations |
| HOG + LBP + ResNet fusion | Best-performing approach |

Final performance:

| Metric | Score |
|---|---:|
| Validation Accuracy | 96.13% |
| Test Accuracy | 93.37% |

The results suggest that combining handcrafted and deep learning features can improve classification performance by capturing complementary information from MRI scans.

## Flipped Image Experiment

An additional experiment evaluated model robustness by testing performance on horizontally flipped MRI images. This tested whether the model relied heavily on orientation-specific features or whether it could still classify tumors using broader visual patterns.

The ResNet-based features remained strong under flipped-image testing, suggesting that the model captured global image context and higher-level representations beyond only local edge or texture patterns.

## Contributions

This was a collaborative computer vision project. My teammates were Amanda Chung, Caitlin Gainey, and Clara Rhoades. My contributions included work on the classification pipeline, feature fusion experiments, model evaluation, and interpretation of results.

This repository is a cleaned and curated public version of the project, focused on the final modeling workflow, experiments, and results.

## Repository Structure

```text
Brain_Tumor_Classification/
├── README.md
├── .gitignore
├── final_classification_model.ipynb
├── flipped_test_experiment.ipynb
├── cnn_baseline.ipynb
├── resnet_comparison.ipynb
├── exploratory_data_analysis.ipynb
├── final_report.pdf
└── images/
