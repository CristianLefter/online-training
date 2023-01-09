# Using SQL commands to select, filter, and sort data

The **SELECT** statement is used in Google BigQuery to retrieve data from a table or a view in a dataset. It is one of the most commonly used SQL statements and is used to retrieve a specific subset of data from one or more tables.

The general syntax for a SELECT statement in BigQuery standard SQL is as follows:

```sql
SELECT [list of fields or expressions]
FROM [source]
WHERE [conditions]
GROUP BY [field or expression]
HAVING [conditions]
ORDER BY [field or expression] [ASC|DESC]
LIMIT [number of rows to return]
```

Here is a breakdown of each part of the SELECT statement:
- **SELECT** *[list of fields or expressions]*: This specifies the list of fields or expressions that you want to retrieve. You can use the * character to select all fields.
- **FROM** *[source]*: This specifies the source table or view that you want to retrieve data from.
- **WHERE** *[conditions]*: This specifies any conditions that must be met for a row to be included in the result set.
- **GROUP BY** *[field or expression]*: This specifies a field or expression that you want to group the results by.
- **HAVING** *[conditions]*: This specifies any conditions that must be met for a group to be included in the result set.
- **ORDER BY** *[field or expression]* [**ASC**|**DESC**]: This specifies a field or expression that you want to use to order the results. You can specify ASC for ascending order or DESC for descending order.
- **LIMIT** *[number of rows to return]*: This specifies the maximum number of rows to return in the result set.


