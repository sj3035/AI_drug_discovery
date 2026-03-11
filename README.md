# AI-Driven Drug Discovery Pipeline for Neglected Tropical Diseases

An end-to-end **computational drug discovery framework** that leverages **machine learning, cheminformatics, and large-scale virtual screening** to identify potential therapeutic compounds for **Neglected Tropical Diseases (NTDs)** such as **Dengue** and **Tuberculosis**.

This project demonstrates how **artificial intelligence can accelerate early-stage drug discovery** by predicting the biological activity of chemical compounds and prioritizing promising drug candidates before expensive laboratory testing.

---

## Project Overview

Drug discovery is traditionally a **time-consuming and expensive process**, often requiring over **10–15 years and billions of dollars** to bring a drug to market. Neglected Tropical Diseases (NTDs) receive limited research investment despite affecting millions of people globally.

This project proposes an **AI-driven in-silico pipeline** that reduces experimental workload by predicting compound activity using **Quantitative Structure–Activity Relationship (QSAR) modeling**.

The pipeline performs:

1. **Bioactivity Data Acquisition**
2. **Chemical Structure Processing**
3. **Molecular Feature Extraction**
4. **Machine Learning Model Training**
5. **Model Validation**
6. **Virtual Screening of Compound Libraries**
7. **Drug-like Candidate Identification**

The output is a ranked list of **high-confidence candidate molecules** for further experimental validation.

---

## Key Features

- Automated **bioactivity data extraction from ChEMBL**
- **Chemical structure standardization** using RDKit
- Molecular representation using **ECFP4 fingerprints**
- Multiple **machine learning regression models**
- Model performance evaluation using **cross-validation**
- **Virtual screening** of large chemical libraries
- Drug-likeness filtering using **Lipinski's Rule of Five**
- Scaffold diversity analysis to ensure chemical novelty
- Identification of promising **drug-like candidate compounds**

---

## System Architecture

The pipeline consists of the following stages:

```
ChEMBL Database
↓
Data Curation & Preprocessing
↓
Molecular Fingerprint Generation (ECFP4)
↓
Machine Learning Model Training
↓
Model Evaluation & Selection
↓
Virtual Screening of Chemical Libraries
↓
Drug-Like Candidate Identification
```

---

## Methodology

### 1. Data Acquisition

Bioactivity data for selected targets were retrieved from the **ChEMBL database**, which contains experimentally validated chemical–biological interaction data.

Targets selected:

- **Dengue Virus NS5 RNA Polymerase**
- **Dengue Virus NS2B–NS3 Protease**
- **Mycobacterium tuberculosis InhA enzyme**

---

### 2. Data Preprocessing

The following preprocessing steps were performed:

- Removal of invalid molecular structures
- Filtering of **IC50 values in nanomolar units**
- Conversion of IC50 to **pIC50 values**
- Deduplication of compounds
- Standardization of SMILES representations

Formula used:

```
pIC50 = 9 − log10(IC50 [nM])
```

---

### 3. Molecular Representation

Chemical compounds are converted into **Extended Connectivity Fingerprints (ECFP4)**.

Characteristics:

- Radius = 2
- Diameter = 4
- 2048-bit fingerprint vector

These fingerprints capture **local atomic environments** and are widely used in QSAR modeling.

---

### 4. Machine Learning Models

The project evaluates multiple supervised regression algorithms:

- **Random Forest Regressor**
- **Support Vector Regression (SVR)**
- **XGBoost Regressor**

Training strategy:

- 80/20 train-test split
- 5-fold cross-validation
- Hyperparameter tuning

Evaluation metrics:

- R² Score
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)

---

### 5. Virtual Screening

After model training, the best-performing model is used to screen **large compound libraries**.

Filtering criteria:

- Molecular Weight: 200–500 Da
- LogP: −1 to 5
- Synthetic Accessibility < 6
- Absence of toxic substructures

High-confidence hits are identified using:

```
pIC50 ≥ 6.5
```

These compounds are considered potential **drug-like candidates**.

---

## Technology Stack

**Programming Language**

- Python

**Libraries**

- RDKit
- Scikit-learn
- XGBoost
- Pandas
- NumPy
- Matplotlib

**Data Sources**

- ChEMBL Database
- ZINC15 Compound Library

---

## Project Structure

```
project-root/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── data_preprocessing.ipynb
│   ├── feature_engineering.ipynb
│   └── model_training.ipynb
│
├── models/
│   └── trained_models/
│
├── src/
│   ├── data_processing.py
│   ├── fingerprint_generation.py
│   ├── model_training.py
│   └── virtual_screening.py
│
├── results/
│   ├── model_metrics/
│   └── screening_hits/
│
└── README.md
```

---

## Example Results

Model performance observed during experiments:

| Target | Best Model | R² Score |
|--------|------------|----------|
| Dengue NS5 | Random Forest | ~0.76 |
| NS2B–NS3 | Random Forest | ~0.79 |
| InhA | Random Forest | ~0.82 |

Virtual screening identified **200+ potential candidate molecules per target**.

---

## Research Contribution

This work demonstrates how **open-source datasets and machine learning tools can be used to accelerate drug discovery**, particularly for diseases that receive limited commercial research investment.

The framework is designed to be:

- Reproducible
- Scalable
- Accessible for academic researchers

---

## Funding and Acknowledgement

This research project was developed under the **IndiaAI Fellowship** supported by the **Ministry of Electronics and Information Technology (MeitY), Government of India**, with a research grant of **₹1,00,000**.

---

## Future Work

Planned improvements include:

- Deep learning models for molecular representation
- Graph Neural Networks for chemical structure learning
- Molecular docking integration
- ADMET property prediction
- De novo molecule generation using generative models

---

## Author

**S. Jayanth**  
B.Tech Computer Science and Engineering  
SRM Institute of Science and Technology, Tiruchirappalli  

LinkedIn: https://www.linkedin.com/in/s-jayanth-10859a266/

GitHub: https://github.com/sj3035

---

## License

This project is released for **research and educational purposes**.
