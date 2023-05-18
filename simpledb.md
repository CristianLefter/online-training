## Practice joins with a simple database
```sql
USE master;
GO
DROP DATABASE IF EXISTS simpledb;
GO
CREATE DATABASE simpledb;
GO
USE simpledb;
GO

-- Create Customers table
CREATE TABLE Customers (
  CustomerID int PRIMARY KEY NOT NULL,
  CustomerName varchar(255) NOT NULL,
  ContactName varchar(255) NULL,
  Country varchar(50) NULL,
  City varchar(50) NULL,
  PostalCode varchar(10) NULL
);

-- Insert some data into Customers
INSERT INTO Customers (CustomerID, CustomerName, ContactName, Country, City, PostalCode)
VALUES 
(1, 'Brilliant Books', 'Harold Finch', 'USA', 'New York', '10001'),
(2, 'Omnivore Orchards', 'Aria Stark', 'USA', 'Los Angeles', '90001'),
(3, 'Cosmic Confectioneries', 'Donna Noble', 'Canada', 'Toronto', 'M1B 1B5');

-- Create Orders table
CREATE TABLE Orders (
  OrderID int PRIMARY KEY NOT NULL,
  CustomerID int REFERENCES Customers(CustomerID) NOT NULL,
  OrderDate date NOT NULL
);

-- Insert some data into Orders
INSERT INTO Orders (OrderID, CustomerID, OrderDate)
VALUES 
(101, 1, '2023-01-01'),
(102, 2, '2023-02-01'),
(103, 3, '2023-03-01');

-- Create OrderDetails table
CREATE TABLE OrderDetails (
  OrderDetailID int PRIMARY KEY NOT NULL,
  OrderID int REFERENCES Orders(OrderID) NOT NULL,
  Product varchar(50) NOT NULL,
  Quantity int NOT NULL
);

-- Insert some data into OrderDetails
INSERT INTO OrderDetails (OrderDetailID, OrderID, Product, Quantity)
VALUES 
(1, 101, 'Novel - The Great Escape', 100),
(2, 102, 'Organic Apples', 500),
(3, 103, 'Chocolate Bonbons', 300),
(4, 101, 'Historical Fiction - The Last Queen', 75),
(5, 102, 'Organic Peaches', 250);

```
