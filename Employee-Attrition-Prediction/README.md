# Employee Attrition Prediction Models

## Project Overview

This project uses machine learning classification algorithms to predict employee attrition using the IBM HR Analytics Employee Attrition dataset. It compares multiple models, evaluates their performance, and identifies features that contribute to model predictions.

## Objectives

- Predict whether an employee is likely to leave the organization.
- Compare four classification algorithms.
- Evaluate models using Accuracy, Precision, Recall, F1-Score, and ROC-AUC.
- Apply cross-validation and hyperparameter tuning.
- Analyze feature importance and interpret the results.
- Provide business insights to support employee-retention planning.

## Dataset

- Dataset: IBM HR Analytics Employee Attrition
- Records: 1,470
- Original columns: 35
- Target variable: `Attrition`
- Classes: `Yes` and `No`

The dataset contains employee demographics, job information, compensation-related fields, work history, and satisfaction-related features.

## Machine Learning Models

The project evaluates these classifiers:

1. Logistic Regression
2. Decision Tree
3. Random Forest
4. XGBoost

Hyperparameter tuning is performed for Logistic Regression and Random Forest using GridSearchCV and five-fold stratified cross-validation.

## Model Evaluation Results

The following results were measured on the held-out test set.

| Model | Version | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---|---:|---:|---:|---:|---:|
| Logistic Regression | Baseline | 0.7517 | 0.3488 | 0.6383 | 0.4511 | 0.8032 |
| Decision Tree | Baseline | 0.7789 | 0.3043 | 0.2979 | 0.3011 | 0.5842 |
| Random Forest | Baseline | 0.8401 | 0.5000 | 0.3404 | 0.4051 | 0.7998 |
| XGBoost | Baseline | 0.8571 | 0.6667 | 0.2128 | 0.3226 | 0.7911 |
| Logistic Regression | Tuned | 0.7687 | 0.3765 | 0.6809 | 0.4848 | 0.8120 |
| Random Forest | Tuned | 0.8265 | 0.4524 | 0.4043 | 0.4270 | 0.7837 |

## Key Findings

- Tuned Logistic Regression achieved the highest Recall, F1-Score, and ROC-AUC among the six evaluated model versions.
- Baseline XGBoost achieved the highest Accuracy and Precision.
- Monthly Income, Age, Total Working Years, Daily Rate, and Years at Company were the five highest-ranked features in the tuned Random Forest model.
- The tuned Logistic Regression confusion matrix showed 32 correctly identified attrition cases, 15 missed attrition cases, and 53 false-positive predictions.

Tuned Logistic Regression is the preferred candidate when detecting more potential attrition cases is the priority. The final choice depends on the business cost of false positives versus missed cases.

## Project Structure

```text
Employee-Attrition-Prediction/
├── data/
│   ├── README.md
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
├── models/
├── notebooks/
│   └── employee_attrition_prediction.ipynb
├── reports/
│   ├── evaluation_report.md
│   ├── business_interpretation_report.md
│   └── final_model_comparison.csv
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

## Installation and Usage

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd Employee-Attrition-Prediction
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your actual repository URL.

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Open Jupyter Notebook

```bash
jupyter notebook
```

Open `notebooks/employee_attrition_prediction.ipynb` and run the cells in order.

## Reports

- `reports/evaluation_report.md` — model evaluation and comparison.
- `reports/business_interpretation_report.md` — business findings and responsible-use recommendations.
- `reports/final_model_comparison.csv` — machine-readable test-set results.

## Limitations and Responsible Use

Predictions are estimates and may be wrong. Feature importance indicates predictive contribution, not causation. Employee data can be sensitive, and model predictions should not be used as the sole basis for employment decisions. Fairness, privacy, and performance should be evaluated before any real-world deployment.

## Author

Atul Gaikwad

## Disclaimer

This project is for educational and research purposes. It is not a validated HR decision-making system.
