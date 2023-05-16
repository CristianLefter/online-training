# Understanding Joins - SQL Denormalization and Normalization Case Study

In this case study, we illustrate the process of denormalizing and normalizing tables in SQL Server. We use a simple example of a table containing student names and the cities they came from.

## Denormalized Data

Initially, we have a denormalized table named "StudentCity". The table looks like this:

| StudentID | StudentName | CityName |
|-----------|-------------|----------|
| 1         | John        |  New York |
| 2         | Jane        |  London   |
| 3         | Bob         |  Paris    |
| 4         | Alice       |  New York |
| 5         | Steve       |  London   |

In this table, we have redundancy. For example, the cities 'New York' and 'London' are repeated.

## Normalized Data

We then normalize this data into two tables:

### Students

| StudentID | StudentName | CityID |
|-----------|-------------|--------|
| 1         | John        | 100    |
| 2         | Jane        | 200    |
| 3         | Bob         | 300    |
| 4         | Alice       | 100    |
| 5         | Steve       | 200    |

### Cities

| CityID | CityName |
|--------|----------|
| 100    | New York |
| 200    | London   |
| 300    | Paris    |

In the normalized tables, each city only appears once in the Cities table, and we've linked students to cities using the CityID field.

To get a list of students along with the names of the cities they came from, we need to JOIN these two tables together. The SQL command for this is:

```sql
SELECT Students.StudentName, Cities.CityName
FROM Students
INNER JOIN Cities ON Students.CityID = Cities.CityID;
