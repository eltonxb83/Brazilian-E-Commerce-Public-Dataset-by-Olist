# Brazilian E-Commerce Live BigQuery Dashboard

Live dashboard URL (GitHub Pages):  
**https://pinghar.github.io/Brazilian-E-Commerce-Public-Dataset-by-Olist/**

> Note: To see live data, users must sign in with a Google account that has
> read access to the BigQuery project **`durable-ripsaw-477914-g0`**.

---

## 1. Executive Summary (for CEO / COO)

This dashboard provides a **single, live view** of key performance indicators for
a Brazilian e-commerce marketplace (Olist dataset). It focuses on three
questions leadership often asks:

1. **Where are our customers and sellers located?**  
2. **Which products and sellers drive the majority of order volume?**  
3. **How is demand evolving over time?**

The data lives in **Google BigQuery**, and the dashboard reads it directly
through secure Google authentication. This means:

- No exports / manual Excel refreshes  
- Always-up-to-date data (as soon as BigQuery is refreshed)  
- Access can be controlled at the Google account level

---

## 2. What the Dashboard Shows

The home page is split into six tiles.

### 2.1 Customer Distribution per State

- **Question:** Where is our customer base concentrated?  
- **Data:** `dim_customers`  
- **What you see:** A treemap showing the number of **unique customers** in each
  Brazilian state.  
- **How to use:**
  - Quickly identify **priority regions** for marketing and logistics.
  - Compare customer concentration vs seller concentration (see next tile).

---

### 2.2 Seller Distribution per State

- **Question:** Do we have enough sellers where our customers are?  
- **Data:** `dim_sellers`  
- **What you see:** A treemap of **seller counts** per state.  
- **How to use:**
  - Spot states with **customer demand but weak seller coverage**.
  - Guide seller acquisition / onboarding strategy.
  - Support COO in **network and logistics planning**.

---

### 2.3 Top 100 Sellers

- **Question:** Who drives most of our orders? How concentrated is our risk?  
- **Data:** `fact_orders` (joined to `dim_sellers`)  
- **Metric:** Number of **order items** per seller.  
- **What you see:**
  - A ranked bar chart (1 = top seller) showing each seller’s order volume.
  - Hover tooltip displays **seller city** and item count.  
- **How to use:**
  - Identify top strategic sellers for **priority support and negotiations**.
  - Assess **concentration risk** if too much volume depends on a few sellers.
  - Support promotional or partnership decisions.

---

### 2.4 Top 50 Product Categories Sold

- **Question:** Which categories dominate our business? Are we diversified?  
- **Data:**  
  - `fact_orders`  
  - `olist_products`  
  - `product_category_name_translation` (for English category names)  
- **Metric:** Count of order items per product category.  
- **What you see:**
  - A horizontal bar chart of the **top 50 categories** by order volume.
- **How to use:**
  - Understand **core categories** that drive demand.
  - Decide where to invest in:
    - assortment expansion,
    - campaigns,
    - or improving service levels.
  - Identify **long-tail categories** that might require a different strategy.

---

### 2.5 Sales per Month

- **Question:** Are we growing? Where is seasonality?  
- **Data:** `fact_orders`  
- **Metric:** Number of **distinct orders** per month.  
- **What you see:**
  - Line chart with monthly order counts (YYYY-MM).
- **How to use:**
  - Track **growth trends** and **seasonal peaks**.
  - Support discussions on:
    - inventory,
    - staffing,
    - marketing timing.
  - Compare with external events (holidays, campaigns, etc.).

---

### 2.6 About / Notes

- Explains the purpose of the dashboard for leadership.
- Suggests additional analyses that can be added later (e.g. revenue, reviews,
  payment types).

---

## 3. How to Use the Dashboard

1. Open the live URL:  
   **https://pinghar.github.io/Brazilian-E-Commerce-Public-Dataset-by-Olist/**
2. Click **“Sign in with Google”** in the top-right corner.
3. Sign in with a Google account that has read access to the BigQuery project.
4. After login, the tiles will load automatically:
   - You can **hover, zoom, and pan** any chart.
   - Use the legend / treemap hierarchy to focus on specific states or
     categories.

For external stakeholders, access can be limited by controlling **who has
BigQuery permissions**; the HTML site itself contains no raw data, only the
visuals generated after secure login.

---

## 4. Data Model (for COO / Technical Audience)

The dashboard is powered by a simple **star schema** in BigQuery:

- **Fact table**
  - `fact_orders`  
    - Grain: one row per order item  
    - Key fields: `order_id`, `customer_id`, `seller_id`, `product_id`,
      `order_purchase_timestamp`  

- **Dimension tables**
  - `dim_customers`  
    - Customer attributes including `customer_state`
  - `dim_sellers`  
    - Seller attributes including `seller_state`, `seller_city`
  - Raw product tables used for categorisation:
    - `olist_products`
    - `product_category_name_translation`

This structure allows fast aggregation **by customer**, **seller**, **category**
and **time** without repeatedly joining the raw Olist tables.

---

## 5. Technical Architecture (High Level)

Pipeline (current or intended):

1. **Source**: Olist Brazilian E-Commerce dataset (Kaggle).
2. **Storage**: Data landed in **Google BigQuery** under dataset `ecommerce`.
3. **Transformations**:
   - Dim/fact tables materialised in BigQuery (`dim_*`, `fact_*`).
4. **Validation (optional next step)**:
   - Add Great Expectations or dbt tests to validate row counts, nulls, etc.
5. **Presentation**:
   - Static HTML dashboard (`index.html`) hosted on **GitHub Pages**.
   - JavaScript front-end uses:
     - **Google API Client (gapi)** for OAuth and BigQuery queries.
     - **Plotly.js** for interactive charts.

No server-side code is required; everything runs in the browser, connecting
directly (and securely) to BigQuery.

---

## 6. Possible Future Enhancements

For roadmap discussions with leadership:

- Add **revenue and margin** metrics, not just order counts.
- Add **delivery performance** KPIs (on-time vs delayed orders).
- Add **customer review scores** by seller / category.
- Create **drill-through** pages for individual states or top sellers.
- Automate data ingestion from production systems instead of Kaggle.

---

## 7. Ownership

This dashboard and pipeline were designed and implemented by **LIM PING HAR
(Pinky)** as part of the NTU PACE Data Science & AI programme.

For questions, enhancements, or access requests, please contact the owner.
