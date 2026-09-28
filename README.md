# DATA-TRANSFORMER
⚡ DATA TRANSFORMER
Turning Raw Data → Meaningful Insights

A practical SQL project for transforming, analyzing, and reporting corporate data using advanced MySQL techniques.

🌐 About The Project

Data Transformer is an advanced SQL project that simulates a Corporate Data Analysis System.

The project works with three major areas:

👥 Customer Information
       ↓
🛒 Sales Transactions
       ↓
👨‍💼 Employee Performance
       ↓
📊 Data Analysis & Transformation

It demonstrates how SQL can transform raw database records into useful business information.

🎯 Main Goals

This project focuses on:

SQL Concept	Purpose
🔗 JOINs	Combine data from multiple tables
🔍 Subqueries	Perform advanced filtering
📅 Date Functions	Analyze dates
🔤 String Functions	Clean and transform text
🪟 Window Functions	Perform analytical calculations
🧩 CASE	Categorize and classify data
🗃️ Database Architecture

The project contains 3 main tables.

👥 Customers
CustomerID
FirstName
LastName
Email
RegistrationDate

Stores customer registration and contact information.

🛍️ Orders
OrderID
CustomerID
OrderDate
TotalAmount

Stores customer purchase transactions.

👨‍💼 Employees
EmployeeID
FirstName
LastName
Department
HireDate
Salary

Stores employee and salary information.

🔗 01 — SQL JOINS

Joins connect related information from different tables.

INNER JOIN

Returns customers who have matching orders.

SELECT
    o.OrderID,
    o.OrderDate,
    o.TotalAmount,
    c.FirstName,
    c.LastName
FROM Orders o
INNER JOIN Customers c
ON o.CustomerID = c.CustomerID;
LEFT JOIN

Returns all customers, including customers without orders.

RIGHT JOIN

Returns all orders, including orders without matching customers.

FULL OUTER JOIN

MySQL does not directly support FULL OUTER JOIN, so the project uses:

LEFT JOIN
    +
RIGHT JOIN
    +
UNION
🔍 02 — SUBQUERIES

Subqueries allow one SQL query to work inside another query.

Customers with above-average orders
SELECT DISTINCT
    c.CustomerID,
    c.FirstName,
    c.LastName
FROM Customers c
JOIN Orders o
ON c.CustomerID = o.CustomerID
WHERE o.TotalAmount > (
    SELECT AVG(TotalAmount)
    FROM Orders
);
Employees with above-average salary
SELECT
    EmployeeID,
    FirstName,
    LastName,
    Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
📅 03 — DATE TRANSFORMATION

Date functions help extract and transform date information.

Extract Year & Month
SELECT
    OrderID,
    OrderDate,
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth
FROM Orders;
Calculate Date Difference
SELECT
    OrderID,
    OrderDate,
    CURDATE() AS CurrentDate,
    DATEDIFF(CURDATE(), OrderDate) AS DaysDifference
FROM Orders;
Readable Date Format
SELECT
    OrderID,
    DATE_FORMAT(OrderDate, '%d-%b-%Y') AS FormattedDate
FROM Orders;

Example:

2023-07-01
     ↓
01-Jul-2023
🔤 04 — STRING TRANSFORMATION

SQL string functions help clean and transform text.

Full Name
SELECT
    CONCAT(FirstName, ' ', LastName) AS FullName
FROM Customers;
Uppercase / Lowercase
SELECT
    UPPER(FirstName) AS FirstNameUpper,
    LOWER(LastName) AS LastNameLower
FROM Customers;
Replace Text
SELECT
    REPLACE(FirstName, 'John', 'Jonathan') AS UpdatedName
FROM Customers;
Remove Extra Spaces
SELECT
    TRIM(Email) AS CleanEmail
FROM Customers;
🪟 05 — WINDOW FUNCTIONS

Window functions perform calculations across related rows while keeping individual records visible.

Running Total
SELECT
    OrderID,
    OrderDate,
    TotalAmount,
    SUM(TotalAmount) OVER (
        ORDER BY OrderDate, OrderID
    ) AS RunningTotal
FROM Orders;
Order Ranking
SELECT
    OrderID,
    TotalAmount,
    RANK() OVER (
        ORDER BY TotalAmount DESC
    ) AS OrderRank
FROM Orders;
🧩 06 — CASE EXPRESSION

CASE is used to create categories based on conditions.

💰 Order Discount
SELECT
    OrderID,
    TotalAmount,
    CASE
        WHEN TotalAmount > 1000 THEN '10% Off'
        WHEN TotalAmount > 500 THEN '5% Off'
        ELSE 'No Discount'
    END AS Discount
FROM Orders;
👨‍💼 Salary Category
SELECT
    EmployeeID,
    FirstName,
    LastName,
    Salary,
    CASE
        WHEN Salary > 60000 THEN 'High'
        WHEN Salary >= 50000 THEN 'Medium'
        ELSE 'Low'
    END AS SalaryCategory
FROM Employees;
🧠 SQL SKILLS COVERED
                    DATA TRANSFORMER
                           │
        ┌──────────────────┼──────────────────┐
        ↓                  ↓                  ↓
      JOINS            SUBQUERIES       FUNCTIONS
        │                  │                  │
   INNER/LEFT/       AVG / Filtering    DATE / STRING
   RIGHT/UNION
        │                  │                  │
        └──────────────────┼──────────────────┘
                           ↓
                  WINDOW FUNCTIONS
                           │
                           ↓
                      CASE EXPRESSION
                           │
                           ↓
                  📊 BUSINESS INSIGHTS
🛠️ TECHNOLOGY STACK
💾 Database       : MySQL
⌨️ Language       : SQL
🧰 Tool           : MySQL Workbench / SQLBook
📚 Project Type   : Academic / Data Analysis
📂 PROJECT STRUCTURE
📁 Data-Transformer
│
├── 📄 Data_Transformer.sql
│
└── 📄 README.md
▶️ HOW TO RUN
1. Open MySQL Workbench / SQLBook
2. Create the database
CREATE DATABASE data_transformer;
3. Select the database
USE data_transformer;
4. Create tables
Customers
Orders
Employees
5. Insert sample data

Add the provided 10 records to each table.

6. Execute queries

Run the queries for:

✓ Joins
✓ Subqueries
✓ Date Functions
✓ String Functions
✓ Window Functions
✓ CASE Expressions
📈 PROJECT OUTCOME

By completing Data Transformer, students gain practical experience in converting raw database records into meaningful information.

Skills developed:
✅ Advanced SQL querying
✅ Relational data analysis
✅ Data transformation
✅ Business-oriented reporting
✅ Analytical SQL
✅ Database problem solving
🌟 WHY THIS PROJECT?

Raw Data → SQL Processing → Transformed Data → Business Insight

This project demonstrates how SQL can be used beyond basic SELECT statements to perform real-world data analysis and transformation.

👩‍💻 Author

Khevna Goyani

📌 Project Status

Completed — Academic SQL Project

"Transform the data. Discover the insight." 🚀
