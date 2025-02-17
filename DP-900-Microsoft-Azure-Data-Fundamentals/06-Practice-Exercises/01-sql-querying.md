# SQL Querying Practice Exercises

This section contains hands-on exercises to help you practice SQL querying skills in **Azure SQL Database** and **Azure Synapse Analytics**. The exercises cover fundamental concepts such as **SELECT queries, filtering, aggregation, joins, and subqueries**.

---

## 1. Getting Started with Azure SQL Database
Before starting the exercises, ensure you have:
- **An Azure SQL Database instance** (or an Azure Synapse SQL pool).
- **SQL Server Management Studio (SSMS)**, Azure Data Studio, or the **Azure Query Editor**.
- **A sample database** such as `AdventureWorks` or `WideWorldImporters`.

To create a sample database:

```sql
CREATE DATABASE SampleDB;
```

To use the database:

```sql
USE SampleDB;
```

---

## 2. Basic SELECT Queries
### **Exercise 1: Retrieve All Data from a Table**
Retrieve all columns and rows from a table.

```sql
SELECT * FROM Sales.Customers;
```
- Modify the query to select specific columns instead of `*`.

### **Exercise 2: Filtering Data**
Retrieve all customers from the `USA`.

```sql
SELECT * FROM Sales.Customers WHERE Country = 'USA';
```
- Modify the query to filter by another country.

---

## 3. Sorting and Aggregation
### **Exercise 3: Sorting Data**
Retrieve products sorted by price in descending order.

```sql
SELECT ProductName, Price FROM Sales.Products ORDER BY Price DESC;
```

### **Exercise 4: Aggregating Data**
Find the total number of orders placed.

```sql
SELECT COUNT(*) AS TotalOrders FROM Sales.Orders;
```

Find the average product price.

```sql
SELECT AVG(Price) AS AveragePrice FROM Sales.Products;
```

---

## 4. Using Joins
### **Exercise 5: INNER JOIN**
Retrieve orders with customer names.

```sql
SELECT O.OrderID, C.CustomerName, O.OrderDate
FROM Sales.Orders O
INNER JOIN Sales.Customers C
  ON O.CustomerID = C.CustomerID;
```
- Modify the query to display product details for each order.

### **Exercise 6: LEFT JOIN**
Retrieve all customers, including those who haven't placed an order.

```sql
SELECT C.CustomerName, O.OrderID
FROM Sales.Customers C
LEFT JOIN Sales.Orders O
  ON C.CustomerID = O.CustomerID;
```

---

## 5. Using Subqueries
### **Exercise 7: Subquery to Find Top Customers**
Retrieve customers who placed more than **5 orders**.

```sql
SELECT CustomerID, CustomerName 
FROM Sales.Customers
WHERE CustomerID IN (
      SELECT CustomerID FROM Sales.Orders
      GROUP BY CustomerID
      HAVING COUNT(OrderID) > 5
);
```

---

## 6. Common Table Expressions (CTEs)
### **Exercise 8: Using CTEs**
Retrieve the top 3 most expensive products.

```sql
WITH TopProducts AS (
  SELECT ProductName, Price,
  RANK() OVER (ORDER BY Price DESC) AS Rank
  FROM Sales.Products
  )
SELECT * FROM TopProducts WHERE Rank <= 3;
```

---

## 7. Advanced Queries
### **Exercise 9: Window Functions**
Retrieve the total number of orders per customer, including a running total.

```sql
SELECT CustomerID, COUNT(OrderID) AS TotalOrders,
SUM(COUNT(OrderID)) OVER (ORDER BY CustomerID) AS RunningTotal
FROM Sales.Orders
GROUP BY CustomerID;
```

### **Exercise 10: Pivot Tables**
Display total sales per product in a pivoted format.

```sql
SELECT * FROM (
   SELECT ProductName, OrderDate, SalesAmount
   FROM Sales.Orders
  ) AS SourceTable
PIVOT (
      SUM(SalesAmount) FOR OrderDate IN ([2023-01-01], [2023-02-01], [2023-03-01])
   ) AS PivotTable;
```
- Modify the dates based on your dataset.

---

## 8. SQL Query Optimization
### **Exercise 11: Using Indexes**
Check if an index exists and create one if necessary.

```sql
SELECT * FROM sys.indexes WHERE object_id = OBJECT_ID('Sales.Orders');
```
Create an index on the `OrderDate` column.

```sql
CREATE INDEX IDX_OrderDate ON Sales.Orders(OrderDate);
```

### **Exercise 12: Analyzing Execution Plans**
Use the execution plan to analyze query performance.

```sql
SET SHOWPLAN_XML ON;
SELECT * FROM Sales.Orders WHERE OrderDate > '2023-01-01';
SET SHOWPLAN_XML OFF;
```

---

## Summary
These exercises cover **basic querying, filtering, aggregation, joins, subqueries, CTEs, window functions, pivot tables, and optimization techniques**. Practicing these concepts in **Azure SQL Database** and **Azure Synapse Analytics** will strengthen your understanding of **SQL for data analysis and management**.
