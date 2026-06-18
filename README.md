# House Price Prediction

A machine learning project that predicts residential property prices using structured housing data. The full workflow—data cleaning, exploratory analysis, feature engineering, model training, evaluation, and visual reporting—is implemented in a single Jupyter Notebook.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [Repository Structure](#repository-structure)
- [Tech Stack](#tech-stack)
- [Workflow](#workflow)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Evaluation Metrics](#evaluation-metrics)
- [Results](#results)
- [Key Insights](#key-insights)
- [Future Work](#future-work)
- [Author](#author)

---

## Project Overview

This project builds a supervised regression pipeline to estimate house prices from structural features such as area, bathrooms, bedrooms, stories, parking, and amenities (e.g., air conditioning, guest room, basement).

Two models are benchmarked:

- **Linear Regression** (baseline)
- **Random Forest Regressor** (ensemble)

The goal is to compare performance and identify the model that generalizes best on this compact real-estate dataset.

---

## Problem Statement

Residential property valuation is often subjective and inconsistent. This project addresses that by using data preprocessing and regression models to estimate prices using objective property attributes.

---

## Objectives

- Clean and validate raw housing data (missing values, duplicates)
- Encode categorical variables for model compatibility
- Split data into train/test sets (80/20)
- Train and compare multiple regression models
- Evaluate model performance with standard regression metrics
- Visualize feature relationships and prediction behavior

---

## Repository Structure

```text
house-price-prediction/
│
├── .gitignore
├── README.md
├── analysis.ipynb
├── Housing.csv
├── summary.pdf
└── charts/
    ├── actual_vs_predicted.png
    ├── correlation_heatmap.png
    └── price_distribution.png
```

---

## Tech Stack

- **Language:** Python 3.x (Jupyter Notebook)
- **Data Analysis:** pandas, numpy
- **Machine Learning:** scikit-learn
- **Visualization:** matplotlib, seaborn

---

## Workflow

1. **Data Loading & Exploration**
   - Import `Housing.csv`
   - Inspect dataset shape, data types, and summary statistics

2. **Data Cleaning**
   - Check missing values
   - Remove duplicates

3. **Preprocessing**
   - One-hot encode categorical features
   - Prepare features (`X`) and target (`y`)

4. **Train-Test Split**
   - 80/20 split with fixed `random_state`

5. **Model Training**
   - Train Linear Regression
   - Train Random Forest Regressor

6. **Evaluation & Visualization**
   - Compute MAE, RMSE, and R²
   - Generate plots for distribution, correlations, and predictions

---

## Dataset

- **Source:** Kaggle Housing Prices Dataset
- **Rows:** 545
- **Columns:** 13
- **Target Variable:** `price`

### Key Input Features

`area`, `bedrooms`, `bathrooms`, `stories`, `mainroad`, `guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `parking`, `prefarea`, `furnishingstatus`

---

## Installation

### 1) Clone the repository

```bash
git clone https://github.com/ishanpote/house-price-prediction.git
cd house-price-prediction
```

### 2) Create and activate a virtual environment

**Windows (PowerShell):**

```bash
python -m venv .venv
.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3) Install dependencies

```bash
pip install jupyter pandas numpy matplotlib seaborn scikit-learn
```

### 4) Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `analysis.ipynb` and run all cells in sequence.

---

## Usage

The complete pipeline is contained in `analysis.ipynb`. Running the notebook performs preprocessing, model training, evaluation, and chart generation.

Generated plots are saved in the `charts/` directory.

---

## Evaluation Metrics

The models are evaluated using:

- **MAE (Mean Absolute Error):** Average absolute prediction error
- **RMSE (Root Mean Squared Error):** Penalizes larger errors more strongly
- **R² Score (Coefficient of Determination):** Proportion of variance explained

---

## Results

Train-test split:

- **Training set:** `(436, 13)`
- **Test set:** `(109, 13)`

| Metric | Linear Regression | Random Forest Regressor |
|---|---:|---:|
| MAE | 970,043.40 | 1,021,546.04 |
| RMSE | 1,324,506.96 | 1,400,565.97 |
| R² Score | **0.6529** | 0.6119 |

### Conclusion

Linear Regression performs better on this dataset and provides stronger generalization compared with Random Forest in the current configuration.

---

## Key Insights

- **Strongest drivers of price:**
  - `area` (correlation ≈ 0.54)
  - `bathrooms` (correlation ≈ 0.52)
- **Bedrooms vs amenities:** Bedrooms show weaker correlation (~0.37) than amenities such as air conditioning (~0.45).
- **Distribution behavior:** Price is right-skewed, with most homes concentrated between approximately 3,000,000 and 5,500,000, and a smaller luxury tail beyond 12,000,000.

### Practical Recommendation

For renovation or investment strategy, prioritize improvements that increase utility and perceived quality (bathroom upgrades, open layouts, climate-control amenities) over simply adding low-value room partitions.

---

## Future Work

- Apply target transformation (e.g., `log1p(price)`) to reduce skewness
- Evaluate regularized linear models (Ridge/Lasso)
- Tune Random Forest hyperparameters via cross-validation
- Add a lightweight deployment interface (Streamlit/Gradio)

---

## Author

**Ishan Pote**  
GitHub: [@ishanpote](https://github.com/ishanpote)
