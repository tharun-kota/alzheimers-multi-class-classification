# Alzheimer's Disease Prediction Using Gene Expression Data

## Overview

This repository contains the code and data for predicting the preclinical stage of Alzheimer's disease (AD) based on gene expression data. AD is the most prevalent form of dementia globally and remains an incurable condition that progressively damages brain cells. This study leverages machine learning to develop a robust algorithm capable of predicting the preclinical stage of AD, utilizing gene expression data across three stages: Normal, Mild Cognitive Impairment (MCI), and Alzheimer's.

## Dataset

The dataset used in this study consists of 329 samples collected from three distinct stages of AD:

- **Normal**: 104 samples
- **Mild Cognitive Impairment (MCI)**: 80 samples
- **Alzheimer's**: 145 samples

The gene expression data consists of 30,000 profiled genes, from which differentially expressed genes were selected based on the following criteria:

- **p-value**: Adjusted p-value threshold < 0.05
- **Filtering**: Removal of duplicated genes and genes with unknown functions.

## Methodology

### Feature Selection
- **Differential Gene Expression**: Genes were filtered based on their adjusted p-value to ensure only significant genes were selected.
- **Recursive Feature Elimination (RFE)**: RFE was used in combination with the Support Vector Classifier (SVC) to select the most relevant genes for the classification task.

### Classification
- **Support Vector Classifier (SVC)**: SVC was used to classify the samples into their respective stages (Normal, MCI, and Alzheimer's).
- **Performance**: The model achieved a **Balanced Accuracy Score (BAS)** of 72%.

## Dependencies

- Python 3.x
- scikit-learn
- numpy
- pandas
- matplotlib



## Results

The machine learning model demonstrates the ability to predict the preclinical stage of Alzheimer's disease with a **Balanced Accuracy Score of 72%**, showing promising results for early-stage detection based on gene expression data.

## Future Work

- Improve model performance by exploring additional machine learning techniques.
- Expand the dataset to include more diverse samples.
- Investigate the biological significance of the selected genes to better understand their role in Alzheimer's progression.



