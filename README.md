# Modeling Cancer Etiology with Machine Learning for Individualized Risk Prediction

## Overview

This project develops a cancer risk prediction model using genomic, clinical, and lifestyle data from the All of Us research program. The goal is to identify individuals at elevated risk for developing cancer, enabling earlier screening and prevention.

This work lies at the intersection of cancer epidemiology, cancer etiology, and machine learning. Unlike traditional binary classifiers, it focuses on predictive modeling using time-to-event (survival) analysis.

## Objectives

- Predict individual-level cancer risk using multimodal data
- Apply survival analysis to account for censored individuals and time-varying risk
- Integrate polygenic risk scores (PRS) from pan-cancer GWAS
- Engineer clinically meaningful features from EHR and survey data
- Apply survival neural networks for time-to-event prediction

## Survival Analysis Approach

Unlike classification models, survival analysis accounts for censored observations, or individuals who have not (yet) developed cancer by their last point of data collection. This is essential for real-world risk modeling. In this project:
-  The outcome is modeled as `time_to_event` (age at cancer diagnosis or censoring)
-  Kaplan-Meier curves are used for exploratory analysis to visualize cancer-free survival across subgroups (e.g., gender, race, area-level cancer prevalence)
-  Survival neural network architecture for time-to-event prediction

## Outcome Definition

- `event = 1` (Cancer Diagnosis): Based on EHR-confirmed cancer diagnosis
- `event = 0` (No Diagnosis): Excludes individuals with any self-reported or EHR-recorded cancer history
- `time_to_event`: Calculated as time from birth to diagnosis or censoring

## Cohort Generation

The cancer and control cohorts were defined based on methodologies from recent studies using the All of Us dataset:

- [Bates et al., 2024, HGG Advances](https://www.cell.com/hgg-advances/fulltext/S2666-2477(25)00008-9#sec-2-5)
- [Aschebrook-Kilfoy et al., 2022, PLOS ONE](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0272522)

### Inclusion Criteria
- Participants with available self-reported whole genome sequencing (srWGS) data  
- Cancer cases were defined using:
  - EHR-based SNOMED or ICD codes indicating a cancer diagnosis  
  - Cancer diagnosis date extracted from the first EHR mention of a cancer diagnosis  
- Controls were defined as participants without any evidence of cancer in:
  - EHR diagnosis codes  
  - EHR condition descriptions  
  - Survey responses  

### Exclusion Criteria
- Pediatric cancer cases (age at diagnosis < 20)
- Missing or implausible time-to-event (e.g., >100 years)

## Feature Engineering

### Clinical & Lifestyle Variables
-  Age Group: Birth year binned into generational eras (e.g., pre-1950, 1950–1969)
-  Gender: Consolidated from self-reported gender identity and sex at birth
-  Race/Ethnicity: Combined and one-hot encoded to capture multiracial identities
-  In Progress: 
    -  Family History: Self-reported history of cancer
    -  Health behaviors: Smoking status, alcohol consumption, physical activity, sleep patterns
    -  Chronic conditions: EHR-derived indicators for obesity, diabetes, and cardiovascular disease
    -  Exposure History: Self-reported trauma from survey data

### Genomic Variables

- **Polygenic Risk Score (PRS)**:  
  Derived from multi-cancer GWAS summary statistics published in  
  [Sato et al., *Nature Communications*, 2023](https://www.nature.com/articles/s41467-023-39136-7).  
  This study conducted a pan-cancer and cross-population GWAS meta-analysis across 13 cancer types and identified shared genetic risk loci.

### Geographic Variables
-  ZIP-code Linked Cancer Prevalence: Mapped from CDC state-level cancer statistics

## Skills Used

- Querying and joining structured EHR and genomic data
- Survival analysis using Kaplan-Meier & Cox models
- Feature engineering from large-scale EHR and survey data
- Genomic data integration (PRS)
- Epidemiological cohort design
- Machine learning for clinical prediction

## Data Source
All data were accessed from the All of Us Researcher Workbench, including:
-  EHR (conditions, visits, observations)
-  Survey data (PPI modules on lifestyle, environment, and health history)
-  Genomic data (via summary statistics)
-  Geographic linkage (ZIP code-level SES and cancer prevalence)

