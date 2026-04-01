# TrueGrade 🌾
### AI-Based Automated Grain Quality Grading System

TrueGrade is a machine learning pipeline that predicts the quality grade of grain samples based on physical parameters — whole grain percentage, broken grain content, foreign matter, and moisture level. Built for the BioXcelerate Hackathon at JUIT.

---

## Problem Statement

Manual grain grading in agricultural supply chains is slow, inconsistent, and dependent on human expertise. TrueGrade automates this process using a trained classification model that assigns standardized grades (A+ to C) in real time from measurable grain parameters.

---

## How It Works

1. **Synthetic Dataset Generation** — 2,000 grain samples are generated with randomized parameters. Each sample is labeled with a grade (A+ through C) based on domain-defined thresholds for broken grain, foreign matter, and moisture.

2. **Model Training** — An XGBoost classifier is trained on 80% of the data, with StandardScaler normalization and label encoding applied. 

3. **Prediction** — Given new sensor or lab input values, the model predicts the grain grade and returns a confidence score.

4. **Visualization** — Feature importance plots and actual-vs-ideal comparison charts provide interpretability alongside the grade output.

---

## Grading Logic

| Grade | Broken Grain | Foreign Matter | Moisture |
|-------|-------------|----------------|----------|
| A+    | ≤ 2%        | ≤ 0.5%         | ≤ 11%    |
| A     | ≤ 5%        | ≤ 1%           | ≤ 12%    |
| B+    | ≤ 8%        | ≤ 2%           | ≤ 13%    |
| B     | ≤ 12%       | ≤ 3%           | ≤ 13.5%  |
| C+    | ≤ 18%       | ≤ 4%           | ≤ 14%    |
| C     | Above thresholds                          |

---

## Input Parameters

| Parameter       | Description                              |
|----------------|------------------------------------------|
| `whole_grain`   | Percentage of intact, undamaged grain    |
| `broken_grain`  | Percentage of broken/damaged kernels     |
| `foreign_matter`| Percentage of non-grain material         |
| `moisture`      | Moisture content percentage              |

---

## Sample Output

```
🔍 TRUEGRADE QUALITY REPORT
----------------------------
Predicted Grade : A
Confidence      : 97.43%

📊 Input Parameters
   whole_grain  broken_grain  foreign_matter  moisture
0         91.2           4.1             0.9      11.6
```

---

## Tech Stack

- **Python** — Core language
- **XGBoost** — Gradient boosted classifier
- **scikit-learn** — Preprocessing, train-test split, evaluation metrics
- **pandas / NumPy** — Data generation and manipulation
- **Matplotlib** — Visualization

---

## Setup & Usage

```bash
pip install pandas numpy scikit-learn xgboost matplotlib
```

Open `truegrade.ipynb` in Jupyter or Google Colab and run all cells sequentially.

To test with your own grain sample, update the `input_sample` dictionary in the prediction cell:

```python
input_sample = {
    "whole_grain": 91.2,
    "broken_grain": 4.1,
    "foreign_matter": 0.9,
    "moisture": 11.6
}
```

---

## Visualizations

- **Feature Importance Chart** — Shows which parameters most influence the grade prediction
- **Actual vs Ideal Bar Chart** — Compares the sample's values against A+ standard benchmarks

---

## Built At

**BioXcelerate Hackathon** — Jaypee University of Information Technology, January 2026  
Winner 🏆
