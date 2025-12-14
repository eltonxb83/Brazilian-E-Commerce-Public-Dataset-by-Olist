
# Brazilian E-Commerce (Olist) – End-to-End Analytics & ML Platform

**From EDA → Machine Learning → Dashboard → Executive Presentation**  
Built on a production-grade data pipeline orchestrated with **Dagster**

---

## 1. Project Context (What This Solves)

This project transforms raw Brazilian E-Commerce (Olist) data into **business-ready insights** and **predictive intelligence**.

After data ingestion, transformation, and validation, this README focuses on the **analytics consumption layer**:

- Exploratory Data Analysis (EDA)
- Machine Learning
- Interactive Dashboard
- Executive Presentation

This aligns with how **business stakeholders actually consume data**.

---

## 2. End-to-End Architecture

```
Kaggle
  ↓
Pandas / CSV
  ↓
Meltano (Extract & Load)
  ↓
BigQuery (Data Warehouse)
  ↓
dbt (Transform & Test)
  ↓
Great Expectations (Validation)
  ↓
EDA → Machine Learning
  ↓
HTML Dashboard
  ↓
Executive Presentation
```

Dagster orchestrates **every step above** as a single reproducible pipeline.

---

## 3. Exploratory Data Analysis (EDA)

📂 Location:
```
ml/EDA_ML_Analysis.py
```

### Objectives
- Understand customer purchasing behavior
- Identify sales trends & seasonality
- Detect outliers & data issues
- Validate business assumptions

### Key Analyses
- Monthly & yearly sales trends
- Top-selling products & categories
- Customer purchase frequency
- Payment method distribution
- Delivery & review score analysis

### Tools Used
- pandas
- matplotlib / seaborn
- BigQuery (SQLAlchemy connection)

EDA results directly guide **feature engineering** for ML.

---

## 4. Machine Learning

### Goal
Demonstrate how curated warehouse data enables **predictive analytics**.

### ML Workflow
1. Feature selection from fact & dimension tables
2. Train / test split
3. Model training
4. Model evaluation
5. Business interpretation

### Example Use Cases
- Customer segmentation
- Sales volume prediction
- Revenue forecasting
- High-value customer identification

### Output
- Model performance metrics
- Feature importance
- Business interpretation (not just accuracy)

> This section shows *how data engineering enables data science*.

---

## 5. Analytics Dashboard (HTML)

📂 File:
```
index.html
```

🌐 Live Version:
```
https://pinghar.github.io/Brazilian-E-Commerce-Public-Dataset-by-Olist/
```

### Dashboard Capabilities
- KPI cards (Orders, Revenue, Customers)
- Sales trend analysis (Year / Month filters)
- Geographic distribution
- Seller & product performance
- Interactive filtering

### Why HTML (Not Tableau/Power BI)?
- Fully open-source
- Reproducible via GitHub Pages
- No licensing cost
- Deployable anywhere

This dashboard is designed for **CEO / COO / Business Teams**.

---

## 6. Dagster Orchestration (Analytics Layer)

Dagster ensures:
- EDA runs only after validated data
- ML runs only after EDA
- Dashboards reflect latest successful pipeline

### Run Dagster
```bash
dagster dev -m dagster_proj.definitions
```

UI:
```
http://localhost:3000
```

Dagster provides:
- Observability
- Dependency tracking
- Failure recovery
- Reproducibility

---

## 7. Executive Presentation (Final Deliverable)

📊 Slide Deck:
```
slides/Executive_Presentation.pdf
```

### Slide Flow
1. Business Problem
2. Data Pipeline Architecture
3. Data Quality Assurance
4. Key Insights from EDA
5. ML Findings & Business Value
6. Live Dashboard Demo
7. Strategic Recommendations
8. Risks & Future Enhancements

### Target Audience
- CEO / COO → Business impact
- CTO / Engineering → Architecture & scalability

---

## 8. Business Value Delivered

✅ Single Source of Truth  
✅ Faster Decision-Making  
✅ Scalable Analytics Platform  
✅ ML-Ready Data Foundation  
✅ Executive-Ready Insights  

This project demonstrates **real-world data engineering maturity**, not just coursework.

---

## 9. Future Enhancements

- Incremental dbt models
- Scheduled Dagster jobs
- Advanced ML models
- Feature store integration
- Role-based dashboard access
- CI/CD automation

---

## 10. Summary

This repository proves the ability to:
- Engineer reliable data pipelines
- Enable analytics & ML
- Communicate insights clearly to executives

**Data → Insight → Decision → Value**

---

**Program:** Advanced Professional Certificate in Data Science & AI (SCTP)  
**Project Type:** End-to-End Data Engineering & Analytics Platform
