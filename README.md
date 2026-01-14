# 🗣️ AI Chatbot Performance Analytics Dashboard

**End-to-End Data Analytics Portfolio Project** | SQL | Power BI | Python | DAX

[![Power BI Dashboard](https://img.shields.io/badge/PowerBI-Dashboard-blue?style=flat&logo=powerbi)](04_Power_BI)
[![Python EDA](https://img.shields.io/badge/Python-EDA-green?style=flat&logo=python)](04_Power_BI)
[![Data](https://img.shields.io/badge/Data-1000%20Rows-orange?style=flat&logo=dataset)](data/datachatbot_models_clean.csv)

---

## 🎯 Business Problem

Analyze **1,000 AI chatbot models** across **6 domains** (Retail, Finance, Healthcare, etc.) to:

- Identify **top performers** under **high load** (35+ concurrent queries)
- Quantify **latency degradation** under stress conditions
- Rank models by **performance efficiency** *(Accuracy ÷ Latency)*
- Recommend **optimization priorities** based on stress test results

### Key Metrics Delivered

| Metric | Value | Insight |
|------|------|------|
| **Stress Test Pass Rate** | 72% | 28% models fail under high load |
| **High Load Success** | 76% | Accuracy drops by 1.2 pts |
| **Latency Increase** | 28% | 319ms → 553ms |
| **Top Model Efficiency** | 0.857 | 🥇 Lin-BurnsBot (Retail) |

---

## 📊 Dashboard Highlights (5 Sheets)

1. **Overview** – KPIs, efficiency ratings (🟢🟡🔴)
2. **Performance Analysis** – Latency vs Accuracy scatter
3. **Domain Comparison** – Retail 🥇, Finance 🥈
4. **Load Analysis** – Stress test & degradation metrics
5. **Optimization Insights** – Ranked Top 20 🥇🥈🥉 + recommendations

---

## 🛠️ Tech Stack

- **Python (EDA):** Pandas, NumPy, Seaborn  
- **SQL:** Data modeling & aggregations  
- **Power BI:** Advanced DAX (RANKX, DIVIDE, VAR, SWITCH)  
- **GitHub:** Clean repository & documentation  

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/YOUR-USERNAME/ai-chatbot-performance-dashboard.git
cd ai-chatbot-performance-dashboard

# 2. Explore Python EDA
jupyter notebook 02_EDA_and_Data_Modeling.ipynb

# 3. Open Power BI Dashboard
# Power BI Desktop → Open AIChatbotPerformanceDashboard.pbix
```

---

## 📈 Key Insights

**🥇 Top Model:** Lin-BurnsBot (Retail) → 85.7% Efficiency

⚠️ **28%** of models fail stress test (latency > 600ms)

**💡 Recommendation:** Prioritize Model Pruning (Neural Architecture Search)

---

## 📁 Project Files

**01_Problem_Statement.pdf / .md**
→ Problem definition, objectives, key questions

**datachatbot_models_clean.csv**
→ 1,000 chatbot model interactions

**02_EDA_and_Data_Modeling.ipynb**
→ Full exploratory analysis & feature engineering

**03_SQL_Analysis.sql / .md**
→ SQL queries & analytical insights

**PowerBI Dashboard (.pbix)**
→ 5-sheet interactive analysis

**05_Project_Report.md**
→ End-to-end project explanation

**06_PDF_Report.pdf**
→ Final interview-ready report

**AI-Chatbot-Analytics-Plan.pdf**
→ Project roadmap

---

## 🎓 Skills Demonstrated

✅ Advanced DAX & ranking logic

✅ Feature Engineering (efficiency_rating, load_level)

✅ Data Quality (EDA, validation, cleaning)

✅ Visualization (KPIs, rankings 🥇🥈🥉)

✅ Business Impact (stress KPIs & optimization strategy)

---

## 👤 Author

**Built by:** N. Kishore  
**Role:** Data Analyst  
**LinkedIn:** [![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://www.linkedin.com/in/kishore--n/)


