# SQLite-Business-Management-Database

- Overview

The Business Management Database System is designed to support end-to-end business operations within an organization.
It provides a structured and relational approach to managing departments, employees, customers, products, orders, projects, supplies, documents, and financial transactions.
The system is built using SQLite and focuses on data integrity, scalability, and real-world business scenarios.

- Department

The Department entity stores information about organizational departments, including the department name and location.
Each department can have multiple employees, making it the foundation for structuring the organization.

- Employees

The Employees entity manages all employee-related information such as names, email addresses, hire dates, and departmental assignments.
Each employee belongs to a single department and can be responsible for managing projects, handling customer orders, purchasing supplies, and maintaining documents.

- Customers

The Customers entity stores data about customer companies and their contact persons.
It also tracks customer email addresses, phone numbers, and total transaction amounts.
Each customer can place multiple orders, enabling the system to analyze customer value and sales performance.

- Products

The Products entity contains information about items sold by the company, including product names and unit prices.
Products can appear in multiple orders, allowing the system to track product sales and revenue.

- Suppliers

The Suppliers entity maintains information about external suppliers who provide materials and equipment.
It includes supplier contact details such as company name, contact person, email, and phone number.
Each supplier can be associated with multiple supply records.

- Projects

The Projects entity stores information related to business projects, including project names, timelines, budgets, and current status.
Each project is managed by an employee and may involve multiple supply records and financial transactions, allowing full cost and budget tracking.

Orders

The Orders entity records customer purchase transactions.
Each order is linked to a customer, a product, and the employee responsible for processing the order.
This structure enables detailed reporting on sales performance, customer behavior, and employee contributions.

- Supplies

The Supplies entity tracks procurement activities for projects.
It records information about purchased items, their costs, supply dates, associated suppliers, responsible employees, and related projects.
This allows the organization to monitor project expenses and supplier performance.

- Financial Transactions

The Financial Transactions entity records all income and expense transactions related to projects.
Each transaction includes a description, amount, transaction type (income or expense), and is linked to a specific project.
This enables accurate financial reporting and project-level budget analysis.

Documents

The Documents entity manages important business documents such as contracts, reports, and internal files.
Each document is assigned to a responsible employee and includes file location and upload date, supporting document tracking and accountability.

- Relationships Summary

The database follows a relational structure where departments are linked to employees, employees are connected to projects, orders, supplies, and documents, and projects are associated with supplies and financial transactions.
Customers place orders for products, suppliers provide materials through supply records, and all financial activities are tied back to projects.
This interconnected design ensures data consistency and supports comprehensive business analysis.

- Conclusion

This database system demonstrates practical SQL database design using real-world business logic.
It is suitable for learning, prototyping, and portfolio presentation, showcasing skills in relational modeling, foreign key constraints, and business-oriented data organization.

# Query Examples
- View employees with department information

SELECT e.first_name, e.last_name, d.dept_name, d.location
FROM employees e
JOIN department d ON e.dept_id = d.dept_id;

- View orders with customer, product, and employee details

SELECT 
    o.order_id, 
    o.order_date,
    c.company_name AS customer,
    p.product_name,
    e.first_name || ' ' || e.last_name AS employee,
    o.total_amount
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id
JOIN employees e ON o.emp_id = e.emp_id;

- View projects with budget and supply costs

SELECT 
    p.project_name,
    p.budget,
    SUM(s.cost) AS total_supplies_cost,
    p.status
FROM projects p
LEFT JOIN supplies s ON p.project_id = s.project_id
GROUP BY p.project_id;

