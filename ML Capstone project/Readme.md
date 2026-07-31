# HR Attrition Prediction – Capstone Project

This project was built as part of a Data Science capstone. The goal is simple: use machine learning to predict whether an employee is likely to leave the company or not, and figure out what's driving that decision.

---

## What this project does

- Loads the HR dataset and does a full analysis (missing values, outliers, distributions, etc.)
- Builds 5 different ML models and compares them
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

Python 3.10+

Packages used:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- scipy

Install them with:
```
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```
