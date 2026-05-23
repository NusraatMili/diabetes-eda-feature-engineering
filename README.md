## 🩺 Diabetes EDA & Feature Engineering

Exploratory Data Analysis and Feature Engineering on the Pima Indians Diabetes Dataset — uncovering the key health factors that predict diabetes using Python, Pandas, and Seaborn.


## 📌 Project Overview

**Dataset :** Pima Indians Diabetes Dataset  
**Source :** Kaggle  
**Records :** 768 patients × 9 features  
**Target :** Outcome — 1 = Has Diabetes, 0 = No Diabetes  
**Tools :** Python, Pandas, NumPy, Matplotlib, Seaborn

**Business Question:** What health factors determine whether a patient has diabetes?

**Hypothesis:** Glucose, BMI, Age, Insulin, and genetic risk (DiabetesPedigreeFunction) are the strongest predictors of diabetes onset.

## 🔑 Key Findings

**1. Glucose is the single strongest predictor of diabetes**

Glucose correlates with Outcome at 0.49 — the highest of any feature in the dataset. Patients with Glucose above 140 mg/dL have a diabetes rate nearly 2× the dataset average of 34.9%. If a clinician could only check one measurement, glucose would be it.

**2. Obesity dramatically increases diabetes risk**

Obese patients (BMI > 30) have the highest diabetes rate among all weight categories. The boxplot confirms diabetic patients have a visibly higher BMI median than non-diabetic patients. BMI correlates with Outcome at 0.29.

**3. Middle-aged patients (35–60) are the highest-risk age group**

The Age_Group bivariate chart shows middle-aged patients have the highest diabetes rate — higher than both adults and seniors. Diabetic patients skew toward older ages in the pairplot, consistent with Age's moderate correlation with Outcome.

**4. Insulin data is severely limited but still informative**

48.7% of Insulin values were coded as zero (missing), making it the least reliable raw feature. However, diabetic patients show a higher Insulin median in boxplot analysis — consistent with insulin resistance. With better data collection, Insulin could become a stronger predictor.

**5. Blood Pressure has almost no predictive value alone**

BloodPressure showed near-zero correlation with DiabetesPedigreeFunction and heavily overlapping distributions between diabetic and non-diabetic groups. It should be deprioritized in modeling unless combined with other features as an interaction term.

## 📊 Analysis Structure

Section 1 — Dataset Overview

Section 2 — Data Quality Audit

Section 3 — Cleaning Pipeline

Section 4 — Univariate Analysis

Section 5 — Bivariate Analysis

Section 6 — Multivariate Analysis

Section 7 — Key Findings

Section 8 — Next Steps

## 🔧 Feature Engineering
Three new features were created and validated against the target:
Feature | Description | Insight
-------|-----------|-------
`Age\_Group`|	Binned age into adult / middle / senior | Middle-aged patients have highest diabetes rate
`High\_Glucose\_Flag` | Binary flag: Glucose > 140 | Strong positive association with diabetes outcome
`Weight\_Status` | BMI categorized into Underweight / Normal / Overweight / Obese |	Obese category has highest diabetes prevalence

## 🧹 Data Quality Issues Found & Fixed
Column | Issue | Missing % | Strategy
--------|------|-----------|----------
Insulin | Zeros as missing values |	48.7% |	Replaced with median
BloodPressure |	Zeros as missing values |	4.6% | Replaced with median
BMI |	Zeros as missing values |	1.4%	| Replaced with median
Glucose	| Zeros as missing values |	0.65%	| Replaced with median

> **Key insight:** This dataset uses `0` as a placeholder for missing values — not actual zero measurements. Identifying this was the critical first step of the audit.

## 📈 Visualizations

Chart |	Type |	Finding
------|------|---------
Target variable distribution |	Countplot + Pie |	65% No Diabetes, 35% Diabetes — slightly imbalanced
Numeric distributions |	Histogram + KDE	| Insulin and DiabetesPedigreeFunction are right-skewed
Categorical distributions |	Bar charts	| Most patients are adults, overweight/obese
Categorical features vs Outcome	| Bar charts	| High glucose flag and obesity most associated with diabetes
Numeric features vs Outcome |	Boxplots |	Glucose and BMI show clearest separation
Feature correlation matrix	| Heatmap	| Glucose–Outcome: 0.49, Age–Pregnancies: 0.54
Pairwise relationships	| Pairplot |	Glucose separates diabetic/non-diabetic most clearly

## 🚀 Next Steps
**- Interaction feature** — create `Glucose × BMI` as a combined metabolic risk score

**- Predictive modeling** — train Logistic Regression and Random Forest; expect Glucose, BMI, and Age as top 3 important features

**- Handle class imbalance** — use `class\_weight='balanced'` in models or SMOTE oversampling to prevent bias toward predicting No Diabetes by default

## 📚 Dataset Information

The Pima Indians Diabetes Dataset was originally collected by the National Institute of Diabetes and Digestive and Kidney Diseases. All patients are females of at least 21 years of age of Pima Indian heritage.
**Features:**
Feature	| Description
--------|-------------
Pregnancies |	Number of times pregnant
Glucose |	Plasma glucose concentration (2-hour oral glucose tolerance test)
BloodPressure	| Diastolic blood pressure (mm Hg)
SkinThickness |	Triceps skin fold thickness (mm)
Insulin	| 2-hour serum insulin (mu U/ml)
BMI	| Body mass index (weight in kg / height in m²)
DiabetesPedigreeFunction |	Diabetes pedigree function (genetic risk score)
Age	| Age in years
Outcome | Target — 1 = Diabetic, 0 = Non-diabetic

## 👤 Author
**Learning Data Science** — A project from my structured Data Science learning journey.
