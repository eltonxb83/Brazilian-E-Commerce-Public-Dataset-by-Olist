
---

## 🖼️ Architecture Flow Diagram

> **Business → Engineering → ML → Dashboard in one continuous pipeline**

```mermaid
flowchart LR
    A[Kaggle Dataset] --> B[Pandas Processing]
    B --> C[CSV Files]
    
    C --> D[Meltano<br><b>Extract & Load</b>]
    D --> E[(BigQuery<br><b>Data Warehouse</b>)]
    
    E --> F[dbt<br><b>Transform</b>]
    F --> G[dbt-expectations<br><b>Data Quality</b>]
    
    G --> H[EDA<br><b>Exploration</b>]
    H --> I[Machine Learning]
    I --> J[Dashboard<br><b>Streamlit / Power BI / HTML</b>]
    
    style A fill:#E3F2FD,stroke:#1E88E5
    style B fill:#E8F5E9,stroke:#43A047
    style C fill:#F3E5F5,stroke:#8E24AA
    style D fill:#FFFDE7,stroke:#FBC02D
    style E fill:#E0F7FA,stroke:#00ACC1
    style F fill:#FBE9E7,stroke:#FB8C00
    style G fill:#FFEBEE,stroke:#E53935
    style H fill:#E1F5FE,stroke:#039BE5
    style I fill:#E8F5E9,stroke:#43A047
    style J fill:#F9FBE7,stroke:#9E9D24

