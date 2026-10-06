<h1 align="center">AutoML-Tool</h1>

<p align="center">
  <strong>Guided Python Shiny prototype for end-to-end tabular machine-learning workflows.</strong><br>
  Upload data, preprocess it, encode categories, generate polynomial features, compare baseline models, select a model, and produce predictions through one interactive interface.
</p>

<p align="center">
  <img alt="Status" src="https://img.shields.io/badge/status-prototype-blue">
  <img alt="Python" src="https://img.shields.io/badge/language-Python-3776AB">
  <img alt="Framework" src="https://img.shields.io/badge/framework-Shiny-informational">
  <img alt="ML" src="https://img.shields.io/badge/ML-scikit--learn-orange">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-green">
</p>

<p align="center">
  <a href="#overview">Overview</a> ·
  <a href="#what-this-repo-contains">Contents</a> ·
  <a href="#implemented-workflow">Workflow</a> ·
  <a href="#models-and-preprocessing">Models</a> ·
  <a href="#run-locally">Run Locally</a>
</p>

---

## Overview

**AutoML-Tool** is a compact Python Shiny application that exposes a guided tabular-ML workflow through a browser interface.

The current application is implemented primarily in <code>app.py</code> and combines data preparation, feature transformation, baseline model comparison, model selection, and interactive prediction.

~~~text
Upload dataset
   ↓
Prepare columns / missing values
   ↓
Encode categorical data
   ↓
Optional polynomial features
   ↓
Select target / features
   ↓
Train and compare baseline models
   ↓
Choose a fitted model
   ↓
Enter feature values and predict
~~~

It is an educational AutoML-style prototype, not a production AutoML platform or managed model-training service.

---

## What This Repo Contains

| File | Purpose |
|---|---|
| <code>app.py</code> | Shiny UI/server, preprocessing helpers, model training/comparison, and prediction workflow. |
| <code>how-to-run.txt</code> | Minimal dependency and launch instructions. |
| <code>README.md</code> | Project documentation. |
| <code>LICENSE</code> | MIT License. |

---

## Implemented Workflow

| Stage | Implementation |
|---|---|
| Data upload | Tabular dataset ingestion through the Shiny interface. |
| Missing values | Interactive preprocessing path for handling missing data. |
| Type handling | User-guided feature/data-type adjustments. |
| Categorical encoding | <code>OneHotEncoder</code> and <code>LabelEncoder</code>. |
| Feature expansion | Degree-2 <code>PolynomialFeatures</code> support for selected inputs. |
| Feature selection | User-controlled feature selection before training. |
| Train/test split | scikit-learn <code>train_test_split</code>. |
| Regression baselines | <code>LinearRegression</code> and <code>RandomForestRegressor</code>. |
| Classification baselines | <code>LogisticRegression</code>, linear-kernel <code>SVC</code>, and <code>RandomForestClassifier</code>. |
| Model comparison | Candidate models are trained and evaluated for the selected task. |
| Prediction | A fitted selected model receives values from dynamically generated inputs. |

---

## Models and Preprocessing

~~~text
pandas
NumPy
scikit-learn
├── preprocessing
│   ├── OneHotEncoder
│   ├── LabelEncoder
│   └── PolynomialFeatures
├── linear_model
│   ├── LogisticRegression
│   └── LinearRegression
├── ensemble
│   ├── RandomForestRegressor
│   └── RandomForestClassifier
├── svm
│   └── SVC
└── model_selection
    └── train_test_split
~~~

The tool does not claim automatic hyperparameter optimization, experiment tracking, production model registry, or universal task inference.

---

## User Flow

~~~text
Launch app
   ↓
Upload dataset
   ↓
Configure preprocessing
   ↓
Choose target and features
   ↓
Generate optional polynomial features
   ↓
Train / compare available models
   ↓
Select model
   ↓
Enter prediction values
   ↓
View predicted output
~~~

---

## Architecture

~~~text
app.py
├── Data/preprocessing helpers
├── Feature transformation helpers
├── Model training/comparison helpers
├── Prediction helper
├── Shiny UI
└── Shiny server / reactive workflow
~~~

The implementation uses module-level mutable workflow state in places. That is acceptable for a local learning prototype, but it should not be treated as evidence of safe multi-user isolation for a hosted production service.

---

## Repository Structure

~~~text
AutoML-Tool/
├── app.py
├── how-to-run.txt
├── README.md
└── LICENSE
~~~

---

## Run Locally

~~~bash
pip install shiny pandas scikit-learn numpy
shiny run --reload app.py
~~~

---

## Validation & Current Maturity

AutoML-Tool is a **functional learning prototype**.

The repository currently has no automated tests, package metadata, pinned environment, model-registry contract, experiment database, hyperparameter-search framework, model-card layer, or production deployment configuration.

Model quality depends on the uploaded dataset, target definition, preprocessing choices, and baseline algorithms used.

---

## Important Notes

- A comparison score on an uploaded dataset is not proof of deployment-grade generalization.
- Users should inspect class balance, leakage, data quality, and train/test methodology before interpreting results.
- Healthcare, finance, or other high-impact datasets require domain-specific validation beyond this prototype.
- Polynomial expansion can increase feature count quickly and should be used deliberately.

---

## License

Released under the **MIT License**. See <code>LICENSE</code>.
