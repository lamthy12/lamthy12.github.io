-- ====================
-- PROJECT: Cleaning Data in Bank Marketing
-- DATABASE: MySQL
-- DATASET: UCI Bank Marketing Machine Learning
-- TOTAL RECORDS: 45211
-- ====================

-- 1. SELECT DATABASE
USE bank_marketing_project;

-- 2. CREATE a working copy of the raw dataset
-- Keep the original dataset unchanged

DROP TABLE IF EXISTS bank_marketing_clean;

CREATE TABLE bank_marketing_clean AS
SELECT *
FROM bank_marketing_raw;

-- ====================
-- 3. DATA QUALITY CHECKS
-- ====================

SELECT COUNT(*) AS total_rows
FROM bank_marketing_raw;

SELECT 
     SUM(CASE WHEN age is NULL THEN 1 ELSE 0 END) AS missing_age,
     SUM(CASE WHEN job is NULL THEN 1 ELSE 0 END) AS missing_job,
     SUM(CASE WHEN education is NULL THEN 1 ELSE 0 END) AS missing_education,
     SUM(CASE WHEN balance is NULL THEN 1 ELSE 0 END) AS missing_balance
FROM bank_marketing_raw;

SELECT 
	 SUM(CASE WHEN job = 'unknown' THEN 1 ELSE 0 END) AS unknown_job,
     SUM(CASE WHEN marital = 'unknown' THEN 1 ELSE 0 END) AS unknown_marital,
     SUM(CASE WHEN education = 'unknown' THEN 1 ELSE 0 END) AS unknown_education,
     SUM(CASE WHEN contact = 'unknown' THEN 1 ELSE 0 END) AS unknown_contact,
     SUM(CASE WHEN poutcome = 'unknown' THEN 1 ELSE 0 END) AS unknown_poutcome
FROM bank_marketing_raw;

SELECT
	 COUNT(*) AS total_rows,
     COUNT(DISTINCT
		  age, job, marital, education, 
          `default`, balance, housing, loan, 
          contact, day, month, duration,
          campaign, pdays, previous, poutcome, y
          ) AS unique_rows
FROM bank_marketing_raw;

-- 4. Data cleaning and standardization

ALTER TABLE bank_marketing_clean
ADD COLUMN subscription_status VARCHAR(15);

SET SQL_SAFE_UPDATES = 0;

UPDATE bank_marketing_clean
SET subscription_status =
    CASE
        WHEN y = 'yes' THEN 'Subscribed'
        WHEN y = 'no' THEN 'Not Subscribed'
        ELSE NULL
	END;

SET SQL_SAFE_UPDATES = 1;

SELECT 
	 y,
     subscription_status,
     COUNT(*) AS total_customers
FROM bank_marketing_clean
GROUP BY y, subscription_status;

-- 5. Feature data 

ALTER TABLE bank_marketing_clean
ADD COLUMN age_group VARCHAR(20);

SET SQL_SAFE_UPDATES = 0;

UPDATE bank_marketing_clean
SET age_group =
	CASE
        WHEN age BETWEEN 18 AND 29 THEN '18-29'
        WHEN age BETWEEN 30 AND 39 THEN '30-39'
        WHEN age BETWEEN 40 AND 49 THEN '40-49'
        WHEN age BETWEEN 50 AND 59 THEN '50-59'
        WHEN age >=60 THEN '60+'
        ELSE 'Unknown'
	END;
    
SET SQL_SAFE_UPDATES=1;

SELECT
      age_group,
      COUNT(*) AS total_customers
FROM bank_marketing_clean
GROUP BY age_group
ORDER BY age_group;

SELECT
      COUNT(*) AS total_rows,
      SUM(CASE WHEN age_group is NULL THEN 1 ELSE 0 END) AS missing_age_group,
      SUM(CASE WHEN subscription_status is NULL THEN 1 ELSE 0 END) AS missing_subscription_status
FROM bank_marketing_clean;

SELECT 
      subsciption_status,
      COUNT(*) AS total_customers
FROM bank_marketing_clean
GROUP BY subscription_status;

SELECT
      age_group,
      COUNT(*) AS total_customers
FROM bank_marketing_clean
GROUP BY age_group
ORDER BY age_group;
