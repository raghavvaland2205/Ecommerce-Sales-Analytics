# E-Commerce Consumer Analytics & Logistics Optimization

## 📌 Overview

This repository contains an end-to-end data analytics project that analyzes **3,900 e-commerce transactions** to uncover the underlying drivers of customer lifetime value (CLV), fulfillment preferences, and subscription adoption. It demonstrates a complete analytics pipeline: from raw data ingestion and Python-based cleaning to SQL-driven insights and Power BI dashboard creation.

The primary objective of this project is to bridge the gap between raw transactional data and actionable business strategy. By engineering an ETL pipeline and visualizing the outputs, this project enables data-driven decision-making for revenue optimization and customer retention.

## 📊 Dataset

The analysis is based on a comprehensive e-commerce dataset containing customer demographics, purchasing behavior, and logistics data.

* **Total Records:** 3,900 transactions
* **Original Features:** 18 columns
* **Final Features:** 20 columns (18 original + 2 engineered)
* **Key Dimensions:** Demographics (Age, Gender, Location), Fulfillment (Shipping Type), Financials (Purchase Amount, Discount Applied), and Engagement (Review Rating, Subscription Status).

### Original Column Names (Raw Data):
1. Customer ID
2. Age
3. Gender
4. Item Purchased
5. Category
6. Purchase Amount (USD)
7. Location
8. Size
9. Color
10. Season
11. Review Rating
12. Subscription Status
13. Shipping Type
14. Discount Applied
15. Promo Code Used
16. Previous Purchases
17. Payment Method
18. Frequency of Purchases

## 🛠️ Tools & Technologies

This project demonstrates proficiency across the modern data stack:

* **Python (Pandas, NumPy):** Data ingestion, exploratory data analysis (EDA), missing value imputation, and feature engineering.
* **MS SQL Server:** Relational database management, complex querying, and metric aggregations.
* **Microsoft Power BI:** Interactive data visualization, DAX calculations, and executive dashboard design.
* **Gamma:** AI-assisted presentation design for the final executive slide deck.

## ⚙️ Project Steps & Architecture

### Phase 1: Data Preprocessing (Python)

* **Data Cleaning:** 
  - Identified 37 missing values in the `Review Rating` column (0.95% of data)
  - Imputed missing values using median rating by product category (intelligent grouping)
  - Result: 100% complete dataset with no data loss

* **Feature Engineering:** Engineered high-value analytical dimensions:
  - **`age_group`**: Classification of customers into four cohorts using quartile-based binning:
    - Young Adult (ages ~18-30)
    - Adult (ages ~31-43)
    - Middle-aged (ages ~44-57)
    - Senior (ages ~58-70)
  - **`purchase_frequency_days`**: Conversion of categorical frequency labels into numeric intervals:
    | Label | Days |
    |-------|------|
    | Weekly | 7 |
    | Fortnightly / Bi-Weekly | 14 |
    | Monthly | 30 |
    | Quarterly / Every 3 Months | 90 |
    | Annually | 365 |

* **Column Standardization:** 
  - Converted all column headers from mixed-case to `snake_case` (e.g., "Customer ID" → "customer_id")
  - Renamed `purchase_amount_(usd)` to `purchase_amount` for clarity
  - Dropped `promo_code_used` column as it was 100% correlated with `discount_applied` (redundant feature)
  - Final standardized columns:
    - customer_id, age, gender, item_purchased, category
    - purchase_amount, location, size, color, season
    - review_rating, subscription_status, shipping_type
    - discount_applied, previous_purchases
    - payment_method, frequency_of_purchases
    - **NEW:** age_group, purchase_frequency_days

### Phase 2: Database Storage & Querying (MS SQL Server)

* Loaded the cleansed dataset into MS SQL Server database: `Customer_Shipping_Behavior.dbo.customer`
* Executed 10 advanced SQL queries to:
  - Analyze revenue by demographic segments (Q1, Q3)
  - Identify discount-dependent SKUs and bargain hunters (Q2, Q6)
  - Evaluate Average Order Value (AOV) across shipping tiers (Q4)
  - Segment customers by purchase history: New, Returning, Loyal (Q7)
  - Discover subscription adoption patterns among repeat buyers (Q9)
  - Rank top products within categories using window functions (Q8)
  - Analyze revenue contribution by age group (Q10)

### Phase 3: Business Intelligence (Power BI)

* Connected Power BI directly to the cleaned SQL data model
* Developed an interactive dashboard focused on high "data-ink ratio," utilizing enterprise color palettes to reduce cognitive load
* Dashboard Components:
  - **KPI Cards:** Total Customers, Average Purchase Amount, Average Review Rating
  - **Clustered Column Charts:** Fulfillment analysis by shipping type
  - **Donut Charts:** Subscription mix visualization
  - **Horizontal Bar Charts:** Demographic revenue breakdown by gender and age group
  - **Interactive Slicers:** Filter by Gender, Subscription Status, Category, and Shipping Type

### Phase 4: Executive Reporting

* Compiled strategic findings into a high-level Business Intelligence report
* Created presentation deck utilizing Gamma for AI-assisted slide design
* Documented actionable recommendations for subscription growth and revenue optimization

## 📈 Key Business Results

The analysis yielded several actionable strategic insights:

1. **The Subscription Paradox:** Discovered a massive conversion gap. Out of 3,116 "Loyal" customers (5+ purchases), a staggering 2,518 repeat buyers are *not* subscribed to the loyalty program. **Revenue opportunity: $107,791**

2. **Revenue Drivers:** Non-subscribers currently generate the vast majority of revenue ($170,436) compared to subscribers ($62,645). This is driven by **volume, not value** — the customer base is predominantly non-subscribed.

3. **Demographic Targeting:** 
   - Male customers generate **2.1x more revenue** ($157,890) than female customers ($75,191)
   - The "Young Adult" cohort leads all age demographics in total spend ($62,143)
   - Clear opportunity for targeted marketing campaigns by segment

4. **Logistics Upselling:** Customers utilizing "Express" shipping yield higher Average Order Value ($60.48) compared to "Standard" shipping ($58.46), indicating premium service adoption and upsell opportunity.

5. **Margin Protection:** Identified **839 "high-value bargain hunters"** who utilized discounts but still exceeded the global average purchase amount ($59.76), proving that strategic discounting drives incremental upselling rather than cannibalizing margins.

## 🖥️ Dashboard Overview

The Power BI dashboard provides an interactive interface for stakeholders to explore the data:

* **KPI Cards:** Dynamic tracking of Total Customers, Average Purchase Amount, and Average Review Rating
* **Visualizations:** 
  - Clustered column charts for fulfillment analysis
  - Donut charts for subscription mix
  - Horizontal bar charts for demographic revenue breakdown
* **Slicers:** Fully interactive filtering by Gender, Subscription Status, Category, and Shipping Type

---

## 📁 Repository Structure

```
Ecommerce-Sales-Analytics/
├── 01_Raw_Data_Customer_Behavior.csv       # Raw customer transaction data (3,900 records, 18 columns)
├── 02_Data_Exploration_Queries.sql         # 10 advanced SQL queries for business intelligence
├── 03_Python_Data_Cleaning_EDA.ipynb       # Python notebook for data preprocessing & EDA
├── 04_PowerBI_Interactive_Dashboard.png    # Power BI dashboard screenshot
├── 05_Executive_Summary_Report.docx        # Executive summary and key findings
├── 06_Project_Presentation.pptx            # Presentation deck (Gamma-designed)
├── DATA_QUALITY_NOTES.md                   # Data validation and consistency checks
├── LICENSE                                 # MIT License
└── README.md                               # This file
```

## 🚀 How to Use This Repository

1. **Review the Data:** Start with `01_Raw_Data_Customer_Behavior.csv` to understand the raw data structure and dimensions.
2. **Run the Analysis:** Execute `03_Python_Data_Cleaning_EDA.ipynb` in Jupyter Notebook to see the cleaning, imputation, and feature engineering process step-by-step.
3. **Explore SQL Insights:** Review `02_Data_Exploration_Queries.sql` for 10 key business questions answered via SQL queries and window functions.
4. **View Dashboard:** Open `04_PowerBI_Interactive_Dashboard.png` for interactive dashboard design and visualization.
5. **Stakeholder Review:** Share `05_Executive_Summary_Report.docx` and `06_Project_Presentation.pptx` with leadership for decision-making.
6. **Data Quality Check:** Review `DATA_QUALITY_NOTES.md` for validation reports and consistency checks.

## 📝 Key Findings Summary

| Metric | Value |
|--------|-------|
| Total Revenue | $233,081 |
| Average Purchase Amount | $59.76 |
| Subscription Rate | 27.1% (1,053 / 3,900) |
| Non-Subscriber Revenue | $170,436 (73.1%) |
| Subscriber Revenue | $62,645 (26.9%) |
| **Customer Segments** | **Distribution** |
| New Customers | 268 (6.9%) |
| Returning Customers | 518 (13.3%) |
| Loyal Customers | 3,116 (79.9%) |
| **Shipping Preferences** | **Share** |
| Free Shipping | 17.3% |
| Standard Shipping | 16.2% |
| Express Shipping | 15.1% |
| Average Review Rating | 3.75 / 5.0 |
| Missing Data Handling | 37 values imputed (0.95%) |

## 🔍 Data Quality & Validation

✅ **Validated Consistency Across All Phases:**
- Raw data → Python processing → SQL queries → Power BI → Executive Report
- All column transformations documented and traceable
- 100% data completeness after preprocessing
- Feature engineering logic verified and tested

See `DATA_QUALITY_NOTES.md` for detailed validation report.

---

## 💡 Recommendations

### For Immediate Action:
1. **Subscription Conversion:** Target the 2,518 "Loyal" non-subscribers with upgrade campaigns
2. **Premium Shipping:** Promote Express shipping to high-value customers
3. **Strategic Discounts:** Implement tiered discount rules for margin protection

### For Medium-Term Growth:
1. **Demographic Targeting:** Tailor campaigns for Young Adult and Male segments
2. **Customer Retention:** Develop loyalty rewards specifically for high-frequency buyers
3. **Product Optimization:** Focus on top-performing categories identified in Q8 analysis

---

**License:** MIT  
**Created:** June 2026  
**Author:** Raghav Valand  
**Repository:** raghavvaland2205/Ecommerce-Sales-Analytics
