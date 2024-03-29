# Using SQL commands to select, filter, and sort data

The **SELECT** statement is used in Google BigQuery to retrieve data from a table or a view in a dataset. It is one of the most commonly used SQL statements and is used to retrieve a specific subset of data from one or more tables.

Content
- [General Syntax](Select-filter-sort-data.md#general-syntax)
- [Filter Data](Select-filter-sort-data.md#filter-data)
- [Sort Data](Select-filter-sort-data.md#sort-data)

## General Syntax

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

## Filter Data

One way of filtering data is using the WHERE clause. The WHERE clause in a SELECT statement in BigQuery standard SQL is used to filter the rows in the result set based on specific criteria. Only rows that meet the specified conditions will be included in the final result set.

The **WHERE** clause has the following syntax:
```sql
WHERE condition
``` 
The **condition** can be any expression that returns a Boolean value (true or false). If the condition evaluates to true, the row will be included in the result set.

We can use the following operators in the WHERE clause:

- **=**: equal to
- **<>**: not equal to
- **>**: greater than
- **<**: less than
- **>=**: greater than or equal to
- **<=**: less than or equal to
- **IN**: in a list of values
- **BETWEEN**: between two values

You can also use logical operators (**AND**, **OR**, **NOT**) to combine multiple conditions.

Here are some examples of using the WHERE clause with the Google Analytics public dataset in BigQuery:

```sql
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE _TABLE_SUFFIX BETWEEN '20170701' AND '20170731'
```
This SELECT statement would retrieve all fields from the tables in the **ga_sessions_***  wildcard table in the **google_analytics_sample** dataset in the **bigquery-public-data** project, where the table suffix is between **'20170701'** and **'20170731'**. This would return data for the month of **July 2017**.



```sql
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE device.deviceCategory = 'desktop'
```

This SELECT statement would retrieve all fields from the tables in the **ga_sessions_*** wildcard table in the **google_analytics_sample**  dataset in the **bigquery-public-data** project, where the device category is **'desktop'**. This would return data for sessions from desktop devices.

```sql
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE trafficSource.source IN ('google', 'bing', 'yahoo')
```

This SELECT statement would retrieve all fields from the tables in the **ga_sessions_*** wildcard table in the **google_analytics_sample** dataset in the **bigquery-public-data** project, where the traffic source is either **'google'**, **'bing'**, or **'yahoo'**. This would return data for sessions from these search engines.

## Sort Data
Sorting results can be done using the **ORDER BY** clause.

The ORDER BY clause specifies a column or expression as the result set's sort criterion. The order of a query's results is not defined if an ORDER BY clause is not present. Column aliases from the FROM clause or the SELECT list are permitted. Aliases in the SELECT clause of a query take precedence over names in the corresponding FROM clause.  
The expression's data type must be orderable (all data types except ARRAY, STRUCT, GEOGRAPHY and JSON).

Some examples of using the ORDER BY clause with the Google Analytics sample dataset in BigQuery are:

- Sort the results of the ga_sessions_* table by the date column in ascending order:
```SQL
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
ORDER BY date ASC
```
- Sort the results of the ga_sessions_* table by the deviceCategory column in descending order, for rows where the totals.visits is greater than 1:
```SQL
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE totals.visits > 1
ORDER BY deviceCategory DESC
```
- Sort the results of the ga_sessions_* table by the totals.bounces column in ascending order, and then by the totals.hits column in descending order, and return the first 10 rows of the sorted results:
```SQL
SELECT *
FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
ORDER BY totals.bounces ASC, totals.hits DESC
LIMIT 10
```



