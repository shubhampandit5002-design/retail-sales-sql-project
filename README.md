# Retail Sales Analysis (SQL)

A PostgreSQL project that cleans a retail transactions dataset and answers business questions about sales, categories and customers.

## Dataset
`data/retail_sales.csv`: around 2,000 transactions with date, time, customer ID, gender, age, category, quantity, price per unit, cost of goods sold and total sale.

## What I did
1. **Created the database and table** with suitable data types for each column
2. **Checked for missing values** in every key column and deleted the incomplete rows
3. **Explored the data** with SQL queries (below)

## Business questions answered
- All sales made on a specific date (2022-11-05)
- Clothing transactions in November 2022 with quantity of 4 or more
- Total sales and order count for each category
- Average age of customers who bought from the Beauty category
- All transactions with a total sale above 1000
- Number of transactions by gender in each category
- Top 5 customers by total sales

## SQL used
`SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`, `LIMIT`, aggregate functions (`SUM`, `COUNT`, `AVG`, `ROUND`), date formatting with `TO_CHAR`

## Files
- `sql/sql_retail_sale.sql`: full script (table creation, cleaning, analysis queries)
- `data/retail_sales.csv`: dataset

## Tools
PostgreSQL, SQL