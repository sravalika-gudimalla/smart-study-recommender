# 📚 Smart Study Recommender System

## 🚀 Overview

This project is a Smart Study Recommender System built as part of the Acadza AI Intern Assignment. The goal of the system is to analyze a student’s past performance data and recommend what they should study next in a structured, step-by-step manner.

The system processes multiple test and assignment attempts of students, identifies patterns such as strengths, weaknesses, and behavioral issues, and generates personalized study recommendations using both rule-based logic and a similarity-based approach.

---

## 🧠 Approach

I approached this problem in three main stages: data preprocessing, performance analysis, and recommendation generation.

First, I cleaned and standardized the input data, especially the marks field which had inconsistent formats. Then, I built an analysis engine to extract meaningful insights such as average score, accuracy, speed, and completion rate. Finally, I designed a recommender system that suggests targeted questions and study actions based on the student’s weak areas.

The overall idea was to simulate how a real EdTech platform would guide a student step-by-step rather than just showing scores.

---

## 🧹 Data Cleaning

One of the main challenges in this dataset was the inconsistent format of marks. The marks field appeared in multiple formats such as:

* `"68/100"`
* `"+52 -8"`
* `"34/75 (45.3%)"`
* `"28"`

To handle this, I implemented a normalization function that converts all formats into a consistent percentage-based score. This ensured that all analysis calculations were accurate and comparable.

Additionally, I cleaned the question bank by:

* Removing duplicate questions
* Handling missing or null difficulty values (defaulted to 3)
* Skipping questions without valid answers
* Normalizing question IDs from different formats

---

## 📊 Performance Analysis

For each student, I analyzed their performance across all attempts and calculated:

* Average score
* Accuracy (attempted vs total questions)
* Average time per question
* Completion rate

I also performed chapter-wise analysis to identify:

* Strengths (average score > 60)
* Weaknesses (average score < 40)

Based on these metrics, I detected key issues such as:

* Low score (concept gaps)
* Slow solving speed
* Low accuracy
* Poor time management

This helped in understanding not just *what* the student scored, but *why* they performed that way.

---

## 🎯 Recommendation Logic

The recommendation system combines rule-based logic with a similarity-based approach.

### 1. Rule-Based Recommendations (DOST Mapping)

Based on detected issues, I mapped them to appropriate DOSTs:

* Low score → Concept learning, Formula revision
* Slow speed → Clicking Power (speed drills)
* Low accuracy → Picking Power (MCQ practice)
* Time issues → Speed Race (timed tests)

### 2. Similarity-Based Question Recommendation

I also implemented a cosine similarity-based recommender. Each student is represented as a feature vector of weaknesses across topics, and questions are represented by topic and difficulty.

The system matches student weakness profiles with relevant questions and recommends the most suitable ones.

---

## 🐞 Debug Process

The provided recommender code had a subtle but critical bug. Although it initially computed a student-specific profile, it was incorrectly overwritten with the cohort average during normalization.

This resulted in all students receiving very similar recommendations, which defeated the purpose of personalization.

I identified this issue by observing the lack of variation in outputs and tracing the vector calculations. I fixed it by correctly normalizing the student’s own profile instead of replacing it.

After the fix, the recommendations became aligned with individual student weaknesses.

---

## 📁 Outputs

The system generates structured outputs for all students and saves them in a `sample_outputs/` folder. Each file contains:

* Performance analysis
* Identified strengths and weaknesses
* Recommended questions

Additionally, I designed a clean and readable console output format that presents insights in a user-friendly way.

---

## 🔮 Future Improvements

Given more time, I would enhance this system by:

* Incorporating machine learning models for adaptive recommendations
* Adding difficulty progression based on student improvement
* Using time-series analysis to track performance trends
* Personalizing study schedules over multiple days

---

## ✅ Conclusion

This project demonstrates how raw student performance data can be transformed into actionable insights and personalized study plans. The focus was on building a practical, interpretable, and student-centric recommendation system.

---

⭐ Thank you for reviewing my submission!
