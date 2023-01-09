# Using SQL commands to select, filter, and sort data

The **SELECT** statement is used in Google BigQuery to retrieve data from a table or a view in a dataset. It is one of the most commonly used SQL statements and is used to retrieve a specific subset of data from one or more tables.

Content
- [General Syntax](Select-filter-sort-data.md#general-syntax)

## General Sytax

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
```
  Using * is considered an anti-pattern!
```
- **FROM** *[source]*: This specifies the source table or view that you want to retrieve data from.
- **WHERE** *[conditions]*: This specifies any conditions that must be met for a row to be included in the result set.
- **GROUP BY** *[field or expression]*: This specifies a field or expression that you want to group the results by.
- **HAVING** *[conditions]*: This specifies any conditions that must be met for a group to be included in the result set.
- **ORDER BY** *[field or expression]* [**ASC**|**DESC**]: This specifies a field or expression that you want to use to order the results. You can specify ASC for ascending order or DESC for descending order.
- **LIMIT** *[number of rows to return]*: This specifies the maximum number of rows to return in the result set.

An example that is using a public dataset:
```sql
SELECT name, COUNT(*) as nmbofnames
FROM `bigquery-public-data.usa_names.usa_1910_2013`
WHERE gender = 'F' AND year > 1950
GROUP BY name
HAVING COUNT(*) > 10
ORDER BY nmbofnames DESC
LIMIT 1000
```

This SELECT statement would retrieve all fields from the **usa_1910_2013** table in the **usa_names** dataset in the **bigquery-public-data project**, where the gender is **'F'** and the year is greater than **1950**, grouped by **name**, having a count of more than **10**, ordered by **count** in descending order, and limited to **1,000** rows.

This SELECT statement would return a list of names that were popular for females in the **USA** from **1950** onwards, where the name was used at least **10** times. The names would be ordered by the number of times they were used, with the most popular names appearing first.

The minimal SELECT statement if the following:
```sql 
SELECT 1 as colname;
``` 
In this statement the keyword **as** allows us to set the name for the resulted column **colname**.

