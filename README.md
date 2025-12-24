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

SELECT
    orders.order_id,
    customers.company_name,
    orders.total_amount
FROM orders
JOIN customers ON orders.customer_id = customers.customer_id;

- Business Report

SELECT 
  company_name,
  customer_amounts
FROM customers
WHERE customer_amounts > 100000
ORDER BY customer_amounts DESC;


