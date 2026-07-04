# Exploratory Research: Predicting MCI Conversion to Alzheimer's Disease

## Overview

This project performs exploratory data analysis on the ADNI (Alzheimer's Disease Neuroimaging Initiative) dataset to investigate factors associated with the progression from **Mild Cognitive Impairment (MCI)** to **Alzheimer's Disease (AD)**.

The notebook constructs a baseline cohort of MCI participants, labels whether each participant eventually converts to AD, and prepares demographic, clinical, cognitive, and biomarker features for downstream statistical analysis and machine learning.

---

## Objectives

- Identify participants diagnosed with MCI at baseline
- Determine whether each participant converts to Alzheimer's Disease during follow-up
- Extract baseline clinical and demographic information
- Merge cognitive assessments and plasma biomarker measurements
- Produce a clean dataset suitable for predictive modeling

---

## Dataset

The notebook uses multiple ADNI data tables, including:

### Enrollment
- Registry
- Roster
- Visits

### Clinical Assessments
- Diagnosis history
- ADAS-Cog
- CDR
- MMSE

### Demographics
- Subject characteristics

### Biomarkers
- UPENN Plasma Fujirebio / Quanterix measurements

---

## Methodology

### 1. Load Data

All required CSV files are loaded from the ADNI dataset.

### 2. Identify Baseline MCI Cohort

- Standardize visit codes
- Select baseline visits (`VISCODE == "bl"`)
- Keep participants with baseline diagnosis of MCI

### 3. Generate Conversion Labels

For each participant:

- Track all follow-up visits
- Identify whether Alzheimer's Disease (Diagnosis = 3) occurs
- Create a binary target variable:

| Label | Meaning |
|-------|---------|
| 0 | Stable MCI |
| 1 | Converted to Alzheimer's Disease |

### 4. Extract Baseline Features

Baseline variables include:

- ADAS13
- CDR Sum of Boxes
- MMSE
- Demographic information
- Clinical variables
- Plasma biomarkers

### 5. Merge Data

All baseline features are merged into a single participant-level dataset using the participant ID (`RID`).

---
## Data Availability

The datasets used in this project are **not included** in this repository.

To protect participant privacy and comply with the ADNI Data Use Agreement, the original research data has been excluded from version control. Users interested in reproducing this work should obtain access to the Alzheimer's Disease Neuroimaging Initiative (ADNI) dataset through the official ADNI data access process and place the required files in the appropriate project directories.

---

## Output

The notebook produces a participant-level dataset containing:

- Participant ID
- Baseline diagnosis
- Demographic variables
- Cognitive assessment scores
- Biomarker measurements
- Alzheimer's conversion label

This dataset can be used for:

- Exploratory data analysis
- Statistical testing
- Feature importance analysis
- Machine learning classification
- Survival or progression modeling

---

## Notes

- Participant matching is performed using the unique ADNI participant identifier (`RID`).
- Only baseline measurements are used as predictor variables.
- Alzheimer's conversion is determined using longitudinal diagnosis records.
