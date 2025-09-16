# Alzheimer's Disease Prediction Using Gene Expression Data

## Overview
This repository contains the code and data for predicting the preclinical stage of Alzheimer's disease (AD) based on gene expression data. AD is the most prevalent form of dementia globally and remains an incurable condition that progressively damages brain cells. This study leverages machine learning to develop a robust algorithm capable of predicting the preclinical stage of AD, utilizing gene expression data across three stages: **Normal, Mild Cognitive Impairment (MCI), and Alzheimer's**.

## Dataset
The dataset used in this study (GSE63063, platform GPL6947) consists of **329 samples** collected across three stages of AD:

- **Normal**: 104 samples  
- **Mild Cognitive Impairment (MCI)**: 80 samples  
- **Alzheimer's**: 145 samples  

The raw data can be downloaded directly from the [NCBI GEO database](https://www.ncbi.nlm.nih.gov/geo/) using the `GEOparse` Python library.  
In this repository, we worked with the processed expression matrix (`GPL6947.csv`) derived from GEO for convenience.  

Gene expression profiles (~30,000 genes) were filtered to remove duplicates and genes with unknown functions. Differential expression analysis was applied using an adjusted **p-value threshold < 0.05** to identify significant genes.

## Methodology
The pipeline combined statistical filtering, feature selection, and classification:

- **Feature Selection**  
  - *Differential Expression Analysis*: Genes selected based on adjusted p-value.  
  - *Recursive Feature Elimination (RFE)*: Performed with Support Vector Classifier (SVC) to identify the most predictive biomarkers.  

- **Classification**  
  - *Support Vector Classifier (SVC)*: Used for multi-class prediction (Normal, MCI, AD).  
  - *Other Classifiers*: Random Forest (RFC), Gaussian Naïve Bayes, and ensemble models were evaluated for comparison.  

![Balanced Accuracy Comparison](https://github.com/user-attachments/assets/8440f4cb-30b2-4bad-b362-a1fc66f869fc)

## Results
Our experiments demonstrated the effectiveness of feature selection and classification methods:

- Baseline classifiers (RFC, SVC, Naïve Bayes) were evaluated with Pearson and Chi-square selected features.  
- RFE with SVC produced the best performance, achieving a **Balanced Accuracy Score (BAS) of 72%**.  
- ROC curves and confusion matrices confirmed that feature selection significantly improved classification robustness.  
  
![Evaluation metrics of Different feature selection techniques](https://github.com/user-attachments/assets/48d90844-f550-4c84-84b2-f24bd10e8ecb)
  

## Dependencies
- Python 3.x  
- scikit-learn  
- numpy, pandas  
- matplotlib, seaborn  
- GEOparse  

## Reproducibility
To ensure reproducibility, the dataset can be directly downloaded from GEO and used with the provided code.  

**Download dataset with GEOparse:**
```python
import GEOparse

# Download and parse dataset
gse = GEOparse.get_GEO("GSE63063", destdir=".")
print(f"Samples: {len(gse.gsms)}")
