# 📘 2025 CDSD Project: Student Habits and Academic Performance

**Authors**: Jaewoong Choi, Seonghee Park, Joseph Kim  
**Course**: CDS 102 – Introduction to Data Science  
**Date**: 2025  

---

## 📌 Project Overview

This project analyzes the relationship between students’ daily habits and their academic performance. Using the **Student Habits vs Academic Performance** dataset from Kaggle, we explore how study hours, sleep, screen time, attendance, and mental health influence exam scores. The project includes data cleaning, visualization, regression modeling, and hypothesis testing.

---

## 📂 Dataset Information

- **Source**: [**Click here to view the full report**](https://github.com/Jaewoong-GMU/2025-CDSD-Project/raw/main/project.pdf)
- **Description**: A synthetic dataset of 1,000 students including lifestyle, well-being, and academic metrics.

### 🔑 Key Variables

| Variable                      | Description                                         | Type        |
|-------------------------------|-----------------------------------------------------|-------------|
| `study_hours_per_day`         | Average daily study time (hours)                    | Numeric     |
| `sleep_hours`                 | Average daily sleep (hours)                         | Numeric     |
| `mental_health_rating`        | Mental health score (1–10)                          | Numeric     |
| `exam_score`                  | Final exam score (%)                                | Numeric     |
| `social_media_hours`          | Daily social media use (hours)                      | Numeric     |
| `netflix_hours`               | Daily Netflix viewing (hours)                       | Numeric     |
| `part_time_job`               | Has a part-time job (Yes/No)                        | Categorical |
| `attendance_percentage`       | Class attendance rate (%)                           | Numeric     |
| `diet_quality`                | Quality of diet (Poor/Fair/Good)                    | Categorical |
| `internet_quality`            | Internet access quality (Poor/Average/Good)         | Categorical |
| `parental_education_level`    | Highest education level of parents                  | Categorical |

---

## 🧠 Project Goals

- Understand how study time, sleep, screen usage, and well-being influence academic outcomes.
- Use regression analysis to predict exam scores.
- Test hypotheses on group differences (e.g., job vs no job).
- Clean, visualize, and model structured data in R.

---

## 📈 Methods and What We Found

### ✅ Data Cleaning & Feature Engineering
**Purpose**: Prepare the data by handling missing values and creating useful new variables.  
**What We Did**:
- Filled missing values in `parental_education_level` using the mode
- Created:
  - `total_screen_time` = `social_media_hours` + `netflix_hours`
  - `well_being` = `sleep_hours` + `mental_health_rating`

**What We Found**:
- New variables helped model combined effects.
- Minimal data was lost thanks to proper imputation.

---

### 📊 Exploratory Data Analysis
**Purpose**: Explore distributions and group-level patterns.  
**What We Did**:
- Histograms for numeric variables
- Bar plots for categorical variables
- Summary statistics and outlier checks

**What We Found**:
- Most students study 1–3 hours and sleep 6–8 hours.
- Mental health ratings mostly ranged from 3–6.
- Most students had no part-time jobs and “Fair” diets.

---

### 📉 Regression Analysis

#### 1. Simple Linear Regression  
**Purpose**: Understand how study hours relate to academic performance.

Model Equation: ŷ = β₀ + β₁x

Where ŷ is the predicted exam score, and x is study hours per day.

**What We Did**:
- Used `lm()` to model `exam_score ~ study_hours_per_day`

**What We Found**:
- Intercept: **35.91**, Coefficient (study_hours): **+9.49**
- R² ≈ **0.68**  
- **Interpretation**: Each additional hour of study increased exam score by ~9.49 points.
- **Residuals** showed a normal spread, supporting model assumptions.

---

#### 2. Multiple Linear Regression  
**Purpose**: Account for multiple influences on exam scores.

**Model Equation**: ŷ = β₀ + β₁ × x₁ + β₂ × x₂ + ... + βₙ × xₙ

**Variables Used**:  
- `study_hours_per_day`, `sleep_hours`, `attendance_percentage`, `mental_health_rating`, `total_screen_time`

**What We Found**:
- Coefficients:
  - `study_hours_per_day`: **+9.51**
  - `sleep_hours`: **+2.05**
  - `attendance_percentage`: **+0.14**
  - `mental_health_rating`: **+1.95**
  - `total_screen_time`: **–2.52**
- R² ≈ **0.87**
- **Interpretation**: These five predictors together explained 87% of the variance in exam scores, indicating a very strong model.

---

### ⚙️ Model Evaluation

**Purpose**: Validate model accuracy and generalizability.

**Metrics Used**:
- **RMSE**: sqrt( (1/n) × Σ(yᵢ - ŷᵢ)² )

**What We Did**:
- 80/20 train-test split
- Calculated RMSE on both sets

**Results**:
- **Train RMSE**: **6.20**
- **Test RMSE**: **5.58**
- **Interpretation**: Predictions were accurate within ±5.6 points on average in the test set.
- Residual plot showed randomness, supporting linearity and homoscedasticity assumptions.

---

### 🧪 Statistical Inference – t-Test

**Purpose**: Test if students with part-time jobs had significantly different exam scores.

**Test Used**:
t = (x̄₁ - x̄₂) / sqrt( (s₁² / n₁) + (s₂² / n₂) )

**What We Did**:
- Two-sample t-test on `exam_score ~ part_time_job`

**What We Found**:
- **p-value ≈ 0.395** → not statistically significant
- Mean difference ≈ –1.09
- **Interpretation**: No evidence that part-time job status significantly affected exam scores.

---

## 🧾 Conclusion
This project demonstrates that daily habits have a measurable impact on students’ academic performance. Our findings show that students who study more, sleep well, attend class regularly, and report better mental health tend to score higher on exams. In contrast, excessive screen time has a modest negative effect.

The multiple regression model with an R² of 0.87 highlights that no single habit determines success. Instead, academic outcomes are shaped by a combination of behavioral and lifestyle factors.

Our t-test showed no statistically significant difference in exam performance between students with and without part-time jobs, suggesting that work status alone does not greatly influence academic results.

This project helped us apply the full data science process from cleaning and exploring data to modeling and inference. These insights may support both students and educators in promoting healthier and more balanced academic routines.

---

## 🛠️ Tools & Technologies

- **Language**: R  
- **Libraries**: `tidyverse`, `ggplot2`, `infer`, `modelr`, `janitor`  
- **Techniques**: Data wrangling, regression modeling, hypothesis testing, visualization

---

## 📚 References

- 📖 [ModernDive: Chapter 5 – Simple Regression](https://moderndive.com/5-regression.html)  
- 📖 [ModernDive: Chapter 6 – Multiple Regression](https://moderndive.com/6-multiple-regression.html)  
- 📖 [ModernDive: Chapter 9 – Hypothesis Testing](https://moderndive.com/9-hypothesis-testing.html)  

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

👉 [**Click to View the Full Report**](https://github.com/Jaewoong-GMU/2025-CDSD-Project/raw/main/project.pdf)
