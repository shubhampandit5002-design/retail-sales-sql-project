# 🛍️ Retail Sales Analysis - SQL Project

An end-to-end data analysis project using **PostgreSQL / SQL** to clean, explore, and answer critical business questions based on a retail sales dataset. 

This project demonstrates core data analyst skills: handling missing values, performing exploratory data analysis (EDA), and writing complex queries (aggregations, GROUP BY, CTEs, and window functions).

---

# 📂 Repository Structure
    ```text
    retail-sales-sql-project/
    │
    ├── data/
    │   └── retail_sales.csv              # Cleaned retail transactions dataset
    │
    ├── sql/
    │   └── sql_retail_sale.sql           # Complete SQL script (Schema, Cleaning, EDA)
    │
    └── README.md


# 🛠️ Project Steps & SQL Implementation
## 1. Database & Table Creation
Setting up the database structure and defining appropriate data types for transactions, customer demographics, categories, quantities, and prices.

## 2. Data Cleaning & Handling Nulls
Checking for missing values across critical columns and removing or handling null records to ensure data integrity before analysis:

-- Example: Checking for null values
SELECT * FROM retail_sales
WHERE transactions_id IS NULL
   OR sale_date IS NULL
   OR sale_time IS NULL
   OR customer_id IS NULL
   OR gender IS NULL
   OR age IS NULL
   OR category IS NULL
   OR quantity IS NULL
   OR price_per_unit IS NULL
   OR cogs IS NULL
   OR total_sale IS NULL;

## 3. Exploratory Data Analysis (EDA) & Business Key Problems
Answering core retail performance questions using advanced SQL aggregation queries:

### Retrieve all columns for sales made on '2022-11-05':

SELECT * FROM retail_sales 
WHERE sale_date = '2022-11-05';

### Find transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022:

SELECT * FROM retail_sales 
WHERE category = 'Clothing' 
  AND TO_CHAR(sale_date, 'YYYY-MM') = '2022-11' 
  AND quantity >= 4;

### Calculate the total sales (total_sale) for each category:

SELECT category, SUM(total_sale) as net_sale, COUNT(*) as total_orders 
FROM retail_sales 
GROUP BY category;

### Find the average age of customers who purchased items from the 'Beauty' category:

SELECT ROUND(AVG(age), 2) as avg_age 
FROM retail_sales 
WHERE category = 'Beauty';

### Find all transactions where the total_sale is greater than 1000:

SELECT * FROM retail_sales 
WHERE total_sale > 1000;

### Find the total number of transactions (transaction_id) made by each gender in each category:

SELECT category, gender, COUNT(*) as total_trans 
FROM retail_sales 
GROUP BY category, gender 
ORDER BY category;

### Find the top 5 customers based on the highest total sales:

SELECT customer_id, SUM(total_sale) as total_sales 
FROM retail_sales 
GROUP BY customer_id 
ORDER BY total_sales DESC 
LIMIT 5;

# 💡 Key Business Takeaways
Peak Sales & Demographics: Identified high-volume product categories and dominant customer age/gender segments driving gross revenue.

Data Hygiene: Implemented robust preprocessing queries to filter out anomalies and incomplete transaction rows.