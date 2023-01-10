# Retrieve data from multiple tables (joins)

In Google BigQuery, a JOIN operation combines rows from two or more tables based on a related column between them. The resulting table contains only those rows that meet the join condition, and typically contains all columns from both tables.

Here are a few examples using the public datasets:
- **Inner join**: This type of join returns only those rows that have matching values in both tables. For example, to find the names and hire dates of all employees in the bigquery-public-data.samples.natality dataset who were born in the same year as someone in the bigquery-public-data.samples.github_timeline dataset, you could use the following query:

```sql
SELECT n.year, n.name, g.created_at
FROM `bigquery-public-data.samples.natality` AS n
JOIN `bigquery-public-data.samples.github_timeline` AS g
ON n.year = EXTRACT(YEAR FROM g.created_at)
``` 

- **Left join**: This type of join returns all rows from the left table, and any matching rows from the right table. If there is no match, NULL values are returned for right table's columns. For example, to find the names and hire dates of all employees in the bigquery-public-data.samples.natality dataset, along with the repository names and descriptions of any repositories they created in the bigquery-public-data.samples.github_timeline dataset, you could use the following query:

```sql
SELECT n.year, n.name, g.repo_name, g.description
FROM `bigquery-public-data.samples.natality` AS n
LEFT JOIN `bigquery-public-data.samples.github_timeline` AS g
ON n.name = g.actor
```

- **Right join**: This type of join is similar to a left join, but returns all rows from the right table, and any matching rows from the left table. If there is no match, NULL values are returned for left table's columns.

