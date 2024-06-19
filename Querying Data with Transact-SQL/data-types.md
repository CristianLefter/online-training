# T-SQL Data Types Practice Exercises

## Exercise 1: Creating a Table

Create a table named `Employees` with the following columns:
- `EmployeeID` (INT, Primary Key)
- `FirstName` (VARCHAR(50))
- `LastName` (VARCHAR(50))
- `BirthDate` (DATE)
- `HireDate` (DATE)
- `Salary` (DECIMAL(10, 2))

## Exercise 2: Inserting Data

Insert the following data into the `Employees` table:
- EmployeeID: 1, FirstName: John, LastName: Doe, BirthDate: 1980-01-15, HireDate: 2010-05-23, Salary: 50000.00
- EmployeeID: 2, FirstName: Jane, LastName: Smith, BirthDate: 1985-07-30, HireDate: 2012-09-17, Salary: 60000.00

## Exercise 3: Querying Data

Write a query to select all employees who were hired after January 1, 2011.

## Exercise 4: Updating Data

Update the salary of the employee with EmployeeID 1 to 55000.00.

## Exercise 5: Deleting Data

Delete the employee with EmployeeID 2.

## Exercise 6: Using Different Data Types

Create a table named `Products` with the following columns:
- `ProductID` (INT, Primary Key)
- `ProductName` (VARCHAR(100))
- `Category` (VARCHAR(50))
- `Price` (DECIMAL(8, 2))
- `InStock` (BIT)

## Exercise 7: Inserting Data into Products

Insert the following data into the `Products` table:
- ProductID: 1, ProductName: Laptop, Category: Electronics, Price: 999.99, InStock: 1
- ProductID: 2, ProductName: Coffee Maker, Category: Appliances, Price: 79.99, InStock: 0

## Exercise 8: Querying with Conditions

Write a query to select all products that are in stock and belong to the 'Electronics' category.

## Exercise 9: Updating Data in Products

Update the price of the product with ProductID 2 to 69.99.


# Solutions

## Exercise 1: Creating a Table

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    BirthDate DATE,
    HireDate DATE,
    Salary DECIMAL(10, 2)
);
```
## Exercise 2: Inserting Data

```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, BirthDate, HireDate, Salary)
VALUES (1, 'John', 'Doe', '1980-01-15', '2010-05-23', 50000.00);

INSERT INTO Employees (EmployeeID, FirstName, LastName, BirthDate, HireDate, Salary)
VALUES (2, 'Jane', 'Smith', '1985-07-30', '2012-09-17', 60000.00);
```

## Exercise 3: Querying Data

```sql
SELECT * FROM Employees
WHERE HireDate > '2011-01-01';
```

## Exercise 4: Updating Data

```sql
UPDATE Employees
SET Salary = 55000.00
WHERE EmployeeID = 1;
```

## Exercise 5: Deleting Data
```sql
DELETE FROM Employees
WHERE EmployeeID = 2;
```

## Exercise 6: Using Different Data Types
```sql
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(100),
    Category VARCHAR(50),
    Price DECIMAL(8, 2),
    InStock BIT
);
```

## Exercise 7: Inserting Data into Products
```sql
INSERT INTO Products (ProductID, ProductName, Category, Price, InStock)
VALUES (1, 'Laptop', 'Electronics', 999.99, 1);

INSERT INTO Products (ProductID, ProductName, Category, Price, InStock)
VALUES (2, 'Coffee Maker', 'Appliances', 79.99, 0);
```

## Exercise 8: Querying with Conditions
```sql
SELECT * FROM Products
WHERE InStock = 1 AND Category = 'Electronics';
```

## Exercise 9: Updating Data in Products
```sql
UPDATE Products
SET Price = 69.99
WHERE ProductID = 2;
```

## Exercise 10: Deleting Data from Products
```sql
DELETE FROM Products
WHERE InStock = 0;
```

# Part II - Additional T-SQL Data Types Practice Exercises

## Exercise 11: Creating a Table with Various Data Types

Create a table named `Orders` with the following columns:
- `OrderID` (INT, Primary Key)
- `CustomerID` (INT)
- `OrderDate` (DATETIME)
- `TotalAmount` (DECIMAL(10, 2))
- `Status` (VARCHAR(20))

## Exercise 12: Inserting Data into Orders

Insert the following data into the `Orders` table:
- OrderID: 1, CustomerID: 101, OrderDate: 2023-05-10 14:30:00, TotalAmount: 250.75, Status: 'Shipped'
- OrderID: 2, CustomerID: 102, OrderDate: 2023-06-15 09:00:00, TotalAmount: 99.99, Status: 'Pending'

## Exercise 13: Querying Data with Date Range

Write a query to select all orders placed between June 1, 2023, and June 30, 2023.

## Exercise 14: Updating Order Status

Update the status of the order with OrderID 2 to 'Shipped'.

## Exercise 15: Deleting Orders

Delete all orders where the total amount is less than 100.00.

## Exercise 16: Creating a Table with NULL Values

Create a table named `Departments` with the following columns:
- `DepartmentID` (INT, Primary Key)
- `DepartmentName` (VARCHAR(50))
- `ManagerID` (INT, Nullable)

## Exercise 17: Inserting Data with NULL Values

Insert the following data into the `Departments` table:
- DepartmentID: 1, DepartmentName: 'HR', ManagerID: NULL
- DepartmentID: 2, DepartmentName: 'IT', ManagerID: 5

## Exercise 18: Querying Data with NULL Values

Write a query to select all departments where the `ManagerID` is NULL.

## Exercise 19: Using the UNIQUE Constraint

Create a table named `Categories` with the following columns:
- `CategoryID` (INT, Primary Key)
- `CategoryName` (VARCHAR(50), Unique)

## Exercise 20: Inserting Data into Categories

Insert the following data into the `Categories` table:
- CategoryID: 1, CategoryName: 'Electronics'
- CategoryID: 2, CategoryName: 'Appliances'
- CategoryID: 3, CategoryName: 'Electronics' (This should result in an error due to the UNIQUE constraint)


# Solutions to Additional T-SQL Data Types Practice Exercises

## Exercise 11: Creating a Table with Various Data Types

```sql
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    OrderDate DATETIME,
    TotalAmount DECIMAL(10, 2),
    Status VARCHAR(20)
);
```

## Exercise 12: Inserting Data into Orders

```sql
INSERT INTO Orders (OrderID, CustomerID, OrderDate, TotalAmount, Status)
VALUES (1, 101, '2023-05-10 14:30:00', 250.75, 'Shipped');

INSERT INTO Orders (OrderID, CustomerID, OrderDate, TotalAmount, Status)
VALUES (2, 102, '2023-06-15 09:00:00', 99.99, 'Pending');
```

## Exercise 13: Querying Data with Date Range
```sql
SELECT * FROM Orders
WHERE OrderDate BETWEEN '2023-06-01' AND '2023-06-30';
```

## Exercise 14: Updating Order Status
```sql
UPDATE Orders
SET Status = 'Shipped'
WHERE OrderID = 2;
```

## Exercise 15: Deleting Orders
```sql
DELETE FROM Orders
WHERE TotalAmount < 100.00;
```

## Exercise 16: Creating a Table with NULL Values
```sql
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50),
    ManagerID INT NULL
);
```

## Exercise 17: Inserting Data with NULL Values
```sql
INSERT INTO Departments (DepartmentID, DepartmentName, ManagerID)
VALUES (1, 'HR', NULL);

INSERT INTO Departments (DepartmentID, DepartmentName, ManagerID)
VALUES (2, 'IT', 5);
```

## Exercise 18: Querying Data with NULL Values
```sql
SELECT * FROM Departments
WHERE ManagerID IS NULL;
```

## Exercise 19: Using the UNIQUE Constraint
```sql
CREATE TABLE Categories (
    CategoryID INT PRIMARY KEY,
    CategoryName VARCHAR(50) UNIQUE
);

```

## Exercise 20: Inserting Data into Categories
```sql
INSERT INTO Categories (CategoryID, CategoryName)
VALUES (1, 'Electronics');

INSERT INTO Categories (CategoryID, CategoryName)
VALUES (2, 'Appliances');

-- This will result in an error due to the UNIQUE constraint
INSERT INTO Categories (CategoryID, CategoryName)
VALUES (3, 'Electronics');
```


