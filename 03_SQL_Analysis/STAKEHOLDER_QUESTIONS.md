# 📊 Chatbot Performance Analysis – SQL Queries

This document contains a curated set of SQL queries used to analyze chatbot models across **performance efficiency, domains, load levels, optimization techniques, latency, and resource usage**.

Each section answers a specific analytical question and can be used directly in your notebook, README, or reporting workflow.

---

## 1️⃣ Top 10 Chatbot Models by Performance Efficiency

Identifies the most efficient chatbot models overall based on the `performance_efficiency` metric.

```sql
SELECT
    model_name,
    category,
    domain,
    response_accuracy,
    latency,
    concurrent_queries,
    performance_efficiency,
    load_level
FROM chatbot_performance
ORDER BY performance_efficiency DESC
LIMIT 10;
```

---

## 2️⃣ Domain-wise Performance Comparison

Compares how different domains (Finance, Healthcare, etc.) perform on average.

```sql
SELECT
    domain,
    COUNT(*) AS model_count,
    ROUND(AVG(response_accuracy), 2) AS avg_accuracy,
    ROUND(AVG(latency), 0) AS avg_latency_ms,
    ROUND(AVG(performance_efficiency), 3) AS avg_efficiency,
    ROUND(AVG(concurrent_queries), 0) AS avg_concurrency
FROM chatbot_performance
GROUP BY domain
ORDER BY avg_efficiency DESC;
```

---

## 3️⃣ Best Performing Models Under High Load

Finds models that maintain strong accuracy and low latency even under **high load**.

```sql
SELECT
    model_name,
    category,
    domain,
    response_accuracy,
    latency,
    concurrent_queries,
    performance_efficiency
FROM chatbot_performance
WHERE load_level = 'High'
  AND response_accuracy >= 85
  AND latency < 600
ORDER BY performance_efficiency DESC
LIMIT 15;
```

---

## 4️⃣ Most Effective Optimization Techniques

Evaluates which optimization strategies deliver the best overall results.

```sql
SELECT
    optimization_technique,
    COUNT(*) AS models_used,
    ROUND(AVG(response_accuracy), 2) AS avg_accuracy,
    ROUND(AVG(latency), 0) AS avg_latency,
    ROUND(AVG(performance_efficiency), 3) AS avg_efficiency,
    ROUND(AVG(memory_usage), 0) AS avg_memory_mb
FROM chatbot_performance
GROUP BY optimization_technique
ORDER BY avg_efficiency DESC;
```

---

## 5️⃣ Fastest Models for Real-Time Chat

Highlights models suitable for real-time chat based on low latency.

```sql
SELECT
    model_name,
    category,
    domain,
    latency,
    response_accuracy,
    performance_efficiency,
    load_level
FROM chatbot_performance
WHERE latency < 300
ORDER BY performance_efficiency DESC
LIMIT 20;
```

---

## 6️⃣ Best Category per Domain

Analyzes which model category performs best within each domain.

```sql
SELECT
    category,
    domain,
    COUNT(*) AS model_count,
    ROUND(AVG(response_accuracy), 2) AS avg_accuracy,
    ROUND(AVG(performance_efficiency), 3) AS avg_efficiency
FROM chatbot_performance
GROUP BY category, domain
HAVING model_count >= 5
ORDER BY avg_efficiency DESC;
```

---

## 7️⃣ Low Memory Usage with High Performance

Identifies memory-efficient models without sacrificing accuracy or latency.

```sql
SELECT
    model_name,
    domain,
    memory_usage,
    response_accuracy,
    latency,
    performance_efficiency,
    (response_accuracy / memory_usage) * 1000 AS efficiency_per_mb
FROM chatbot_performance
WHERE memory_usage < 800
ORDER BY efficiency_per_mb DESC
LIMIT 15;
```

---

## 8️⃣ Performance Degradation Under High Load

Measures how much efficiency drops when moving from low to high load.

```sql
WITH perf_summary AS (
    SELECT
        category,
        domain,
        load_level,
        COUNT(*) AS model_count,
        ROUND(AVG(response_accuracy), 2) AS avg_accuracy,
        ROUND(AVG(latency), 0) AS avg_latency,
        ROUND(AVG(performance_efficiency), 3) AS avg_efficiency
    FROM chatbot_performance
    GROUP BY category, domain, load_level
)
SELECT
    category,
    domain,
    MAX(CASE WHEN load_level = 'Low' THEN avg_efficiency END) AS low_load_eff,
    MAX(CASE WHEN load_level = 'High' THEN avg_efficiency END) AS high_load_eff,
    ROUND(
        (MAX(CASE WHEN load_level = 'High' THEN avg_efficiency END) /
         MAX(CASE WHEN load_level = 'Low' THEN avg_efficiency END)) * 100,
        1
    ) AS degradation_pct
FROM perf_summary
GROUP BY category, domain
HAVING low_load_eff IS NOT NULL
   AND high_load_eff IS NOT NULL
ORDER BY degradation_pct;
```

---

### ✅ Usage Notes

- Suitable for **EDA notebooks**, **Power BI / Tableau prep**, and **GitHub README**
- Queries assume a cleaned and validated `chatbot_performance` table
- Metrics like `performance_efficiency` should be precomputed

---

📌 _This file is designed to be directly saved as `chatbot_performance_analysis.md`._
