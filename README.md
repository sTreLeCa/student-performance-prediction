# Student Performance Prediction

An end-to-end machine learning project analyzing and predicting student academic performance using both regression and classification approaches.

## Project Overview

This project applies data science techniques to predict student academic outcomes based on demographic, social, and academic features. We implement both regression (grade prediction) and classification (pass/fail) models to provide comprehensive insights into factors affecting student performance.

**Dataset:** Student Performance Dataset (UCI ML Repository / Kaggle)
**Target Variables:**
- Final Grade (G3) - Regression task
- Pass/Fail Status - Classification task

## Team Members & Contributions

### Aleksandre Pluzhnikovi — Data Cleaning & Preprocessing
**Deliverable:** `01_data_cleaning.ipynb`

Responsibilities:
- Loaded raw student performance dataset
- Handled missing values and outliers
- Encoded categorical variables using one-hot encoding
- Normalized/scaled numeric features using StandardScaler
- Created cleaned dataset saved to `/data/processed/student_cleaned.csv`

**Key Achievements:**
- Successfully preprocessed 395 student records with 42 features
- Documented all data transformation decisions
- Established reproducible data pipeline

---

### Sandro Saralidze — Exploratory Data Analysis (EDA & Visualization)
**Deliverable:** `02_eda_visualization.ipynb`

Responsibilities:
- Analyzed grade distributions and statistical summaries
- Explored relationships between study time and final grades
- Investigated parental education impact on student performance
- Created correlation heatmaps and distribution plots
- Generated publication-quality visualizations

**Key Findings:**
- Previous grades (G1, G2) strongly correlate with final performance
- Study time shows positive but moderate correlation with grades
- Parental education level positively influences student outcomes
- Grade distribution shows reasonable variance suitable for prediction

**Visualizations Created:**
- Grade distribution histograms
- Study time vs grade scatter plots with trend lines
- Parental education impact bar charts
- Correlation heatmaps
- Box plots for outlier detection

All figures saved to `/report/figures/`

---

### Levan Mosiashvili — Regression Model (Predict Final Grade)
**Deliverable:** `03_regression_model.ipynb`

Responsibilities:
- Implemented Linear Regression model to predict numeric final grades (G3)
- Performed 80/20 train-test split
- Evaluated model using R², MSE, and RMSE metrics
- Analyzed feature importance through regression coefficients
- Created actual vs predicted visualizations

**Model Performance:**
- **R² Score:** 0.724 (72.4% variance explained)
- **RMSE:** 2.378 grade points
- **MSE:** 5.657

**Key Insights:**
- Previous period grades (G1, G2) are strongest predictors
- Academic history dominates prediction power
- Model achieves reasonable accuracy for grade forecasting

---

### Andria Bibiashvili — Classification Model (Pass / Fail)
**Deliverable:** `04_classification_model.ipynb`

Responsibilities:
- Defined pass/fail threshold (G3 >= 10 = Pass)
- Built Decision Tree classifier for binary classification
- Evaluated using accuracy, precision, recall, and confusion matrix
- Created decision tree visualizations
- Interpreted model behavior and feature importance

**Model Performance:**
- **Accuracy:** 0.873 (87.3%)
- **Precision:** 0.978 (97.8% - When predicting "Pass", correct 98% of the time)
- **Recall:** 0.830 (83.0% - Identifies 83% of students who actually pass)
- **F1-Score:** 0.900 (90.0% for Pass class)
- **Training Accuracy:** 95.6%
- **Testing Accuracy:** 87.3%
- **Generalization Gap:** 8.2% (Acceptable - good generalization)

**Confusion Matrix Results:**
- True Negatives: 25 (Correctly predicted Fail)
- False Positives: 1 (Incorrectly predicted Pass - very low!)
- False Negatives: 9 (Incorrectly predicted Fail)
- True Positives: 44 (Correctly predicted Pass)

**Key Features:**
- Highly interpretable model structure
- Feature importance analysis for intervention planning
- Visual decision tree showing exact prediction logic
- Practical threshold-based classification

**Interpretations:**
- Model successfully distinguishes passing from failing students
- Previous grades remain dominant predictors
- Study habits, failures, and absences show significant importance
- Results provide actionable insights for early intervention

---

## Project Structure

```
student-performance-prediction/
│
├── data/
│   ├── raw/                          # Original dataset (not tracked)
│   └── processed/
│       └── student_cleaned.csv       # Cleaned dataset
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb        # Person 1: Data preprocessing
│   ├── 02_eda_visualization.ipynb    # Person 2: EDA & visualizations
│   ├── 03_regression_model.ipynb     # Person 3: Grade prediction
│   └── 04_classification_model.ipynb # Person 4: Pass/fail classification
│
├── report/
│   └── figures/                      # Generated visualizations
│       ├── grade_distribution.png
│       ├── studytime_vs_g3.png
│       ├── correlation_heatmap.png
│       ├── confusion_matrix_classification.png
│       ├── feature_importance_classification.png
│       └── decision_tree_visualization.png
│
├── CONTRIBUTIONS.md                  # Members contributions
├── README.md                         # Project documentation
└── requirements.txt                  # Python dependencies

```

## Installation & Setup

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation Steps

1. Clone this repository:
```bash
git clone https://github.com/[your-username]/student-performance-prediction.git
cd student-performance-prediction
```

2. Install required packages:
```bash
pip install -r requirements.txt
```

3. Launch Jupyter Notebook:
```bash
jupyter notebook
```

4. Run notebooks in order (01 → 02 → 03 → 04)

## Required Dependencies

```
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=0.24.0
jupyter>=1.0.0
```

## Usage Examples

### Running Data Cleaning
```python
# From 01_data_cleaning.ipynb
import pandas as pd
from sklearn.preprocessing import StandardScaler

# Load, clean, and preprocess data
df = pd.read_csv('data/raw/student_data.csv')
# ... preprocessing steps ...
df.to_csv('data/processed/student_cleaned.csv', index=False)
```

### Training Regression Model
```python
# From 03_regression_model.ipynb
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

model = LinearRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
print(f"R² Score: {r2_score(y_test, predictions):.3f}")
```

### Training Classification Model
```python
# From 04_classification_model.ipynb
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score, confusion_matrix

# Create binary target
y = (df['G3'] >= 10).astype(int)

model = DecisionTreeClassifier(max_depth=5, random_state=42)
model.fit(X_train, y_train)
predictions = model.predict(X_test)

print(f"Accuracy: {accuracy_score(y_test, predictions):.3f}")
print(confusion_matrix(y_test, predictions))
```

## Results Summary

### Regression Model (Grade Prediction)
- **Approach:** Linear Regression
- **Target:** Numeric final grade (0-20)
- **Performance:** R² = 0.724, RMSE = 2.378
- **Best Predictors:** G1, G2, schoolsup_yes, absences

### Classification Model (Pass/Fail)
- **Approach:** Decision Tree (max_depth=5)
- **Target:** Binary (Pass = G3 >= 10, Fail = G3 < 10)
- **Performance:** Accuracy = 87.3%, Precision = 97.8%, Recall = 83.0%
- **Confusion Matrix:** TN=25, FP=1 (only 1 false positive!), FN=9, TP=44
- **Best Predictors:** G2, G1, failures, absences, studytime
- **Key Strength:** Very high precision (97.8%) means minimal false alarms when predicting "Pass"

### Combined Insights

Both models reveal that **academic history is the strongest predictor** of student performance:
1. **Previous grades (G1, G2)** dominate all predictions
2. **Failures and absences** negatively impact outcomes
3. **Study time** shows positive correlation
4. **Parental education** has moderate influence
5. **School support** appears beneficial

These findings suggest early intervention strategies should focus on:
- Monitoring first and second period performance
- Addressing attendance issues promptly
- Encouraging consistent study habits
- Providing support for students with previous failures

## Model Comparison

| Aspect | Regression Model | Classification Model |
|--------|------------------|---------------------|
| **Task** | Predict exact grade | Predict pass/fail |
| **Algorithm** | Linear Regression | Decision Tree |
| **Output** | Continuous (0-20) | Binary (0 or 1) |
| **Interpretability** | Moderate (coefficients) | High (visual tree) |
| **Use Case** | Grade forecasting | Early warning system |
| **Advantage** | Precise predictions | Clear actionable threshold |

**Recommendation:** Use both models together for comprehensive student performance analysis.

## Key Findings

1. **Previous Performance Matters Most**
   - First and second period grades are overwhelmingly predictive
   - Suggests early intervention is critical

2. **Behavioral Factors Are Important**
   - Study time, absences, and failures significantly affect outcomes
   - These are modifiable factors suitable for intervention

3. **Demographic Factors Have Moderate Influence**
   - Parental education shows positive correlation
   - Family support and school support contribute

4. **Model Performance is Practical**
   - Both models achieve performance suitable for decision support
   - Should be used to guide, not replace, human judgment

## Limitations & Future Work

### Current Limitations
- Dataset limited to specific student population
- Some features may not capture full student context
- Models assume linear/tree-based relationships
- No temporal dynamics (semester-by-semester tracking)

### Future Improvements
- **Ensemble Methods:** Combine multiple algorithms (Random Forest, Gradient Boosting)
- **Feature Engineering:** Create interaction terms, polynomial features
- **Hyperparameter Tuning:** Optimize model parameters using GridSearchCV
- **Cross-Validation:** Implement k-fold CV for robust performance estimates
- **Class Imbalance Handling:** Apply SMOTE or class weights if needed
- **Larger Dataset:** Incorporate more schools and demographics
- **Temporal Analysis:** Track student progression over multiple periods
- **External Factors:** Include socioeconomic indicators, school resources

## Acknowledgments

- **Dataset Source:** UCI Machine Learning Repository / Kaggle
- **Course:** Data Science with Python
- **Project Type:** Final Course Project
- **Project Duration:** 2-3 weeks

## License

This project is created for educational purposes as part of a Data Science course.

**Last Updated:** January 2026
**Status:** ✓ All four components completed (Data Cleaning, EDA, Regression, Classification)