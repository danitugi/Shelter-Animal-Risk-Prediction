# 🐾 Predicting Risk in Shelter Animals
### Data Mining Course Project (2025)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![LightGBM](https://img.shields.io/badge/LightGBM-4.6-success?style=for-the-badge)
![CatBoost](https://img.shields.io/badge/CatBoost-1.2-yellow?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?style=for-the-badge&logo=Jupyter&logoColor=white)

> **Authors:** Kfir Diamond & Daniel Tugendhaft

> **Course:** Advanced Topics in ML / Data Mining

> **Link to data:** https://catalog.data.gov/dataset/louisville-metro-ky-animal-service-intake-and-outcome
---

## 📖 Overview
This project addresses a critical challenge in animal shelter management: identifying animals at high risk of negative outcomes upon intake. Using the **Louisville Metro KY Animal Service dataset**, we developed a predictive pipeline to classify animals as "At-Risk" (defined as outcomes of Euthanasia, Died, or Disposal).

The project combines advanced classification architectures with clustering techniques to create actionable risk profiles for shelter staff.

---

## 🛠️ Methodology & Feature Engineering
To handle the categorical nature and imbalance of the data, the following steps were implemented:
* **Preprocessing:** Cleaning of breed and color fields, and merging size categories (e.g., merging "PUPPY" and "KITTN" into a single high-vulnerability group).
* **Temporal Features:** Extraction of intake seasons to capture cyclical trends like "Kitten Season".
* **Imbalance Handling:** Implementation of **SMOTE** (Synthetic Minority Over-sampling Technique) within a pipeline to ensure high sensitivity toward the minority "At-Risk" class.

---

## 📊 Supervised Learning: Model Benchmark
We evaluated five distinct architectures, prioritizing **Recall** and **PR AUC** to ensure that high-risk cases are not overlooked.

| Model | Recall (Risk) | Precision | PR AUC | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **LightGBM** | **0.81** | 0.29 | **0.52** | 0.42 |
| **CatBoost** | **0.85** | 0.25 | 0.51 | 0.39 |
| **Random Forest** | 0.74 | 0.28 | 0.45 | 0.40 |
| **MLP (Neural Net)** | 0.48 | 0.41 | 0.43 | 0.44 |
| **Logistic Regression**| 0.62 | 0.26 | 0.35 | 0.37 |

*Note: LightGBM was selected as the final model due to the best balance between high recall and precision-recall area under the curve (PR AUC).*

---

## 🧩 Unsupervised Learning: Risk Profiling
A major focus of the recent analysis involved comparing clustering methods to identify "Risk Profiles" among the shelter population.

### Clustering Performance Comparison
We compared **K-Modes** (designed for categorical data) against **Hierarchical Clustering**.

| Metric | K-Modes | Hierarchical |
| :--- | :--- | :--- |
| **Silhouette Score** | **0.159** | 0.153 |
| **Cohesion (WSS)** | **164,638** | 172,742 |
| **Separation (BSS)** | 0.595 | **0.654** |

**Key Findings:**
* **K-Modes** proved superior in creating cohesive clusters for this categorical dataset.
* The analysis identified specific clusters with significantly higher mortality rates, allowing for targeted behavioral or medical interventions based on intake profiles.

---

## 📜 Conclusion
* **Sensitivity at Scale:** The LightGBM model successfully flags **81%** of at-risk animals immediately upon intake.
* **Proactive Intervention:** By combining classification with risk-profile clustering, shelters can allocate resources to the most vulnerable populations based on empirical evidence rather than intuition.
* **Vulnerability Factors:** Analysis confirmed that specific age/size categories (Puppy/Kitten) and intake types are the strongest predictors of medical and operational risk.

---
**Created by Kfir Diamond & Daniel Tugendhaft**