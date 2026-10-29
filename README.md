# 🧠 Data-Driven Education: Identifying At-Risk Cohorts for Wellness Interventions

📄 **[Click here to view the full PDF Report exported from DataLab](Datacamp-Analyzing%20Student's%20Mental%20Health.pdf)**

## 📌 Executive Summary
This project analyzes the psychological impact of studying abroad on international students. Using **PostgreSQL**, I queried and aggregated mental health survey data to uncover how the length of stay correlates with depression (PHQ), social connectedness (SCS), and acculturative stress (AS). The primary objective is to provide actionable data for university administrations to optimize the allocation of student wellness resources.

## 🛠️ Tech Stack & Skills
- **SQL (PostgreSQL):** Relational data querying, `GROUP BY` aggregations, filtering, and mathematical functions (`ROUND`, `AVG`, `COUNT`).
- **Data Visualization:** Trend analysis and sample size monitoring via DataLab.
- **Analytical Skills:** Cohort analysis, descriptive statistics, and translating raw metrics into operational business insights.

## 📊 The Business Problem
Universities manage limited budgets for student wellness and psychological support programs. By analyzing the dataset, this project answers a critical operational question: **At what stage of their academic journey do international students experience the highest levels of stress, and where should proactive intervention efforts be focused?**

## 💻 Methodology & SQL Implementation
To extract these insights, I engineered a query to isolate international students, group them by their temporal cohort (years of stay), and calculate the average scores for each mental health metric while tracking the sample size to ensure statistical relevance:

```sql
-- Extracting cohort averages for international students
SELECT 
    stay, 
    COUNT(inter_dom) AS count_int,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
