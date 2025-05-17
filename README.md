# 📘 2025 CDSD Project: Student Habits and Academic Performance

**Authors**: Jaewoong Choi, Seonghee Park, Joseph Kim  
**Course**: CDS 102 – Introduction to Data Science  
**Date**: 2025  

---

## 📌 Project Overview

This project analyzes the relationship between students’ daily habits and their academic performance. Using the **Student Habits vs Academic Performance** dataset from Kaggle, we explore how study hours, sleep, screen time, attendance, and mental health influence exam scores. The project includes data cleaning, visualization, regression modeling, and hypothesis testing.

---

## 📂 Dataset Information

- **Source**: [Kaggle - Student Habits vs Academic Performance](https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance)
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

## 📈 Methods Used

### ✅ Data Cleaning & Feature Engineering
**Purpose**: Prepare the data for analysis by handling missing values and creating useful new variables.  
**What We Did**:
- Filled missing values in `parental_education_level` using the mode
- Created two new variables:
  - `total_screen_time` = `social_media_hours` + `netflix_hours`
  - `well_being` = `sleep_hours` + `mental_health_rating`

**What We Found**:
- The newly created variables made it easier to analyze the combined impact of screen time and personal wellness on academic performance.
- There were missing values mostly in categorical variables like parental education, which we resolved without removing data.

---

### 📊 Exploratory Data Analysis
**Purpose**: Understand the shape, distribution, and group-level patterns in the data.  
**What We Did**:
- Created histograms for numeric variables
- Created bar plots for categorical variables
- Checked for skewness, outliers, and group differences

**What We Found**:
- Most students study 1–3 hours per day, and sleep between 6–8 hours.
- Mental health ratings were mostly low (3–6), suggesting stress or academic pressure.
- The majority of students had no part-time jobs and reported “Fair” or “Good” diet quality.
- These visual patterns helped inform which variables might impact exam performance and justified including them in our models.

---

### 📉 Regression Analysis

#### 1. Simple Linear Regression  
**Purpose**: Measure the relationship between study hours and exam scores.  
**What We Did**:  
- Fit a linear model: `exam_score ~ study_hours_per_day`

**What We Found**:
- A strong, statistically significant **positive correlation** between study hours and exam scores.
- The model indicated that each additional study hour increased expected exam score by approximately a few percentage points.
- However, the model only explained part of the variance (R² ≈ moderate), meaning other variables are also important.

#### 2. Multiple Linear Regression  
**Purpose**: Understand the combined effect of multiple variables on exam scores.  
**What We Did**:
- Included predictors: `study_hours_per_day`, `sleep_hours`, `attendance_percentage`, `mental_health_rating`, `total_screen_time`

**What We Found**:
- All included variables were statistically significant.
- **Study hours**, **attendance**, and **mental health** had strong positive effects.
- **Total screen time** had a mild negative effect.
- The model had a very high R² (~0.90), indicating that these variables together explain most of the variation in exam scores.

---

### 🧪 Statistical Inference

#### Two-Sample t-Test  
**Purpose**: Test whether exam scores differ based on part-time job status.  
**What We Did**:  
- Conducted a t-test comparing `exam_score` between students with and without a part-time job.

**What We Found**:
- Students without part-time jobs scored **significantly higher** on average.
- The result supports the hypothesis that part-time work may reduce academic performance, likely due to time or energy constraints.

---

### ⚙️ Model Evaluation

**Purpose**: Validate the regression model’s ability to predict exam scores.  
**What We Did**:
- Split data into training (80%) and testing (20%) sets
- Fit model on training data and calculated RMSE on both sets
- Visualized predicted vs actual scores and residuals

**What We Found**:
- RMSE was low and similar for both training and testing datasets, indicating a well-generalized model.
- Residuals were randomly scattered around zero, satisfying linearity and homoscedasticity assumptions.
- Visual diagnostics confirmed that the multiple regression model was reliable and unbiased.

---

## 🧠 Summary of Findings

- 📚 **Studying longer** leads to higher exam scores — the strongest predictor in all models.
- 💤 **More sleep and better mental health** are associated with better academic performance.
- 📱 **Excessive screen time** (social + Netflix) slightly lowers exam scores.
- 💼 **Part-time job holders** tend to score lower, statistically confirmed.
- 📊 **Our regression model explained ~90% of exam score variation**, indicating a high level of predictive power.

---

## 📉 Limitations

- The dataset is synthetic and may not reflect real-life complexity.
- Many variables are self-reported and may be biased or inaccurate.
- The model assumes linearity and does not account for interaction effects or nonlinear trends.

---

## 🛠️ Tools & Technologies

- **Language**: R  
- **Libraries**: `tidyverse`, `ggplot2`, `infer`, `modelr`, `janitor`  
- **Techniques**: Data wrangling, regression modeling, visualization, inference

---

## 📚 References

- 📖 [ModernDive: Chapter 5 – Simple Regression](https://moderndive.com/5-regression.html)  
- 📖 [ModernDive: Chapter 6 – Multiple Regression](https://moderndive.com/6-multiple-regression.html)  
- 📖 [ModernDive: Chapter 9 – Hypothesis Testing](https://moderndive.com/9-hypothesis-testing.html)  

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## 🔗 [📥 View Final Report (PDF)](./project.pdf)
