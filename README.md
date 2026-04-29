# ADEGuard 🛡️ (Working on this project)
### AI-Powered Adverse Drug Event Detection & Severity Mapping

ADEGuard is an end-to-end AI/ML system designed to detect Adverse Drug Events (ADEs) from VAERS (Vaccine Adverse Event Reporting System) reports. Since the COVID-19 pandemic, mass vaccinations have led to a significant rise in adverse event reporting. This project leverages Natural Language Processing (NLP) to automatically extract drug and symptom information and classify the severity of reactions — transforming unstructured clinical narratives into actionable safety insights.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation & Usage](#installation--usage)
- [Data](#data)
- [Acknowledgments](#acknowledgments)

---

## Project Overview

ADEGuard targets COVID-19 related VAERS reports (2020–2025) and applies a multi-stage NLP pipeline to:

1. **Extract** named entities — drug names and adverse drug events — from free-text symptom narratives.
2. **Classify** severity levels (Mild, Moderate, Severe) using clinical flags such as Death, Life-Threatening, and Hospitalization.
3. **Explain** predictions using Explainable AI (XAI) techniques, making outputs audit-ready for healthcare providers, regulators, and pharmaceutical companies.

The system is designed for real-time pharmacovigilance and post-market drug safety monitoring.

---

## Key Features

- **COVID-19 Focused Filtering** — Targets reports from 2020–2025 for consistent, relevant analysis.
- **Custom Severity Engine** — Generates training labels from clinical outcome flags (e.g., Death, Hospitalization, Life-Threatening).
- **Named Entity Recognition (NER)** — Extracts exact DRUG and ADE mentions following strict clinical annotation guidelines.
- **Explainable AI (XAI)** — SHAP and LIME integrations provide token-level explanations for regulatory and clinical review.
- **Interactive Dashboard** — Streamlit UI with token-level highlights, symptom clustering plots, and explainability visualizations.

---

## Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| NLP / NER | BioBERT, SciSpaCy |
| Transformers | HuggingFace Transformers |
| Clustering | HDBSCAN + Sentence-BERT |
| XAI | SHAP, LIME |
| Dashboard | Streamlit |
| Annotation | Label Studio |

---

## Project Structure

```
ADEGuard/
├── data/
│   ├── raw/                              # Original VAERS CSV files (excluded — see Data section)
│   └── processed/                        # Filtered COVID-19 reports & gold standard labels
├── notebooks/
│   ├── 01_data_merging_cleaning.ipynb    # Merging 5 years of VAERS data
│   ├── 02_data_preparation.ipynb         # Make the data clean and ready for model
│   ├── 03_baseline_model.ipynb           # TF-IDF & Logistic Regression baseline
│   └── 04_annotation_prep.ipynb          # Data sampling and labeling setup  
├── src/
│   ├── preprocessing/                    # Data cleaning and COVID-19 filtering
│   ├── training/                         # NER and classification training pipelines
│   └── inference/                        # Ready-to-use prediction scripts
├── models/                               # Saved model weights (.pt) and tokenizers
├── docs/                                 # Annotation guidelines and project documentation
├── app.py                                # Streamlit dashboard
├── requirements.txt                      # Environment dependencies
└── README.md
```

---

## Installation & Usage

### 1. Clone the repository

```bash
git clone https://github.com/your-username/ADEGuard.git
cd ADEGuard
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the dashboard

```bash
streamlit run app.py
```

---

## Data

The raw VAERS data used in this project is publicly available from the official VAERS Data Portal:

> **https://vaers.hhs.gov/data/datasets.html**

Due to GitHub's file size limitations, the merged dataset (~1.5 GB) is **not** included in this repository. To reproduce it:

1. Download the raw annual CSV files from the link above.
2. Place them in `data/raw/`.
3. Run `notebooks/01_data_merging_cleaning.ipynb` to filter for COVID-19 reports and apply the cleaning pipeline.

The processed output will be saved to `data/processed/` and is ready for use in subsequent notebooks and training scripts.

---

## Acknowledgments

This project was developed as part of the **Codebasics Resume Project Challenge** for **CureviaAI**.

Special thanks to:
- **Tony Sharma** (CIO, CureviaAI) — for the project vision and problem statement.
- **The CDC and FDA** — for maintaining the VAERS public dataset.
- **The Codebasics Team** — for providing resources and challenge infrastructure.

---

> **Disclaimer:** ADEGuard is a research and demonstration project. It is not intended for clinical decision-making or regulatory submission without proper validation by qualified professionals.