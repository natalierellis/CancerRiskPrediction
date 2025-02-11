# **Cancer Risk Prediction Model**

## **Overview**  
I am developing a model using genomic, clinical, and lifestyle data from All of Us to estimate when someone might develop cancer, rather than simply predicting if they will. Instead of a binary classification, the model will output a risk score (hazard function), leveraging EHR, survey, and whole genome sequencing (WGS) data from the All of Us research program.  

Rather than focusing on a single cancer type, the model includes all cancers, aligning with the shift toward molecular subtyping over classification by tissue of origin.

## **Model Approach**  
The model will likely use **DeepSurv**, a deep learning-based survival analysis framework that extends the Cox model with neural networks. 

For more information on **DeepSurv**, visit the [DeepSurv GitHub Pages](https://humboldt-wi.github.io/blog/research/information_systems_1920/group2_survivalanalysis/) and refer to the original paper:  

📄 **Katzman, Jared L., et al.** *DeepSurv: Personalized Treatment Recommender System Using a Cox Proportional Hazards Deep Neural Network. BMC Medical Research Methodology 18.1 (2018): 24*  

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


