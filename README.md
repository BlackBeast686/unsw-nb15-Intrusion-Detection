# UNSW-NB15 Intrusion Detection

Benchmarking a range of machine learning models for **IoT network intrusion detection** on the **UNSW-NB15** dataset. Each model is trained on the same IoT-relevant feature set to classify network flows as **normal** or **attack** (binary), making it easy to compare approaches on identical data.

> **Note on scope:** These are research/experimental notebooks for comparing models, not a production intrusion-detection system.

## Task & data

- **Dataset:** UNSW-NB15 (`UNSW_NB15_training-set.csv` + `UNSW_NB15_testing-set.csv`), combined and re-split.
- **Task:** binary classification — normal (0) vs. attack (1).
- **Features:** an IoT-relevant subset of the flow features (duration, protocol, service, byte/packet counts, timing, etc.), with categorical columns label-encoded and features min-max scaled.

The dataset is **not** included in this repository — place the two CSVs at the paths referenced in the notebook (`/content/` on Colab) or update them. UNSW-NB15 is available from the Australian Centre for Cyber Security (ACCS).

## Models

The notebook trains and evaluates eight models, each in its own section:

1. K-Nearest Neighbors
2. Decision Tree
3. Naive Bayes (Gaussian)
4. Logistic Regression
5. Random Forest
6. XGBoost
7. Support Vector Machine (SVM)
8. Stacking Classifier (ensemble of the above)

Every model reports accuracy, precision, recall, F1, log loss, and ROC-AUC, with a confusion matrix and ROC curve.

## Results

Test-set metrics as reported in the notebook (single runs):

| Model | Accuracy | F1 | ROC-AUC |
|-------|----------|-----|---------|
| Stacking ensemble | 0.933 | 0.948 | 0.987 |
| XGBoost | 0.911 | 0.931 | 0.978 |
| Decision Tree | 0.910 | 0.932 | 0.979 |
| Random Forest | 0.907 | 0.926 | 0.978 |
| KNN | 0.898 | 0.922 | 0.940 |
| SVM | 0.897 | 0.925 | 0.971 |
| Naive Bayes | 0.866 | 0.902 | 0.895 |
| Logistic Regression | 0.853 | 0.893 | 0.904 |

> The stacking ensemble performs best overall. Figures are single runs — treat them as indicative rather than definitive.

## Requirements

Developed in Google Colab. Main dependencies:

- `scikit-learn`
- `xgboost`
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `torch`  *(used only for seed-setting / reproducibility)*

Install everything with:

```bash
pip install -r requirements.txt
```

## Getting started

1. Open the notebook in Google Colab or Jupyter.
2. Place `UNSW_NB15_training-set.csv` and `UNSW_NB15_testing-set.csv` at the paths used in the cells.
3. Run the cells for whichever models you want — each section is self-contained.

## Repository structure

```
.
├── Rauf_All_models.ipynb
└── README.md
```
