# Data Quality & Consistency Notes

## ✅ Verified Content Consistency

This document tracks data quality checks and consistency validations across all project files.

### File Consistency Check

| Component | Status | Notes |
|-----------|--------|-------|
| CSV Data File | ✅ | `01_Raw_Data_Customer_Behavior.csv` - 3,900 records, 18 features |
| Python Notebook | ✅ | `03_Python_Data_Cleaning_EDA.ipynb` - correctly processes raw data |
| SQL Queries | ✅ | `02_Data_Exploration_Queries.sql` - queries validated against database schema |
| Power BI Dashboard | ✅ | `04_PowerBI_Interactive_Dashboard.png` - visualizes cleaned data |
| Executive Report | ✅ | `05_Executive_Summary_Report.docx` - uses findings from SQL queries |
| Presentation | ✅ | `06_Project_Presentation.pptx` - presents key insights |

---

## 🔍 Data Validation Summary

### Missing Values
- **Review Rating:** 37 missing values (0.95%)
  - **Treatment:** Imputed using median by Category (categorical grouping)
  - **Result:** Zero missing values after processing

### Column Standardization
- **Original:** Mixed case with spaces (e.g., "Purchase Amount (USD)")
- **Processed:** Snake_case format (e.g., "purchase_amount")
- **Reason:** SQL Server compatibility and consistency

### Feature Engineering

#### 1. Age Group Classification
- **Method:** Quartile-based binning (pd.qcut)
- **Categories:** Young Adult, Adult, Middle-aged, Senior
- **Purpose:** Demographic segmentation for revenue analysis
- **Example:** Ages 18-30 → "Young Adult"

#### 2. Purchase Frequency Days
- **Method:** Categorical to numeric mapping
- **Mapping:**
  | Frequency Label | Days |
  |-----------------|------|
  | Weekly | 7 |
  | Fortnightly / Bi-Weekly | 14 |
  | Monthly | 30 |
  | Quarterly / Every 3 Months | 90 |
  | Annually | 365 |
- **Purpose:** Behavioral segmentation for CLV calculation

#### 3. Dropped Features
- **Promo Code Used:** Dropped because it is 100% correlated with "Discount Applied"
  - Analysis shows: Whenever `discount_applied = 'yes'`, `promo_code_used = 'yes'`
  - Redundancy: No value in retaining both columns

---

## 📊 Data Alignment Verification

### Python Notebook → SQL Queries
- ✅ Column names match after standardization
- ✅ Database schema corresponds to cleaned DataFrame
- ✅ 3,900 records consistent across all tools

### SQL Queries → Power BI
- ✅ Aggregated metrics in SQL queries feed into dashboard KPIs
- ✅ Demographic breakdowns align with dashboard slicers
- ✅ Revenue calculations verified

### Power BI → Executive Report
- ✅ Dashboard insights support reported findings
- ✅ Key metrics (revenue, subscription rate, AOV) are consistent
- ✅ Customer segments align across all documents

---

## 🎯 Analysis Validity

All analyses meet the following quality criteria:

1. **Data Completeness:** 99.05% complete (37 missing values imputed appropriately)
2. **Feature Relevance:** All features used in analysis are relevant to business objectives
3. **SQL Validity:** Queries follow best practices (proper JOINs, aggregations, window functions)
4. **Metric Accuracy:** All calculations independently verified
5. **Visualization Accuracy:** Dashboard visualizations correctly represent underlying data

---

## 📋 Checklist for Repository Users

- [ ] Verify CSV data integrity (row count: 3,900)
- [ ] Run Python notebook to confirm data preprocessing steps
- [ ] Execute SQL queries to validate database schema
- [ ] Review Power BI dashboard for visual accuracy
- [ ] Confirm findings in Executive Report match SQL query results
- [ ] Present findings using the prepared presentation deck

---

**Last Updated:** 2026-06-12
**Reviewed By:** Data Quality Team
