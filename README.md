# Cancer Risk Prediction Model

## Overview

This project develops a cancer risk prediction model using genomic, clinical, and lifestyle data from the All of Us research program. The goal is to identify individuals at elevated risk for developing cancer — enabling earlier screening and prevention.

This work lies at the intersection of cancer epidemiology, cancer etiology, and machine learning. It focuses on predictive modeling using time-to-event (survival) analysis.

## Pan-Cancer Approach

Although each cancer has distinct genetic underpinnings, many share common risk factors:

- Behavioral: Smoking, alcohol, obesity, inflammation
- Socioeconomic and access-related factors
- Genetic overlap: Shared risk loci such as TERT, TP53
- Shared environmental exposures

A pan-cancer model enables general risk stratification when the future cancer type is unknown.

## Objectives

- Predict individual-level cancer risk using multimodal data
- Integrate polygenic risk scores (PRS) from pan-cancer GWAS
- Engineer clinically meaningful features from EHR and survey data
- Apply survival neural networks for time-to-event prediction

## Current Focus: Outcome Definition

- `event = 1` (Cancer Diagnosis): Based on EHR-confirmed cancer diagnosis
- `event = 0` (No Diagnosis): Excludes individuals with any self-reported or EHR-recorded cancer history
- `time_to_event`: Calculated as time from baseline (e.g., enrollment) to diagnosis or censoring

## Cohort Generation

The cancer and control cohorts were defined based on methodologies from recent studies using the All of Us dataset:

- [Bates et al., 2024, HGG Advances](https://www.cell.com/hgg-advances/fulltext/S2666-2477(25)00008-9#sec-2-5)
- [Aschebrook-Kilfoy et al., 2022, PLOS ONE](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0272522)

### Inclusion Criteria
- Participants with available **self-reported whole genome sequencing (srWGS)** data  
- Cancer cases were defined using:
  - EHR-based **SNOMED** or **ICD** codes indicating a cancer diagnosis  
  - Cancer diagnosis date extracted from the first EHR mention of a cancer diagnosis  
- Controls were defined as participants **without any evidence of cancer** in:
  - EHR diagnosis codes  
  - EHR condition descriptions  
  - Survey responses  

### Exclusion Criteria
- Participants **younger than 20** or **older than 100** at baseline  

### Cohort Size

- **Initial sample**: 38,725 individuals with srWGS data (prior to full quality control and filtering)

## Feature Engineering

### Clinical & Lifestyle Variables

- **Demographics**: Birth decade, gender, race/ethnicity
- **Family History**: Self-reported history of cancer
- **Behavioral Factors**:
  - Smoking history
  - Alcohol use
  - Physical activity
  - Sleep patterns
  - Diet (if available)
- **Chronic Conditions**: Obesity, diabetes, cardiovascular disease
- **Reproductive/Hormonal History**: For sex-specific cancers
- **Environmental/Trauma Exposure**: If available

### Genomic Variables

- **Polygenic Risk Score (PRS)**:  
  Derived from **multi-cancer GWAS summary statistics** published in  
  [Sato et al., *Nature Communications*, 2023](https://www.nature.com/articles/s41467-023-39136-7).  
  This study conducted a pan-cancer and cross-population GWAS meta-analysis across 13 cancer types and identified shared genetic risk loci.

## Modeling Approach

- Survival neural network architecture for time-to-event prediction
- Model trained for prediction, not inference

## Skills Used

- Survival analysis
- Feature engineering from large-scale EHR and survey data
- Genomic data integration (PRS)
- Epidemiological cohort design
- Machine learning for healthcare applications

## Data Source

All data come from the All of Us Research Program (via Researcher Workbench), including:

- EHR data
- Survey/lifestyle data
- Whole genome sequencing (WGS) data (via linked summary statistics or PRS)

---

For questions or collaboration, feel free to reach out or open an issue.

