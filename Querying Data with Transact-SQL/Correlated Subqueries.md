## Correlated Subqueries in T-SQL: Practical Examples

### Introduction

Subqueries are a powerful feature in SQL that allows you to perform complex queries in a more readable and logically structured manner. 
Among the various types of subqueries, correlated subqueries stand out due to their ability to reference a column or columns in the outer query. 
This unique characteristic enables the execution of queries dynamically related to the rows processed by the outer query. 
This article will explore the practical applications of correlated subqueries in T-SQL through examples, using a simple table.

### Sample Table Setup

Before diving into the examples, let's set up a sample table named `employees`. This table will serve as the basis for our subsequent queries.

```sql
   drop table if exists employees;
     go
 create table employees (EmployeeID int
      , EmployeeName varchar(100)
	    , Salary decimal(10, 2)
	    , Department varchar(50));
     go
 insert into employees (EmployeeID, EmployeeName, Salary, Department) 
 values (1, 'John Doe', 50000, 'Engineering')
      , (2, 'Jane Smith', 60000, 'Engineering')
      , (3, 'Emily Davis', 55000, 'Design')
      , (4, 'Michael Brown', 65000, 'Design')
      , (5, 'Sarah Miller', 70000, 'Engineering')
      , (6, 'James Wilson', 58000, 'Marketing')
      , (7, 'Linda Garcia', 62000, 'Marketing')
      , (8, 'Robert Martinez', 48000, 'Design');
```
The final table looks like this:
| EmployeeID | EmployeeName | Salary | Department | 
|------------|------------|----------|--------------|
|1           | 'John Doe' | 50000    | 'Engineering'|
|2| 'Jane Smith'| 60000| 'Engineering'|
|3| 'Emily Davis'| 55000| 'Design'|
|4| 'Michael Brown'| 65000| 'Design'|
|5| 'Sarah Miller'| 70000| 'Engineering'|
|6| 'James Wilson'| 58000| 'Marketing'|
|7| 'Linda Garcia'| 62000| 'Marketing'|
|8| 'Robert Martinez'| 48000| 'Design'|


```sql
-- correlated subquery
 select EmployeeID
      , EmployeeName
   from employees emp
  where Salary > (
        select avg(Salary)
          from employees
         where Department = emp.Department);

-- correlated subquery
 select EmployeeName
      , Salary
	  , Department
      , (select avg(Salary) 
           from employees
          where Department = emp.Department) as DepartmentAverage
   from employees emp
  order by Department
```
Examples using TSQL sample database.

```sql

-- Change database context
USE TSQL;
GO

-- Find the product ID with the highest total quantity sold
SELECT TOP 1 productid, totalqty
FROM (
    SELECT productid, SUM(qty) AS totalqty
    FROM Sales.OrderDetails 
    GROUP BY productid
) AS dt
ORDER BY totalqty DESC;

-- List product names along with their total quantities sold
SELECT dt2.productname, dt1.totalqty
FROM (
    SELECT productid, SUM(qty) AS totalqty
    FROM Sales.OrderDetails 
    GROUP BY productid
) AS dt1
JOIN (
    SELECT productid, productname
    FROM Production.Products
) AS dt2
ON dt1.productid = dt2.productid;

-- Another way to select the product names along with their total quantities sold
SELECT p.productname, dt1.totalqty
FROM (
    SELECT productid, SUM(qty) AS totalqty
    FROM Sales.OrderDetails 
    GROUP BY productid
) dt1
JOIN Production.Products p
ON dt1.productid = p.productid;

-- Select product names along with their minimum and maximum prices, but only for products with different min and max prices
SELECT productname, minprice, maxprice
FROM (
    SELECT productid, MIN(unitprice) AS minprice, MAX(unitprice) AS maxprice
    FROM Sales.OrderDetails 
    GROUP BY productid 
) AS dt
JOIN Production.Products p
ON dt.productid = p.productid
WHERE dt.minprice <> dt.maxprice;

-- Find products that have been sold at more than one distinct price
SELECT productid, COUNT(DISTINCT unitprice) AS nmbprices
FROM Sales.OrderDetails 
GROUP BY productid
HAVING COUNT(DISTINCT unitprice) > 1;

-- Select company names of customers who have made at least 10 orders
SELECT c.companyname, COUNT(o.orderid) AS NmbOrders
FROM Sales.Customers c
JOIN Sales.Orders o
ON c.custid = o.custid
GROUP BY c.custid
HAVING COUNT(o.orderid) >= 10;

-- Another way to select company names of customers who have made at least 10 orders
SELECT c.companyname, nmborders
FROM (
    SELECT custid, COUNT(orderid) AS nmborders
    FROM Sales.Orders 	
    GROUP BY custid
    HAVING COUNT(orderid) >= 10
) AS dt
JOIN Sales.Customers c
ON dt.custid = c.custid;

-- Yet another way to select company names of customers who have made at least 10 orders
SELECT c.companyname, nmborders
FROM (
    SELECT custid, COUNT(orderid) AS nmborders
    FROM Sales.Orders 	
    GROUP BY custid	
) dt
JOIN Sales.Customers c
ON dt.custid = c.custid
WHERE nmborders >= 10;

```


### Exercise 01: Retrieve All Orders for Individual Customers

**Objective**: Retrieve all orders and their corresponding customer names, specifically for individuals.

**Database**: AdventureWorks2012

**Requirements**:
- Retrieve only the rows where the `PersonType` column in the `Person.Person` table has the value 'IN' (Individual consumers).
- Include the following columns in your results:
  - `FirstName`, `MiddleName`, `LastName` from the `Person.Person` table.
  - `OrderDate`, `TotalDue` from the `Sales.SalesOrderHeader` table.

**Hints**: 
- You need to use the `Sales.Customer` table.
- Not always foreign key columns have the same name as the referred column.

**Sample output**:

| FirstName | MiddleName | LastName | PersonType | OrderDate                  | TotalDue    |
|-----------|------------|----------|------------|----------------------------|-------------|
| Takiko    | J.         | Collins  | SC         | 2011-05-31 00:00:00.000    | 1457.3288   |
| Jauna     | E.         | Elson    | SC         | 2011-05-31 00:00:00.000    | 36865.8012  |
| ...       | ...        | ...      | ...        | ...                        | ...         |

``` (31465 rows affected) ```

### Exercise 02: Retrieve the product names and corresponding categories

**Objective**: Retrieve the product names and corresponding categories from the Products table and the ProductCategory table.

**Database**: AdventureWorks2012

**Requirements**:
- Include the following columns in your results:
  - `Name` (use alias `ProductName`) from the `Production.Product` table.
  - `Name` (use alias `CategoryName`) from the `Production.ProductCategory` table.

**Hints**: 
- You need to use the `ProductSubcategory` table.

**Sample output**:

| ProductName                 | CategoryName |
|-----------------------------|--------------|
| HL Road Frame - Black, 58   | Components   |
| HL Road Frame - Red, 58     | Components   |
| ...                         | ...          |

``` (295 rows affected) ```

### Exercise 03: Retrieve a specific product

**Objective**: Retrieve a specific product using its location

**Database**: AdventureWorks2012

**Requirements**:
- Retrieve the product name for the product stored in `Subassembly` location, Shelf `W` and Bin `9`.
- Include the following columns in your results:
  - `Name` (use alias `ProductName`) from the `Production.Product` table.
  - `Quantity` from the `Production.ProductInventory` table.

**Hints**: 
- You need to use the `Production.Location` table.
- You need a `WHERE` clause.

**Output**:

| ProductName	   | Quantity |
|------------------|----------|
|HL Mountain Pedal |	153   |

``` (1 row affected) ```


## Answers 

### Exercise 01: Retrieve All Orders for Individual Customers

```sql
select p.FirstName
     , p.MiddleName
     , p.LastName
     , p.PersonType
     , soh.OrderDate
     , soh.TotalDue
  from Sales.SalesOrderHeader soh
  join Sales.Customer c
	  on soh.CustomerID = c.CustomerID
  join Person.Person p
    on p.BusinessEntityID = c.PersonID
 where p.PersonType = 'IN'
```

### Exercise 02: Retrieve the product names and corresponding categories

```sql
select p.Name as ProductName
     , pc.Name as CategoryName
  from Production.Product p 
  join Production.ProductSubcategory ps
    on p.ProductSubcategoryID = ps.ProductSubcategoryID
  join Production.ProductCategory pc 
	on ps.ProductCategoryID = pc.ProductCategoryID;
```
### Exercise 03: Retrieve a specific product

```sql
select p.[Name] as ProductName
     , pv.Quantity
  from Production.Product p
  join Production.ProductInventory pv
    on p.ProductID = pv.ProductID
  join Production.[Location] l
    on pv.LocationID = l.LocationID
 where l.[Name] = 'Subassembly'
   and pv.Shelf = 'W'	
   and pv.Bin = 9 
```
