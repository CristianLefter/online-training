# Transact-SQL Introduction Recap

In today's lesson, we've covered the basics of Transact-SQL (T-SQL), focusing on Data Definition Language (DDL) and Data Manipulation Language (DML) operations. Here's a summary of what we learned:

## DDL (Data Definition Language)
- **CREATE**: Used to create a new table or database.
- **ALTER**: Used to modify an existing database object, such as a table.
- **DROP**: Used to delete an existing table or database.

## DML (Data Manipulation Language)
- **SELECT**: Retrieves data from a database.
- **INSERT**: Inserts new data into a database.
- **UPDATE**: Updates existing data within a database.
- **DELETE**: Deletes data from a database.

### Key Concepts
- **Primary Key**: A column or a combination of columns that uniquely identifies a row in a table.

### Example Code

#### Creating a Database and Table
```sql
CREATE DATABASE demodb;
GO
USE demodb;
GO

CREATE TABLE person(
    personid INT PRIMARY KEY NOT NULL,
    firstname VARCHAR(60) NOT NULL,
    lastname VARCHAR(60) NOT NULL,
    age TINYINT NULL
);
```
Inserting Data
```sql
INSERT INTO person(personid, firstname, lastname) VALUES(1, 'Nico', 'Smith');
INSERT INTO person(personid, firstname, lastname) VALUES(2, 'John', 'Jones');
```

Selecting Data

```sql
SELECT * FROM person;
SELECT firstname, lastname FROM dbo.person;
```

Updating Data

```sql
UPDATE person SET age = 30;
UPDATE person SET age = 25 WHERE personid = 1;
UPDATE person SET firstname = 'Carmen-Nico' WHERE personid = 1;
```

Deleting Data

```sql
DELETE FROM person WHERE personid = 3;
```

Exercises
Retrieve All Customers

```sql
USE adventureworks;
GO
SELECT * FROM SalesLT.Customer;
```

List All Products (only Name, ListPrice columns)

```sql
SELECT Name, ListPrice FROM SalesLT.Product;
```

Find Customers in a Specific Region (e.g., "California")

```sql
SELECT FirstName, LastName
FROM SalesLT.Customer 
WHERE Title = 'Mr.';
```

Additional SELECT Techniques
Using DISTINCT to select unique values.
Using TOP to limit the results.
Filtering results with WHERE.
Pattern matching with LIKE.
Pattern Matching Examples

```sql
SELECT * FROM SalesLT.Product WHERE Name LIKE '%l';
SELECT * FROM SalesLT.Product WHERE Color LIKE '_lue';
SELECT * FROM SalesLT.Customer WHERE FirstName LIKE 'J____';
SELECT * FROM SalesLT.Customer WHERE FirstName LIKE '[A-F]%';
```

Phone Number Pattern Matching

```sql
SELECT FirstName, LastName, Phone FROM SalesLT.Customer
WHERE Phone LIKE '[0-9][0-9][0-9]-[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]';
```

