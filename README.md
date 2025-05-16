
# 📘 2025 CDSD Project

## 📌 Project Overview

This project aims to analyze the relationship between students’ daily habits and their academic performance. Using the "Student Habits vs Academic Performance" dataset from Kaggle, we explore how various factors impact exam scores.

## 📂 Dataset Information

- Source: [Kaggle - Student Habits vs Academic Performance](https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance)
- Description: This synthetic dataset represents 1,000 students and includes variables such as study hours, sleep duration, social media and Netflix usage, exercise frequency, attendance, and mental health scores to examine their influence on exam performance.

## 📊 Key Variables

| Variable                         | Description                                           | Type       |
|----------------------------------|-------------------------------------------------------|------------|
| student_id                       | Student ID                                            | Identifier |
| age                              | Age                                                   | Numeric    |
| gender                           | Gender                                                | Categorical|
| study_hours_per_day              | Average daily study time (hours)                      | Numeric    |
| social_media_hours               | Daily social media usage (hours)                      | Numeric    |
| netflix_hours                    | Daily Netflix viewing time (hours)                    | Numeric    |
| part_time_job                    | Has a part-time job? (Yes/No)                         | Categorical|
| attendance_percentage            | Attendance rate (%)                                   | Numeric    |
| sleep_hours                      | Average daily sleep duration (hours)                  | Numeric    |
| diet_quality                     | Quality of diet (Poor, Fair, Good, etc.)              | Categorical|
| exercise_frequency               | Exercise frequency per week                           | Numeric    |
| parental_education_level         | Parent’s highest level of education                   | Categorical|
| internet_quality                 | Internet quality (Poor, Average, Good, etc.)          | Categorical|
| mental_health_rating             | Mental health rating (1 to 10)                        | Numeric    |
| extracurricular_participation    | Participates in extracurricular activities? (Yes/No)  | Categorical|
| exam_score                       | Final exam score (%)                                  | Numeric    |

## 🧠 Analysis Objectives

- Analyze how students' daily habits influence their exam performance.
- Use regression analysis to identify relationships and predict future outcomes.
- Apply statistical inference to draw conclusions about the population.
- Clean and reshape the data to prepare it for analysis.

## 📈 Analysis Methods

### 1. Regression Analysis

- Purpose: Understand relationships between variables and predict future values.
- Example Topics:
  - Effect of study hours on exam score
  - Combined effects of attendance, sleep, and mental health
  - Negative effects of Netflix and social media on performance
  - Impact of diet quality and parental education level
  - Interaction effects (e.g., study time × sleep time)

### 2. Statistical Inference

- Purpose: Draw conclusions about a population from sample data.
- Example Topics:
  - Exam score differences based on part-time job status
  - Differences in average scores between students in extracurricular activities
  - Estimate correlation and confidence intervals between study time and scores
  - Hypothesis testing for gender-based exam score differences

### 3. Data Wrangling

- Purpose: Preprocess and restructure the data for analysis.
- Example Tasks:
  - Create derived variables (e.g., total screen time, wellbeing score)
  - Identify and handle missing values
  - Summarize statistics by group
  - Sort and filter data
  - Pivot data between wide and long format

## 🛠️ Technologies Used

- Language: R
- Libraries: tidyverse, infer, ggplot2
- Techniques: regression analysis, statistical inference, data cleaning, visualization

## 📄 License

This project is licensed under the MIT License. See the LICENSE file for details.
