# Bank Marketing Data Cleaning | MySQL

## Project Overview

This project primarily focuses on evaluating data quality, catogorizing customer subscription information from a Portugueus bank's direct marketing campaign by using MySQL. By anazyling data, cleaning data and standardizing subscription outcomes are to improve the accuracy of subscription information, and prepare a structured data for further banking and customer employees

---

## 1. Project Problems

Before analyzing the effectiveness of a marketing campaign, it is important to understand whether the underlying customer data is reliable and consistent.

This project focuses on three main questions:

- Are there missing values, duplicate records, or unusual data values?
- How can customer subscription outcomes be presented more clearly?
- How can customer age information be organized for future analysis?

---

## 2. Dataset

**Source:** [UCI Machine Learning Repository – Bank Marketing]
(https://archive.ics.uci.edu/dataset/222/bank+marketing)

**File:** `bank-full.csv`

| Dataset Information | Details |
|---|---|
| Industry | Banking and Financial Services |
| Records | 45,211 |
| Original Columns | 17 |
| Database | MySQL |
| Target Variable | `y` (Term Deposit Subscription) |

- Variables Table in BankMarketing_Dataset includes:

Age
Job 
Marital Status
Education
Credit Default
Balance
Housing Loan 
Personal Loan
Contact
Day_of_week
Month
Duration
Campaign
Pdays
Previous 
Poutcome
(y) Term Deposit Subscription

---

## 3. Tools & SQL Skills

**Tools:** MySQL Workbench, Tableau, Visualization

**What SQL Techniques I used?:**
- Data profiling using `COUNT()`, `DISTINCT`, `MIN()` and `MAX()`
- Conditional logic using `CASE WHEN`
- Data transformation using `ALTER TABLE` and `UPDATE`
- Data validation using `GROUP BY` and aggregate functions

---

## 4. Data Preparation Process

### a. Data Quality Assessment

Examined the original dataset to identify potential data quality issues.

- Checked missing values and `unknown` categories.
- Compared total records against distinct combinations of the original 17 columns.
- Checked selected text fields for unnecessary whitespace.
- Reviewed age, account balance, call duration, and campaign contact ranges.

**Results:**
- 45,211 total records
- 45,211 distinct combinations across the original columns
- No unnecessary whitespace detected in the selected fields
- 3 records with zero call duration
- 3,766 records with negative account balances

Negative balances and other unusual values were retained because they were not confirmed to be data errors.

### b. Subscription Status Standardization

Created a separate table, `bank_marketing_clean`, to preserve the original dataset.

Added a new `subscription_status` column to make the subscription outcome easier to interpret.

| Original Value | Standardized Value |
|---|---|
| yes | Subscribed |
| no | Not Subscribed |

### c. Customer Age Segmentation

Created an `age_group` column using SQL `CASE WHEN` statements.

Customers were classified into five age categories: 18–29, 30–39, 40–49, 50–59, and 60+.

### d. Final Data Validation

Verified the resulting dataset to confirm that:

- All 45,211 customer records were retained.
- Both new columns contained no NULL values.
- Five age groups and two subscription categories were successfully created.

---

## 5. Key Findings

<text>**Subscription outcomes**</text>

| Subscription Status | Customers | Share |
|---|---:|---:|
| Subscribed | 5,289 | 11.7% |
| Not Subscribed | 39,922 | 88.3% |
| **Total** | **45,211** | **100%** |

Approximately 11.7% of the customer records show a successful term deposit subscription.

**Customer age distribution**

| Age Group | Customers |
|---|---:|
| 18–29 | 5,273 |
| 30–39 | 18,089 |
| 40–49 | 11,655 |
| 50–59 | 8,410 |
| 60+ | 1,784 |

Customers aged 30–39 represent the largest age group, accounting for approximately 40% of the dataset.

These findings describe the overall dataset and do not establish which customer characteristics caused subscription outcomes.

---

## Project Files

- `bank_marketing_cleaning.sql` 
- `bank-full.csv` 
- `tableau.pdf` 

---

## What I learned


---

## Conclusion

This project demonstrates foundational SQL skills in examining data quality, applying conditional transformations, preserving original records, and validating a prepared dataset. The resulting data structure supports future analysis of customer characteristics and term deposit subscriptions.

