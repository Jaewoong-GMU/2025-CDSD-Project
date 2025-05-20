# 📘 2025 CDSD Project: Student Habits and Academic Performance

**Authors**: Jaewoong Choi, Seonghee Park, Joseph Kim, Hyunha Noh  
**Course**: CDS 102 – Introduction to Data Science  
**Date**: 2025/05/20  

---

## 📌 Project Overview

This project analyzes the relationship between students’ daily habits and their academic performance. Using the **Student Habits vs Academic Performance** dataset from Kaggle, we explore how study hours, sleep, screen time, attendance, and mental health influence exam scores. The project includes data cleaning, visualization, regression modeling, and hypothesis testing.

---

## 📂 Dataset Information

- **Source**: [Kaggle – Student Habits vs Academic Performance Dataset](https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance)  
- **Full Report**: [**Click here to view the full report**](https://github.com/Jaewoong-GMU/2025-CDSD-Project/raw/main/project.pdf)  
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
- Created two new variables:
  - `total_screen_time`: The sum of `social_media_hours` and `netflix_hours`, representing overall recreational screen usage
  - `well_being`: The sum of `sleep_hours` and `mental_health_rating`, as a proxy for holistic wellness

**What We Found**:
- These composite variables helped assess combined effects of lifestyle factors
- Minimal data loss due to smart imputation strategies

---

### 📊 Exploratory Data Analysis
**Purpose**: Explore distributions and group-level patterns.

**What We Did**:
- Histograms for numeric variables  
- Bar plots for categorical variables  
- Summary statistics and outlier checks

**What We Found**:
- Most students study 1–3 hours and sleep 6–8 hours  
- Mental health ratings mostly ranged from 3 to 6  
- Majority did not have part-time jobs; most had “Fair” diet quality  

---

### 📉 Regression Analysis

#### 1. Simple Linear Regression  
**Purpose**: Understand how study hours relate to academic performance.

**Model**:  
\[
\hat{y} = \beta_0 + \beta_1 x
\]  
Where \(\hat{y}\) is the predicted exam score, and \(x\) is `study_hours_per_day`

**What We Did**:
- Used `lm()` to model `exam_score ~ study_hours_per_day`

**What We Found**:
- Intercept: **35.91**, Coefficient: **+9.49**  
- R² ≈ **0.68**

**Interpretation**:
- For each additional hour of daily study, students scored **about 9.49 points higher** on average.
- Residuals were normally distributed, supporting linear model assumptions.

---

#### 2. Multiple Linear Regression  
**Purpose**: Account for multiple influences on exam scores.

**Model**:  
\[
\hat{y} = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_n x_n
\]

**Variables Used**:  
- `study_hours_per_day`, `sleep_hours`, `attendance_percentage`, `mental_health_rating`, `total_screen_time`

**What We Found**:
| Predictor               | Coefficient |
|-------------------------|-------------|
| `study_hours_per_day`   | +9.51       |
| `sleep_hours`           | +2.05       |
| `attendance_percentage` | +0.14       |
| `mental_health_rating`  | +1.95       |
| `total_screen_time`     | –2.52       |

- R² ≈ **0.87**

**Interpretation**:
- The model explains **87% of the variance** in exam scores.
- Study hours had the strongest positive effect, while screen time showed a mild negative impact.

---

### ⚙️ Model Evaluation

**Purpose**: Test model performance and generalization.

**Metrics Used**:
\[
\text{RMSE} = \sqrt{ \frac{1}{n} \sum (y_i - \hat{y}_i)^2 }
\]

**What We Did**:
- Split the data into 80% training and 20% testing
- Calculated RMSE for both sets

**Results**:
- **Train RMSE**: 6.20  
- **Test RMSE**: 5.58  

**Interpretation**:
- The model makes predictions within **±5.6 points** on average for unseen data.
- Residuals were randomly distributed, supporting linearity and constant variance.

---

### 🧪 Statistical Inference – t-Test

**Purpose**: Examine if having a part-time job significantly affects exam performance.

**What We Did**:
- Two-sample t-test: `exam_score ~ part_time_job`

**Results**:
- **p-value ≈ 0.395** → Not statistically significant  
- Mean difference: ≈ –1.09  

**Interpretation**:
- No evidence of a significant difference in exam scores between students with and without part-time jobs.

**💡 Visualization Suggestion**:
- Include a **boxplot** comparing exam scores by part-time job status for clearer communication.

---

## 🧾 Conclusion

Our analysis reveals that **daily habits significantly influence academic performance**:

- 📚 **Study time** had the greatest impact on exam scores
- 💤 **Sleep** and 🧠 **mental health** positively contributed to performance
- 📱 **Excessive screen time** showed a modest negative effect
- 👷 **Part-time job status** did not significantly affect outcomes

📌 **Key Takeaways for Students**:
- Increase study time and maintain good sleep habits
- Monitor screen use to avoid overexposure
- Mental well-being matters—take care of it!
- Don’t worry too much about working part-time—focus on balance

---

## 🛠️ Tools & Technologies

- **Language**: R  
- **Libraries**: `tidyverse`, `ggplot2`, `infer`, `modelr`, `janitor`  
- **Techniques**: Data wrangling, regression modeling, hypothesis testing, visualization

---

## 📚 References

- 📖 [Kaggle Dataset](https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance)  
- 📖 [ModernDive: Chapter 5 – Simple Regression](https://moderndive.com/5-regression.html)  
- 📖 [ModernDive: Chapter 6 – Multiple Regression](https://moderndive.com/6-multiple-regression.html)  
- 📖 [ModernDive: Chapter 9 – Hypothesis Testing](https://moderndive.com/9-hypothesis-testing.html)

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

👉 [**Click to View the Full Report**](https://github.com/Jaewoong-GMU/2025-CDSD-Project/raw/main/project.pdf)
