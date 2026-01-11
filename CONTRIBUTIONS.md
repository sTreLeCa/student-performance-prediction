# Team Member Contributions

This document outlines the individual responsibilities and contributions of each team member in the **Student Performance Prediction** project.  
All work was divided evenly and completed collaboratively, following an end-to-end data science workflow.

---

## 👤 Aleksandre Pluzhnikovi — Data Cleaning & Preprocessing

**Primary Responsibility:** Data preparation and preprocessing pipeline

**Deliverable:**
- `notebooks/01_data_cleaning.ipynb`
- `data/processed/student_cleaned.csv`

**Contributions:**
- Loaded the raw Student Performance dataset
- Inspected data quality and structure
- Handled missing values and verified data consistency
- Encoded categorical variables using one-hot encoding
- Scaled numerical features using `StandardScaler`
- Removed irrelevant or redundant features
- Generated a fully cleaned and model-ready dataset
- Saved the processed dataset to `/data/processed/student_cleaned.csv`
- Documented all preprocessing decisions for reproducibility

**Outcome:**
- Cleaned dataset containing **395 student records** and **42 features**
- Reproducible preprocessing pipeline used by all downstream tasks

---

## 👤 Sandro Saralidze — Exploratory Data Analysis (EDA & Visualization)

**Primary Responsibility:** Data exploration and visualization

**Deliverable:**
- `notebooks/02_eda_visualization.ipynb`
- Visual outputs saved to `report/figures/`

**Contributions:**
- Performed statistical summaries of key variables
- Analyzed grade distributions and variance
- Explored relationships between:
  - Study time and final grades
  - Parental education and student performance
  - Previous grades (G1, G2) and final outcomes
- Created clear and interpretable visualizations, including:
  - Histograms
  - Scatter plots with trend lines
  - Bar charts
  - Correlation heatmaps
  - Box plots for outlier detection
- Saved all figures in publication-ready format

**Outcome:**
- Identified key performance drivers
- Provided visual insights to guide modeling decisions

---

## 👤 Levan Mosiashvili — Regression Model (Final Grade Prediction)

**Primary Responsibility:** Regression modeling and evaluation

**Deliverable:**
- `notebooks/03_regression_model.ipynb`

**Contributions:**
- Implemented a **Linear Regression** model to predict final grade (G3)
- Performed an 80/20 train-test split
- Evaluated model performance using:
  - R² score
  - Mean Squared Error (MSE)
  - Root Mean Squared Error (RMSE)
- Analyzed regression coefficients for feature importance
- Created actual vs. predicted value visualizations
- Interpreted results and documented model behavior

**Outcome:**
- Achieved **R² = 0.724**, explaining 72.4% of grade variance
- Confirmed previous grades (G1, G2) as strongest predictors

---

## 👤 Andria Bibiashvili — Classification Model (Pass / Fail Prediction)

**Primary Responsibility:** Classification modeling and interpretability

**Deliverable:**
- `notebooks/04_classification_model.ipynb`

**Contributions:**
- Defined binary target variable:
  - Pass = G3 ≥ 10
  - Fail = G3 < 10
- Built a **Decision Tree Classifier** for interpretability
- Evaluated model using:
  - Accuracy
  - Precision
  - Recall
  - F1-score
  - Confusion matrix
- Visualized decision tree structure
- Analyzed feature importance for intervention planning
- Assessed generalization gap between training and testing data

**Outcome:**
- Achieved **87.3% accuracy** with **97.8% precision**
- Produced an interpretable model suitable for early-warning systems

---

## 🤝 Team Collaboration Summary

- All team members contributed equally and completed their assigned tasks
- Shared a common cleaned dataset and consistent project structure
- Coordinated notebook execution order (01 → 04)
- Maintained clear documentation and reproducibility
- Final project integrates preprocessing, EDA, regression, and classification into a cohesive pipeline

**Project Status:** ✅ All components completed successfully  
**Last Updated:** January 2026
