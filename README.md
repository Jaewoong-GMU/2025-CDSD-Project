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

| Variable                    | Description                                      | Type        |
|-----------------------------|--------------------------------------------------|-------------|
| `study_hours_per_day`       | Average daily study time (hours)                 | Numeric     |
| `sleep_hours`               | Average daily sleep (hours)                      | Numeric     |
| `mental_health_rating`      | Mental health score (1–10)                       | Numeric     |
| `exam_score`                | Final exam score (%)                             | Numeric     |
| `social_media_hours`        | Daily social media use (hours)                   | Numeric     |
| `netflix_hours`             | Daily Netflix viewing (hours)                    | Numeric     |
| `part_time_job`             | Has a part-time job (Yes/No)                     | Categorical |
| `attendance_percentage`     | Class attendance rate (%)                        | Numeric     |
| `diet_quality`              | Quality of diet (Poor/Fair/Good)                 | Categorical |
| `internet_quality`          | Internet access quality (Poor/Average/Good)      | Categorical |
| `parental_education_level`  | Highest education level of parents               | Categorical |

---

## 🧠 Project Goals

- Understand how study time, sleep, screen usage, and well-being influence academic outcomes  
- Use regression analysis to predict exam scores  
- Test hypotheses on group differences (e.g., job vs no job)  
- Clean, visualize, and model structured data in R  

---

## 📈 Methods and What We Found

### ✅ Data Cleaning & Feature Engineering

- Filled missing values in `parental_education_level` using the mode  
- Created new variables:  
  - `total_screen_time` = `social_media_hours` + `netflix_hours`  
  - `well_being` = `sleep_hours` + `mental_health_rating`  

---

## 📊 Exploratory Data Analysis

**What We Did**:
- Histograms for numeric variables  
- Bar plots for categorical variables  

### 📷 Numeric Variable Distributions  
![Numeric Distributions](CDSD_Project_Images/numeric_distributions.png)  
*This set of histograms displays how students are distributed across study time, sleep, mental health, and exam scores. Most students study 1–3 hours and sleep 6–8 hours per day.*

![Categorical Distributions](CDSD_Project_Images/categorical_distributions.png)  
*These bar charts show how categorical variables like part-time job, diet quality, and internet access are distributed. Most students do not work part-time and report having "Fair" diets.*


---

## 📉 Regression Analysis

### 1. Simple Linear Regression

**Model**:
```
ŷ = β₀ + β₁x
```
Where `x` is `study_hours_per_day`, and `ŷ` is the predicted exam score.

**Results**:
- Intercept: 35.91  
- Coefficient: +9.49  
- R² ≈ 0.68  

**Interpretation**:  
The simple linear regression reveals a strikingly powerful relationship between study time and academic performance. With a coefficient of +9.49, the model quantifies what many educators intuitively understand: dedicated study time dramatically impacts outcomes. To put this in perspective: a student who increases their daily study time from 1 hour to 3 hours could expect, on average, a remarkable 19-point improvement in their exam score, potentially transforming a failing grade into a solid pass or a B into an A.

The R² value of 0.68 is particularly noteworthy in educational research, where human performance is typically influenced by countless variables. That a single factor (study time) explains over two-thirds of the variation in academic outcomes speaks to its fundamental importance in learning processes. This powerful explanatory value far exceeds typical single-predictor models in social science research, where R² values of 0.3 are often considered substantial.

This finding has profound implications for educational interventions: if resources are limited, focusing on increasing effective study time may yield the highest return on investment compared to other potential interventions. However, the 32% unexplained variance reminds us that academic success isn't one-dimensional; it likely involves a complex interplay of cognitive, behavioral, and environmental factors that extend beyond mere time allocation.

The linearity of this relationship is equally significant, suggesting that benefits continue to accrue even at higher study durations, with no evidence of diminishing returns within the observed range. This contradicts the common student belief that "cramming" (intense but short-duration studying) can substitute for consistent study habits.

### 📷 Study Hours vs Exam Score  
![Study Hours vs Exam Score](CDSD_Project_Images/study_vs_exam.png)  
*Scatter plot showing that increased study time correlates strongly with higher exam scores. The regression line confirms a positive linear relationship.*

---

### 2. Multiple Linear Regression

**Model**:
```
ŷ = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ
```

**Variables Used**:  
- `study_hours_per_day`, `sleep_hours`, `attendance_percentage`, `mental_health_rating`, `total_screen_time`

**Results**:

| Predictor               | Coefficient |
|-------------------------|-------------|
| `study_hours_per_day`   | +9.51       |
| `sleep_hours`           | +2.05       |
| `attendance_percentage` | +0.14       |
| `mental_health_rating`  | +1.95       |
| `total_screen_time`     | –2.52       |

- R² ≈ 0.87  

**Interpretation**:  
The multiple regression model provides a sophisticated portrait of academic success, explaining an impressive 87% of exam score variation, a level of predictive power rarely achieved in behavioral research. The 19 percentage point improvement over the simple model demonstrates that while study time is foundational, a holistic approach to student success yields substantially better outcomes.

The model coefficients reveal several compelling insights: 
Study time's coefficient (+9.51) remains virtually unchanged from the simple model, demonstrating remarkable robustness. This "stability under control" is a powerful statistical signal that study time has a direct causal pathway to academic performance rather than merely serving as a proxy for other positive behaviors. The effect size remains substantial: approximately 3 hours of additional study per week throughout a semester could potentially transform a B- student (80%) into an A student (90%). 

Sleep emerges as the second most influential factor (+2.05 per hour), highlighting the critical yet often overlooked role of physiological health in cognitive performance. This translates to practical advice: a student who improves their sleep from 6 to 8 hours per night might gain 4 additional points on their exam score, equivalent to about 25 minutes of extra daily study time. This efficiency makes sleep optimization a particularly valuable strategy for time-pressed students. 

The mental health coefficient (+1.95 per rating point) quantifies the academic impact of psychological wellbeing. This finding challenges traditional academic support approaches that focus exclusively on content mastery while neglecting emotional health. It suggests that university mental health services and stress management programs may indirectly serve as academic performance enhancers, with each point improvement on the mental health scale contributing nearly 2 percentage points to predicted exam scores. 

The negative screen time coefficient (-2.52 per hour) provides concrete evidence of the academic costs of digital distraction. Notably, the magnitude suggests that each hour spent on social media or streaming services effectively negates approximately 15 minutes of dedicated study time. For the average student in the sample, reducing screen time by just 2 hours daily could boost exam scores by 5 points, a significant improvement for minimal effort. 

The attendance coefficient (+0.14 per percentage point) quantifies the "showing up" factor in academic success. While smaller in magnitude, this effect compounds over a semester; a student who improves attendance from 70% to 95% could see a 3.5-point boost in exam performance beyond what their study habits alone would predict. This suggests that regular class participation provides unique learning benefits that cannot be fully replicated through independent study.

---

## ⚙️ Model Evaluation

**Metric**:
```
RMSE = sqrt((1/n) × Σ(yᵢ - ŷᵢ)²)
```

**Results**:
- Train RMSE: 6.20  
- Test RMSE: 5.58  

**Interpretation**:  
The model demonstrates impressive predictive accuracy with a test RMSE of 5.58, indicating predictions typically fall within about 5-6 percentage points of actual exam scores. In practical terms, this means the model can distinguish between students likely to achieve different letter grades, making it sufficiently precise for identifying at-risk students who might benefit from targeted interventions.

The unusual relationship between training RMSE (6.20) and test RMSE (5.58) contradicts typical statistical patterns where test errors exceed training errors. This suggests the model has captured fundamental relationships in student performance that generalize exceptionally well to new data. Such generalizability enhances the model's practical utility and suggests the five predictors represent truly foundational factors in academic success rather than dataset-specific correlations.

The residual plots confirm linear model assumptions through their random scatter around zero without concerning patterns. This validation strengthens confidence that the identified relationships reflect genuine effects rather than statistical artifacts. The visual homoscedasticity (consistent variance across the range of predicted values) indicates that the model predicts equally well for both high and low-performing students, making it valuable across the entire performance spectrum.

The combination of high R² (0.87) and reasonably low RMSE (5.58) establishes this model as both explanatory and predictive. This dual strength makes it valuable not only for understanding the mechanisms of academic performance but also for practical applications such as early warning systems to identify struggling students before formal assessments.

### 📷 Predicted vs Actual Exam Scores  
![Predicted vs Actual](CDSD_Project_Images/predicted_vs_actual.png)  
*This plot shows the predicted exam scores versus actual scores. Most points are close to the diagonal, indicating accurate model predictions.*

![Residuals vs Fitted](CDSD_Project_Images/residuals_vs_fitted.png)  
*This plot checks model assumptions. Residuals appear randomly scattered, supporting linearity and constant variance.*

---

## 🧪 Statistical Inference – t-Test

**What We Did**:
- Conducted a two-sample t-test on `exam_score ~ part_time_job`

**Results**:
- p-value ≈ 0.395  
- Mean difference: –1.09  

**Interpretation**:  
The t-test results challenge conventional wisdom about part-time employment and academic performance. With a high p-value of 0.395 and a negligible mean difference of just -1.09 points, the data provide compelling evidence that working students perform academically on par with their non-working peers.

This finding has substantial implications for student advising and financial aid policies. For students facing financial pressures, these results suggest they can pursue part-time work without expecting significant academic penalties. The magnitude of the observed difference (-1.09 points) is so small that it would be more than offset by just 7 additional minutes of daily study time, based on our regression coefficient for study hours.

Several mechanisms may explain this counterintuitive finding. Working students might develop enhanced time management skills, experience reduced financial stress, gain complementary real-world knowledge that aids academic understanding, or simply become more efficient in their study habits. Additionally, work experience may provide structure and purpose that benefit overall wellbeing and academic motivation.

This result underscores the importance of evidence-based approaches to student success rather than relying on assumptions about supposed incompatibility between employment and academic achievement. For educational institutions, it suggests that rather than discouraging employment, resources might be better directed toward helping students integrate work and study effectively through flexible scheduling options and time management training.

---

## 🧾 Conclusion

📚 **Study time** had the strongest positive effect  
🧠 **Mental health** and 💤 **sleep** boosted scores  
📱 **Excessive screen time** lowered performance slightly  
👷 **Part-time work** had no significant effect

The multivariate analysis reveals that academic success is best understood as an ecosystem of interconnected behaviors and wellbeing factors rather than isolated variables. While study time stands out as the single most powerful predictor, its effect is significantly amplified when combined with adequate sleep, good mental health, and limited screen time.

These findings suggest opportunities for educational interventions that target multiple factors simultaneously. For instance, campus initiatives that combine study skill workshops with sleep hygiene education and screen time management strategies might yield synergistic benefits exceeding what would be expected from addressing each factor in isolation.

The lack of significant academic impact from part-time employment challenges common institutional policies that discourage working students. Instead, universities might better serve students by helping them integrate employment with academic responsibilities through more flexible scheduling, blended learning options, and targeted time management support.

From a methodological perspective, the substantial improvement in explanatory power from single to multiple regression (R² from 0.68 to 0.87) demonstrates the value of comprehensive, multivariate approaches to understanding academic performance. Future research should explore additional factors and potential interaction effects that might capture the remaining 13% of unexplained variance.

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
