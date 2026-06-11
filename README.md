# E-Commerce Consumer Analytics & Logistics Optimization

## 📌 Overview

This repository contains an end-to-end data analytics project that analyzes **3,900 e-commerce transactions** to uncover the underlying drivers of customer lifetime value (CLV), fulfillment preferences, and subscription adoption.

The primary objective of this project is to bridge the gap between raw transactional data and actionable business strategy. By engineering an ETL pipeline and visualizing the outputs, this project identifies critical conversion gaps within the customer loyalty program and provides data-backed recommendations to optimize discount strategies, targeted marketing, and shipping operations.

## 📊 Dataset

The analysis is based on a comprehensive e-commerce dataset containing customer demographics, purchasing behavior, and logistics data.

* **Total Records:** 3,900 transactions
* **Total Features:** 18 columns
* **Key Dimensions:** Demographics (Age, Gender, Location), Fulfillment (Shipping Type), Financials (Purchase Amount, Discount Applied), and Engagement (Review Rating, Subscription Status).


## 🛠️ Tools & Technologies

This project demonstrates proficiency across the modern data stack:

* **Python (Pandas, NumPy):** Data ingestion, exploratory data analysis (EDA), missing value imputation, and feature engineering.
* **MS SQL Server:** Relational database management, complex querying, and metric aggregations.
* **Microsoft Power BI:** Interactive data visualization, DAX calculations, and executive dashboard design.
* **Gamma:** AI-assisted presentation design for the final executive slide deck.


## ⚙️ Project Steps & Architecture

### Phase 1: Data Preprocessing (Python)

* **Data Cleaning:** Addressed 37 missing values in the `Review Rating` column by intelligently imputing the median rating based on specific product categories.

* **Feature Engineering:** Engineered high-value analytical dimensions, including an `age_group` classification and a `purchase_frequency_days` metric for behavioral segmentation.

* **Standardization:** Standardized all column headers to `snake_case` for seamless SQL integration and dropped redundant features (`promo_code_used`).

### Phase 2: Database Storage & Querying (MS SQL Server)

* Loaded the cleansed dataset into MS SQL Server.
* Executed advanced SQL queries to analyze revenue by demographic, isolate discount-dependent SKUs, and evaluate average order value (AOV) across different shipping tiers.

### Phase 3: Business Intelligence (Power BI)

* Connected Power BI directly to the cleaned data model.
* Developed an interactive dashboard focused on a high "data-ink ratio," utilizing enterprise color palettes to reduce cognitive load and highlight key performance indicators (KPIs).

### Phase 4: Executive Reporting

* Compiled strategic findings into a high-level Business Intelligence report (PDF) and a presentation deck utilizing Gamma.

## 📈 Key Business Results

The analysis yielded several actionable strategic insights:

1. **The Subscription Paradox:** Discovered a massive conversion gap. Out of 3,116 "Loyal" customers, a staggering 2,518 repeat buyers (5+ purchases) are *not* subscribed to the loyalty program.
2. **Revenue Drivers:** Non-subscribers currently generate the vast majority of revenue ($170,436) compared to subscribers ($62,645).
3. **Demographic Targeting:** Male customers generate 2.1x more revenue ($157,890) than female customers ($75,191). The "Young Adult" cohort leads all age demographics in total spend ($62,143).
4. **Logistics Upselling:** Customers utilizing "Express" shipping yield a higher Average Order Value ($60.48) compared to "Standard" shipping ($58.46).
5. **Margin Protection:** Identified 839 "high-value bargain hunters" who utilized discounts but still exceeded the global average purchase amount, proving that strategic discounting drives upsells rather than just eroding margins.

## 🖥️ Dashboard Overview

The Power BI dashboard provides an interactive interface for stakeholders to explore the data.

* **KPI Cards:** Dynamic tracking of Total Customers, Average Purchase Amount, and Average Review Rating.
* **Visualizations:** Includes clustered column charts for fulfillment analysis, donut charts for subscription mix, and horizontal bar charts for demographic revenue breakdown.
* **Slicers:** Fully interactive filtering by Gender, Subscription Status, Category, and Shipping Type.

---

