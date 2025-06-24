# walmart-retail-insights

Performed Exploratory Data Analysis and SQL querying on Walmart retail sales data using Python and MySQL. Uncovered insights on customer behavior, product trends, and branch-wise performance with visualizations and queries.

The dataset (Walmart.csv) contains transaction-level data from three Walmart branches across different cities. Each record includes:

Invoice_ID, Branch, City

Customer_type, Gender

Product_line, Unit_price, Quantity

Payment method, Tax, Total, Date, Time

COGS, Gross_income, Rating

After importing into MySQL, the data is stored in a table named walmart_sales.

🛠 SQL Skills Practiced:
✅ Basic SQL Queries
SELECT specific columns from the table

WHERE clause to filter by city, gender, product line, etc.

ORDER BY to sort sales by revenue, quantity, or ratings

✅ Aggregation & Grouping
GROUP BY used to analyze:

Sales per city

Average rating by product line

Revenue by gender

Aggregate functions used: SUM(), AVG(), COUNT(), MAX(), MIN()

✅ Joins
INNER JOIN used with a secondary table (branch_info) to add branch manager details to sales records

✅ Date and Time Functions
MONTH(), DAY(), HOUR() to break sales into time periods

Used to identify peak sales hours or best-performing months

✅ Aliasing & Limiting Results
AS for readable column aliases

LIMIT to restrict query output 

Example SQL Queries:

1. Total revenue by city
SELECT City, SUM(Total) AS Revenue
FROM walmart_sales
GROUP BY City
ORDER BY Revenue DESC;

2. Average rating per product line
SELECT Product_line, ROUND(AVG(Rating), 2) AS Avg_Rating
FROM walmart_sales
GROUP BY Product_line
ORDER BY Avg_Rating DESC;

3. Female customers in Yangon
SELECT * FROM walmart_sales
WHERE Gender = 'Female' AND City = 'Yangon';

4. Highest grossing invoices
SELECT Invoice_ID, Total
FROM walmart_sales
ORDER BY Total DESC
LIMIT 5;

5. Join with branch_info to fetch manager names
SELECT a.Invoice_ID, a.Total, b.Branch_Manager
FROM walmart_sales a
INNER JOIN branch_info b ON a.Branch = b.Branch;
