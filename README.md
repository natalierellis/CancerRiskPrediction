# Cancer Risk Prediction Model

## Overview

This project develops a cancer risk prediction model using genomic, clinical, and lifestyle data from the All of Us research program. The goal is to identify individuals at elevated risk for developing cancer — enabling earlier screening and prevention.

This work lies at the intersection of cancer epidemiology, cancer etiology, and machine learning. It focuses on predictive modeling using time-to-event (survival) analysis.

## Objectives

- Predict individual-level cancer risk using multimodal data
- Integrate polygenic risk scores (PRS) from pan-cancer GWAS
- Engineer clinically meaningful features from EHR and survey data
- Apply survival neural networks for time-to-event prediction

## Current Focus: Outcome Definition

- `event = 1` (Cancer Diagnosis): Based on EHR-confirmed cancer diagnosis
- `event = 0` (No Diagnosis): Excludes individuals with any self-reported or EHR-recorded cancer history
- `time_to_event`: Calculated as time from baseline (e.g., enrollment) to diagnosis or censoring

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

- **Polygenic Risk Score (PRS)**: Derived from multi-cancer GWAS summary statistics

## Modeling Approach

- Survival neural network architecture for time-to-event prediction
- Model trained for prediction, not inference

## Why Pan-Cancer?

Although each cancer has distinct genetic underpinnings, many share common risk factors:

- Behavioral: Smoking, alcohol, obesity, inflammation
- Socioeconomic and access-related factors
- Genetic overlap: Shared risk loci such as TERT, TP53
- Shared environmental exposures

A pan-cancer model enables general risk stratification when the future cancer type is unknown.

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

