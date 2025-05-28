# Mercedes-Benz Greener Manufacturing

A machine learning project to optimize and reduce the time Mercedes-Benz vehicles spend on the test bench, improving production efficiency and reducing carbon emissions.

---

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Dataset](#dataset)
- [Approach & Methodology](#approach--methodology)
  - [Data Preparation](#data-preparation)
  - [Dimensionality Reduction](#dimensionality-reduction)
  - [Modeling](#modeling)
- [Results](#results)
- [Workflow Summary](#workflow-summary)
- [How to Run](#how-to-run)
- [Key Takeaways](#key-takeaways)
- [License](#license)

---

## Overview

The **Mercedes-Benz Greener Manufacturing** project uses machine learning to predict and minimize the time cars spend on the test bench. By reducing testing time, Mercedes-Benz can streamline production, lower costs, and decrease carbon emissions, all while maintaining high safety and quality standards.[1][3][5]

---

## Problem Statement

Mercedes-Benz’s rigorous testing process can lead to delivery delays and increased operational costs. The aim is to use data-driven methods to predict and minimize the time a car spends on the testing bench, thus enhancing efficiency and sustainability in manufacturing.[1][5]

---

## Dataset

- **Rows:** 4,209 (each representing a car/test)
- **Features:** 378 anonymized columns (binary, categorical, ordinal, numerical)
  - 369 binary columns (test characteristics)
  - 8 categorical columns (car characteristics)
  - 1 numerical ID column
- **Target Variable:** `y` — time a car spends on the test bench (in seconds)[1][2][3]

---

## Approach & Methodology

### Data Preparation

- Checked for and confirmed no null values.
- Removed outliers (~1% of data) and features with zero variance or high correlation.
- One-hot encoded categorical variables, increasing feature count post-encoding (up to 412 features).[1][2]

### Dimensionality Reduction

High dimensionality was addressed using:
- **Feature Selection:** Top 30% features based on F-value scores (reduced to 124 features).
- **Feature Extraction:** Created new features by decomposition (e.g., NMF, reduced to 123 features).
- **Principal Component Analysis (PCA):** Reduced features while retaining 85% variance (to 79 features).
- **Autoencoders:** Neural networks compressed features into a lower-dimensional space (to 32 features).[1]

### Modeling

Evaluated five regression models:
- **K-Nearest Neighbors (KNN)**
- **Neural Network (MLPRegressor)**
- **Random Forest**
- **XGBoost**
- **Linear Regression**

Performance was measured using R² (coefficient of determination) and Mean Squared Error (MSE).[1][2][6]

---

## Results

| Dim. Reduction | XGBoost | Random Forest | KNN   | Neural Net | Linear Reg. |
| -------------- | ------- | ------------ | ----- | ---------- | ----------- |
| PCA            | 53.73%  | 50.18%       | 48.05%| 47.47%     | 56.24%      |
| Feature Select | 62.5%   | 50.8%        | 53.76%| 53.59%     | 58.84%      |
| Feature Extr.  | 58.80%  | 57.37%       | 32.85%| 56.64%     | 60.22%      |
| Autoencoder    | 52.95%  | 50.34%       | 46.47%| 49.33%     | 48.50%      |

- **Best Performance:** XGBoost with Feature Selection (R² = 62.5%, lowest MSE ≈ 48.7)
- **Key Insight:** Dimensionality reduction, especially feature selection, significantly improved model accuracy and efficiency.[1]

---

## Workflow Summary

1. **Load and Inspect Data**
2. **Remove Nulls, Outliers, and Redundant Features**
3. **Encode Categorical Variables**
4. **Apply Dimensionality Reduction**
5. **Train Multiple Regression Models**
6. **Evaluate and Compare Results**
7. **Select Best Model (XGBoost + Feature Selection) for Prediction**[1][2][6]

---

## How to Run

1. **Clone the Repository**
- git clone https://github.com/Yashtated/Mercedes--Benz-Greener-Manufacturing--

2. **Install Dependencies**
- Python 3.x
- pandas, numpy, scikit-learn, xgboost, tensorflow, matplotlib, seaborn

3. **Prepare Data**
- Place the provided dataset CSV files in the project directory.

4. **Run the Notebook or Script**
- Open and execute the Jupyter notebook (`Group-7-Project-5.ipynb`) or run the Python scripts as provided.

5. **Results**
- The notebook will output model performance metrics and visualizations.
- The best model (XGBoost with feature selection) can be used to predict testing times for new data.[2]

---

## Key Takeaways

- **Dimensionality reduction** is crucial for handling high-dimensional manufacturing data.
- **XGBoost** with feature selection delivers the most accurate predictions for test bench time.
- **Efficient modeling** can directly contribute to operational efficiency and sustainability in automotive manufacturing.[1][6]

---

## License

This project is for academic and educational purposes only.

