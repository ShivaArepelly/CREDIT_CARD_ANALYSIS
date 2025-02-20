# Credit Card Financial Dashboard (Power BI & SQL)

### Dashboard Link : [https://app.powerbi.com/links/XNB-mrsRfP?ctid=6f6b1693-538c-4613-b7f4-e9416e6649bc&pbi_source=linkShare](https://app.powerbi.com/links/Vuv2mNiwqm?ctid=6f6b1693-538c-4613-b7f4-e9416e6649bc&pbi_source=linkShare)

## Project Overview
This dashboard provides insights into credit card transactions, customer spending behavior, and revenue patterns. It helps financial institutions understand their customer base, revenue streams, and card usage trends to optimize services and improve profitability.

### Steps followed 

**Data Collection & Import**
- Imported credit card transaction data into MYSQL Server for processing.
- Connected Power BI to SQL Server for real-time data access.

**Data Cleaning & Preparation (SQL)**
- Removed duplicates, missing values, and inconsistencies.
- Standardized card categories, transaction types, and customer demographics.
- Converted date formats for time-based analysis.
  
**Data Analysis & Querying (SQL)**
- Extracted key metrics:
  - Total Revenue ($55M) and Total Transactions (656K).
  - Revenue by Card Type, Transaction Type, and Job Category.
  - Quarterly trends and regional performance.
    
**Data Modeling & Transformation (Power BI)**
- Built relationships between tables for accurate reporting.
- Used Power Query for data transformation and ETL processes.
  
**Dashboard Development (Power BI & DAX)**

✅ Revenue & Transaction Trends

✅ Customer Segmentation (Job, Income, Age, Education)

✅ Card Usage & Spending Behavior

✅ Regional & Demographic Breakdown

✅ Quarterly & Weekly Spending Patterns

## DAX formulas used for KPIs creation

  
**AgeGroup** = SWITCH(

 TRUE(),
 
 'public cust_detail'[customer_age] < 30, "20-30",
 
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 
 'public cust_detail'[customer_age] >= 60, "60+",
 
 "unknown"
 
 )

 
  -----------------------------------------------------------------------------------------
**IncomeGroup** = SWITCH(

 TRUE(),
 
 'public cust_detail'[income] < 35000, "Low",
 
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 
 'public cust_detail'[income] >= 70000, "High",
 
 "unknown"
 
)


----------------------------------------------------------

**week_num2** = WEEKNUM('public cc_detail'[week_start_date])

**Revenue** = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]

-----------------------------------------------------

**Current_week_Reveneue** = CALCULATE(

 SUM('public cc_detail'[Revenue]),
 
 FILTER(
 
 ALL('public cc_detail'),
 
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))


------------------------------------------------------------------
**Previous_week_Reveneue** = CALCULATE(

 SUM('public cc_detail'[Revenue]),
 
 FILTER(
 
 ALL('public cc_detail'),
 'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

 
 -----------------------------------------------------------------------------------------
 
 # Report Snapshot (Power BI DESKTOP)

 
![Image](https://github.com/user-attachments/assets/e7c803fd-ed85-474c-9622-e0f429c9a7c4)

![Image](https://github.com/user-attachments/assets/0a7560d8-b2ef-4e99-8422-4d256b2e3cbd)


## Key Insights & Findings
**Revenue & Transactions Overview**

- Total Revenue: $55M across all card types.

- Total Transactions: 656K processed.

- Quarterly Trends: Revenue ranged between $13.3M – $14.2M per quarter.

**Customer Analysis**

- Top Job Categories:
  - Business Owners (31%) generate the highest revenue ($17M).
  - Government Employees & Self-Employed contribute $8M+ each.
- Top Income Groups:
  - High-income customers: $22M+ revenue.
  - Medium & Low-income groups: Contribute $8M – $10M each.
- Age Group Breakdown:
  - 30-40 age group leads with $14M revenue.
  - 50+ customers contribute $20M+ revenue combined.
**Card Usage & Revenue Distribution**
- By Card Type:
  - Blue Card: Highest revenue ($46M, 83% of total).
  - Silver, Gold, Platinum: Combined $9M revenue.
- By Transaction Type:
  - Swipe Transactions: $35M revenue (dominant method).
  - Chip & Online Transactions: $17M & $3M revenue, respectively.
**Regional & Demographic Insights**
- Top States by Revenue: Texas, New York, California, Florida, New Jersey (~$7M each).
- Marital Status Breakdown:
  - Married Customers: Highest spending (~$15M revenue).
  - Singles & Unknown Status: $11M+ each.
## Technology Stack
- Database: MYSQL Server (Data Cleaning, Querying, Analysis)
- Visualization: Power BI (DAX, KPIs, Interactive Dashboard)
- Data Processing: Power Query (ETL, Transformations)
## Dashboard Features
✅ Revenue & Transaction Trends Analysis

✅ Customer Segmentation by Job, Income, Age, and Education

✅ Card Usage & Spending Behavior

✅ Regional & Demographic Breakdown

✅ Quarterly & Weekly Spending Patterns
