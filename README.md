# SQLite-Business-Management-Database

This project is a sample database for a business management system, developed using SQLite to demonstrate SQL proficiency and database design skills

## Database Structure
- Departments
- Employees
- Customers (150 records)
- Products
- Orders
- Projects
- Financial Transactions
- Documents
- Supplies

##  Technologies
- SQLite
- SQL

## Project Structure

# Example Queries sql
SELECT company_name, customer_amounts
FROM customers
ORDER BY customer_amounts DESC
LIMIT 10;

SELECT COUNT(*) FROM customers;

- JOIN
SELECT o.order_id, c.company_name, o.total_amount
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;

- Business Report
SELECT 
  company_name,
  customer_amounts
FROM customers
WHERE customer_amounts > 100000
ORDER BY customer_amounts DESC;


