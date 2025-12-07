# Brazilian E-Commerce Data Pipeline (End-to-End Modern Data Stack)

## Meltano → BigQuery → dbt (Star Schema) → Great Expectations → Dagster → Machine Learning → GitHub Dashboard

Live interactive dashboard:  
👉 **https://pinghar.github.io/Brazilian-E-Commerce-Public-Dataset-by-Olist/**

---

## 1. Architecture Overview

```
Kaggle → Meltano → BigQuery (raw)
           ↓
        dbt (staging → dim → fact)
           ↓
      GX validation
           ↓
      Dagster orchestration
           ↓
ML (prediction + feature store)
           ↓
Dashboard (GitHub Pages)
```

---

## 2. Meltano: Extract → Load into BigQuery

### Installation  
```bash
pip install meltano
meltano init olist_pipeline
cd olist_pipeline
```

### Add extractors and loaders  
```bash
meltano add extractor tap-kaggle
meltano add loader target-bigquery
```

### Run Pipeline  
```bash
meltano run tap-kaggle target-bigquery
```

---

## 3. dbt: Build Star Schema in BigQuery

### Star Schema Output  
- dim_customers  
- dim_products  
- dim_sellers  
- dim_dates  
- fact_order_items  

### Run dbt  
```bash
dbt deps
dbt build
```

---

## 4. Great Expectations (GX)

```bash
python GX_Validation_Report.py
```

Outputs HTML data quality reports.

---

## 5. Dagster Workflow Orchestration

```bash
dagster dev
```

Schedules Meltano → dbt → GX → ML.

---

## 6. Machine Learning  
Models included in `ml_eda.ipynb`:  
- Order value prediction  
- Customer segmentation  
- Review score modeling  

---

## 7. Dashboard (GitHub Pages)

Hosted at:  
👉 **https://pinghar.github.io/Brazilian-E-Commerce-Public-Dataset-by-Olist/**

---

## 8. CEO Summary

- Revenue trend grows YoY  
- São Paulo dominates customer base  
- Freight cost is major margin factor  
- Review score strongly predicts churn  
- Top categories generate 70% of revenue  

---

## 9. Run Entire Pipeline

```bash
meltano run tap-kaggle target-bigquery
dbt build
python GX_Validation_Report.py
dagster dev
python ml/train.py
```

---

## 10. Repository Structure

```
meltano/
dbt/
GX/
dagster_pipeline/
ml/
docs/index.html
README.md
```
