## Inner Joins in T-SQL: Practical Exercises on AdventureWorks2012

### Exercise 01: Retrieve All Orders for Individual Customers

**Objective**: Retrieve all orders and their corresponding customer names, specifically for individuals.

**Database**: AdventureWorks2012

**Requirements**:
- Retrieve only the rows where the `PersonType` column in the `Person.Person` table has the value 'IN' (Individual consumers).
- Include the following columns in your results:
  - `FirstName`, `MiddleName`, `LastName` from the `Person.Person` table.
  - `OrderDate`, `TotalDue` from the `Sales.SalesOrderHeader` table.

**Hints**: 
- You need to use the `Sales.Customer` table

**Sample output**:

| ProductName                 | CategoryName |
|-----------------------------|--------------|
| HL Road Frame - Black, 58   | Components   |
| HL Road Frame - Red, 58     | Components   |


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
```




