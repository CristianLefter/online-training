# Aggregating data in BigQuery
We occasionally require data summaries. For example, we may need to know the total number of rows in a table, the average value for a specific table column, and other information. We can obtain those using aggregate functions.

Some examples of aggregate functions that we can use in Google BigQuery:

- COUNT: This function counts the number of rows in a table or column. For example, you can use the following query to count the number of rows in the "bigquery-public-data.samples.natality" table:
- 
```sql
SELECT COUNT(*) FROM `bigquery-public-data.samples.natality`
```

- SUM: This function adds up the values of a column. For example, you can use the following query to find the total weight of all the babies born in the "bigquery-public-data.samples.natality" table:
```sql
SELECT SUM(weight_pounds) FROM `bigquery-public-data.samples.natality`
```

- AVG: This function calculates the average of the values in a column. For example, you can use the following query to find the average weight of all the babies born in the "bigquery-public-data.samples.natality" table:

```sql
SELECT AVG(weight_pounds) FROM `bigquery-public-data.samples.natality`
```

- MIN: This function finds the minimum value in a column. For example, you can use the following query to find the lowest weight of a baby born in the "bigquery-public-data.samples.natality" table:

```sql
SELECT MIN(weight_pounds) FROM `bigquery-public-data.samples.natality`
```
- MAX: This function finds the maximum value in a column. For example, you can use the following query to find the highest weight of a baby born in the "bigquery-public-data.samples.natality" table:

```sql
SELECT MAX(weight_pounds) FROM `bigquery-public-data.samples.natality`
```
