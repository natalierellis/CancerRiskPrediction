# **Cancer Risk Prediction Model**

## **Overview**
This project will apply **DeepSurv**, a deep learning survival analysis model, to predict **who** will develop cancer and **when** it might occur. Instead of a binary classification, the model outputs a **risk score (hazard function)** using **EHR, survey, and whole genome sequencing (WGS) data** from the **All of Us** research program.  
Rather than focusing on a single cancer type, the model includes **all cancers**, aligning with the shift toward **molecular subtyping** over classification by tissue of origin.

For more information on **DeepSurv**, visit the [DeepSurv GitHub Pages](https://humboldt-wi.github.io/blog/research/information_systems_1920/group2_survivalanalysis/).

---

## **Cohort Definition**
- **Event = 1 (Cancer Diagnosis)**: Identified via **EHR-recorded cancer diagnoses**.
- **Event = 0 (No Cancer Diagnosis)**: Excludes individuals with cancer in EHR or self-reported cancer history to avoid misclassification.

---

## **Feature Engineering**
### **Clinical & Lifestyle Features**
- **Demographics**: Age bin, gender, location  
- **Lifestyle Factors**: Smoking, alcohol use  
- **Medical History**: Comorbidities  

To prevent the model from learning **“older age = higher cancer risk”**, it will use **age bins** instead of raw age, ensuring the model captures risk factors beyond just age.

### **Genomic Features**
Evaluating:
1. **SNPs** – High-dimensional but detailed.  
2. **Gene-Burden Scores** (preferred) – Aggregates damaging mutations per gene, reducing dimensionality while retaining biological relevance.  

---

## **Current Focus: Extracting Outcome Variables**
I am currently working on defining and extracting **outcome variables** for the survival analysis model:
- **Event (Cancer Diagnosis)**: Assigning **1** or **0** based on EHR and survey data.  
- **Time to Event**: Determining **time from baseline to cancer diagnosis** for event = 1 cases and **censoring time** for event = 0 cases.  

This step is critical for structuring the dataset before moving on to feature selection and model training.

