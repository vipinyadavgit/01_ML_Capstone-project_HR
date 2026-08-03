
# 🏢 HR Employee Attrition Prediction

#   Goal
> *Predicting whether an employee will leave — and understanding why.*

---

## 📌 Overview

Employee attrition costs organizations time, money, and institutional knowledge. This project tackles that problem using machine learning — not just predicting *who* will leave, but identifying *what's driving* those decisions and giving HR teams something they can actually act on.

Built as a full Data Science capstone, this project covers every step from raw data to business recommendations.

---

## 🎯 Business Problem

| Item | Detail |
|---|---|
| **Client** | HR Department — Mid-size Enterprise |
| **Problem** | Rising employee attrition causing high hiring costs and productivity loss |
| **ML Task** | Binary Classification — Predict Attrition: Yes / No |
| **Success Metric** | F1-Score (primary), Accuracy ≥ 80% |
| **Key Deliverable** | Explainable model + actionable HR recommendations |

---

## 🗂️ Project Structure

```
ML Capstone project/
│
├── 📁 dataset/
│   └── HR-Employee-Attrition.csv        → 1470 employees, 35 features
│
├── 📁 docs/
│   ├── HR attrition BRD.docx            → Business Requirement Document
│   ├── Final capstone project.docx      → Project brief & assignment
│   ├── ML rule book.md                  → Step-by-step technical rules
│   └── Sample Project Document.pdf      → Reference output format
│
├── 📁 output_plots/
│   ├── 01_outlier_boxplots.png
│   ├── 02_target_distribution.png
│   ├── 03_univariate_numerical.png
│   ├── 04_univariate_categorical.png
│   ├── 05_bivariate_categorical_vs_attrition.png
│   ├── 06_bivariate_numerical_vs_attrition.png
│   ├── 07_correlation_heatmap.png
│   └── 08_feature_importance.png        → Top 15 drivers of attrition
│
├── 📄 hr_attrition_prediction.py        → Main script (run this)
├── 📄 Readme.md                         → You are here
└── 📁 .venv/                            → Virtual environment
```

---

## 🚀 How to Run

**1. Activate the virtual environment**
```bash
.venv\Scripts\Activate.ps1
```

**2. Run the script**
```bash
python hr_attrition_prediction.py
```

All output prints to the terminal. All 8 plots are saved automatically to `output_plots/`.

---

## 📊 What the Script Does — Step by Step

```
STEP 1  →  Import Libraries
STEP 2  →  Load Dataset                    (1470 rows × 35 columns)
STEP 3  →  Exploratory Data Analysis
           ├── Basic info, shape, dtypes
           ├── Drop useless columns         (EmployeeNumber, EmployeeCount, Over18, StandardHours)
           ├── Null & duplicate check
           ├── Outlier detection (IQR)      (10 columns flagged)
           ├── Univariate analysis          (histograms + bar charts)
           ├── Bivariate analysis           (feature vs Attrition)
           └── Correlation heatmap
STEP 4  →  Feature Engineering
           ├── Encode target: Yes=1, No=0
           ├── Binary encoding              (Gender, OverTime)
           ├── Ordinal encoding             (BusinessTravel)
           └── One-Hot Encoding             (Department, EducationField, JobRole, MaritalStatus)
STEP 5  →  Model Building                  (5 models trained)
STEP 5b →  5-Fold Stratified Cross-Validation
STEP 5c →  Hyperparameter Tuning           (GridSearchCV)
STEP 6  →  Model Evaluation                (Accuracy, Precision, Recall, F1, Confusion Matrix)
STEP 7  →  Feature Importance              (Random Forest — Top 15 features)
STEP 8  →  Sample Predictions              (2 employees from test set)
STEP 9  →  Business Recommendations
```

---

## 🤖 Models Trained & Compared

| # | Model | Why Used |
|---|---|---|
| 1 | **Logistic Regression** | Simple, interpretable baseline for binary classification |
| 2 | **Decision Tree** | Explainable rules, easy to present to non-technical teams |
| 3 | **Random Forest** | Strong ensemble model, used for feature importance |
| 4 | **KNN** | Non-parametric, good for comparison |
| 5 | **Naive Bayes** | Fast probabilistic classifier, handles small data well |

> All models use `class_weight='balanced'` (where applicable) to handle the class imbalance (84% No Attrition vs 16% Yes).  
> Best model is selected automatically based on **F1-Score**.

---

## 📈 Results Summary

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| **Logistic Regression** ⭐ | 0.77 | 0.38 | 0.68 | **0.48** |
| Random Forest | 0.83 | 0.48 | 0.47 | 0.47 |
| Decision Tree | 0.77 | 0.35 | 0.53 | 0.42 |
| Naive Bayes | 0.62 | 0.25 | 0.70 | 0.37 |
| KNN | 0.82 | 0.31 | 0.11 | 0.16 |

> ⭐ Best model by F1-Score: **Logistic Regression**

---

## 🔍 Top Attrition Drivers (Feature Importance)

Based on the Random Forest model:

| Rank | Feature | Importance |
|---|---|---|
| 1 | TotalWorkingYears | 0.088 |
| 2 | OverTime | 0.084 |
| 3 | Age | 0.076 |
| 4 | MonthlyIncome | 0.071 |
| 5 | YearsWithCurrManager | 0.065 |
| 6 | YearsAtCompany | 0.058 |
| 7 | StockOptionLevel | 0.042 |
| 8 | YearsInCurrentRole | 0.041 |

---

## 💡 Business Recommendations

Based on model insights, HR should prioritize:

| # | Recommendation | Why It Matters |
|---|---|---|
| 1 | **Reduce Overtime** | OverTime is the #2 driver — employees on mandatory overtime are at significantly higher attrition risk |
| 2 | **Improve Salary Hikes** | Low `PercentSalaryHike` correlates with higher attrition — regular pay reviews reduce risk |
| 3 | **Focus on Engagement** | Low `JobSatisfaction` and `JobInvolvement` scores are early warning signs — invest in 1-on-1s and engagement programs |

---

## 📂 Documents Guide

| Document | Purpose | Read When |
|---|---|---|
| `HR attrition BRD.docx` | Business problem, KPIs, success criteria | Start here — understand the "why" |
| `Final capstone project.docx` | Assignment brief, task list, evaluation criteria | Understand what needs to be delivered |
| `ML rule book.md` | Technical step-by-step rules for the project | Follow this during implementation |
| `Sample Project Document.pdf` | Reference example of final deliverable | Useful for preparing presentation/report |

---

## ⚙️ Tech Stack & Requirements

| Package | Version |
|---|---|
| Python | 3.10.5 |
| scikit-learn | 1.7.2 |
| pandas | 2.3.3 |
| numpy | 2.2.6 |
| matplotlib | 3.x |
| seaborn | 0.13.2 |
| scipy | latest |

**Install all dependencies:**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

---

## 📁 Dataset Info

- **File:** `dataset/HR-Employee-Attrition.csv`
- **Rows:** 1,470 employees
- **Features:** 35 columns → 31 after dropping constant columns
- **Target:** `Attrition` (Yes = 1 / No = 0)
- **Class split:** 84% No Attrition · 16% Yes Attrition (imbalanced)

---

<div align="center">

*HR Attrition Prediction · Data Science Capstone · 2026*

</div>
- Tunes each model to get the best settings
- Shows which factors matter most for attrition
- Predicts attrition for new/sample employees
- Gives 3 practical recommendations to the HR team

---

## Folder structure

```
ML Capstone project/
│
├── dataset/
│   └── HR-Employee-Attrition.csv       the main data file used for training
│
├── docs/
│   ├── HR attrition BRD.docx           business requirement document – start here to understand the problem
│   ├── Final capstone project.docx     the project brief / assignment document
│   ├── ML rule book.md                 step-by-step rules we had to follow for this project
│   ├── Sample Project Document.pdf     reference sample for how the final output should look
│   └── hr_attrition_prediction copy.py old backup of the script (ignore this)
│
├── output_plots/
│   ├── 01_outlier_boxplots.png
│   ├── 02_target_distribution.png
│   ├── 03_univariate_numerical.png
│   ├── 04_univariate_categorical.png
│   ├── 05_bivariate_categorical_vs_attrition.png
│   ├── 06_bivariate_numerical_vs_attrition.png
│   ├── 07_correlation_heatmap.png
│   └── 08_feature_importance.png       this one shows the top 15 reasons for attrition
│
├── hr_attrition_prediction.py          main script – this is what you run
├── Readme.md                           this file
└── .venv/                              python virtual environment (don't touch)
```

---

## How to run

Make sure you are in the project root folder, then run:

```
.venv\Scripts\python.exe hr_attrition_prediction.py
```

That's it. The script will print everything to the terminal and save all 8 plots inside the `output_plots/` folder.

---

## Which documents to read and in what order

1. **HR attrition BRD.docx** – Read this first. It explains the business problem, what HR wants, and what success looks like. Think of it as the "why are we doing this" document.

2. **Final capstone project.docx** – This is the assignment brief. It lists what tasks need to be done and how the project will be evaluated.

3. **ML rule book.md** – This is the technical checklist. It tells exactly what steps to follow: EDA, outlier handling, model building, evaluation, etc. The code follows this document step by step.

4. **Sample Project Document.pdf** – A reference example showing how the final deliverable should look. Useful if you're preparing a presentation or report.

---

## Models used

| Model | Why used |
|---|---|
| Logistic Regression | Simple, good baseline for binary classification |
| Decision Tree | Easy to interpret, shows decision paths |
| Random Forest | Generally strong performer, used for feature importance |
| KNN | Non-parametric, good for comparison |
| Naive Bayes | Fast, works well with small data |

All models are tuned using GridSearchCV (3-fold cross-validation).

---

## Key findings (from feature importance)

The top reasons employees leave, according to the Random Forest model:

1. Total Working Years – less experienced employees leave more
2. Overtime – employees doing overtime are at much higher risk
3. Age – younger employees tend to leave more
4. Monthly Income – lower salary = higher attrition risk
5. Years with Current Manager – instability in reporting increases risk

---

## Business recommendations

Based on the model output, three things HR should act on:

- **Reduce overtime** – this is the biggest controllable factor
- **Improve salary hikes** – regular and fair increments reduce the risk
- **Focus on engagement** – employees with low job satisfaction and involvement are more likely to leave

---

## Dataset info

- File: `dataset/HR-Employee-Attrition.csv`
- Rows: 1470 employees
- Columns: 35 features
- Target column: `Attrition` (Yes / No)

Three columns were dropped before modeling because they carry no useful information:
`EmployeeCount`, `Over18`, `StandardHours`

---

## Requirements

