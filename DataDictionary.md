# 📘 Data Dictionary — Student Performance Dataset

This data dictionary describes all fields used in the final "Student Performance Prediction" project. It explains the meaning of each feature so that both technical and non-technical readers can understand the dataset.

---

## 🎯 Target Variables

| Feature | Description | Type | Range / Values | Example |
|---|---|---|---|---|
| `G3` | Final grade for the course | Integer | 0–20 | 14 |

---

## 📚 Academic & Study Features

| Feature | Description | Type | Values | Example |
|---|---|---|---|---|
| `studytime` | Weekly study time (ordinal scale) | Categorical (Ordinal) | 1: <2h, 2: 2–5h, 3: 5–10h, 4: >10h | 2 |
| `failures` | Number of past class failures | Integer | 0–3 | 1 |
| `schoolsup` | Extra educational support at school | Categorical (Binary) | yes/no | no |
| `famsup` | Family educational support | Categorical (Binary) | yes/no | yes |
| `higher` | Desires higher education | Categorical (Binary) | yes/no | yes |
| `absences` | Total school absences | Integer | 0–100+ | 6 |

---

## 👨‍👩‍👧 Socioeconomic & Family Features

| Feature | Description | Type | Values | Example |
|---|---|---|---|---|
| `sex` | Student gender | Categorical | M/F | F |
| `age` | Student age | Integer | 15–22 | 17 |
| `Medu` | Mother's education level | Categorical (Ordinal) | 0–4 | 3 |
| `Fedu` | Father's education level | Categorical (Ordinal) | 0–4 | 2 |
| `famrel` | Family relationship quality | Ordinal (1–5) | 1: very bad → 5: excellent | 4 |

---

## 🧠 Behavioral & Lifestyle Features

| Feature | Description | Type | Values | Example |
|---|---|---|---|---|
| `goout` | Frequency of social outings | Ordinal (1–5) | 1: low → 5: high | 3 |
| `Dalc` | Workday alcohol consumption | Ordinal (1–5) | 1: low → 5: high | 1 |
| `Walc` | Weekend alcohol consumption | Ordinal (1–5) | 1: low → 5: high | 2 |
| `health` | Current health status | Ordinal (1–5) | 1: very bad → 5: very good | 4 |

---

## 🏠 Housing & Commute Features

| Feature | Description | Type | Values | Example |
|---|---|---|---|---|
| `address` | Student living area | Categorical | U: urban, R: rural | U |
| `famsize` | Family size | Categorical | LE3: ≤3, GT3: >3 | GT3 |
| `traveltime` | Home-to-school travel time | Ordinal (1–4) | 1: <15m → 4: >1h | 2 |

---

## 🛠 Features Derived for Modeling

If additional features were engineered during preprocessing (e.g. for classification):

| Feature | Description | Type | Example |
|---|---|---|---|
| `passed` | Binary pass/fail label (threshold on G3) | Categorical | 1 (pass) |
| `G3_scaled` | Normalized version of G3 | Numeric | 0.54 |

---

## 📁 Dataset Context

- **Source:** UCI Student Performance Dataset
- **Prediction Tasks:**
  - Regression → Predict final numeric grade (`G3`)
  - Classification → Predict pass/fail label

---

## Notes for Interpretation

- Ordinal variables with numeric values (e.g. `studytime`, `failures`) represent ordered categories, not measured quantities.
- Binary variables are encoded as `"yes"/"no"` or `0/1` depending on preprocessing.
- Some features may have been encoded or scaled during preprocessing (see `01_data_cleaning.ipynb`).

---
