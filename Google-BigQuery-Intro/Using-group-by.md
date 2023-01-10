# Using GROUP BY and HAVING clauses
The GROUP BY clause is used in a SELECT statement to group rows into subsets that have the same values in one or more columns. The aggregate functions, such as COUNT, SUM, AVG, MIN, and MAX, can then be applied to each group to produce summary information.

The HAVING clause is used in combination with the GROUP BY clause to filter the groups based on a condition. It is similar to the WHERE clause, but it is applied to the groups after they have been created, rather than to the individual rows.

Here's an example of how you can use the GROUP BY and HAVING clauses in a query:

```sql
SELECT year, state, COUNT(*) as num_births
FROM `bigquery-public-data.samples.natality`
GROUP BY year, state
HAVING COUNT(*) > 100
ORDER BY year, num_births DESC;
```

This query groups the rows in the "bigquery-public-data.samples.natality" table by year and state and counts the number of births in each group. The HAVING clause is used to filter the groups so that only those with more than 100 births are included in the result. The query then orders the results by year and the number of births in each group, in descending order.

You can notice that the group by is applied on the columns year and state so it will produce groups based on the different values of these columns.

Another example:

```sql
SELECT mother_age, COUNT(*) as num_births, AVG(weight_pounds) as avg_weight
FROM `bigquery-public-data.samples.natality`
GROUP BY mother_age
HAVING num_births > 1000
ORDER BY mother_age;
```

This query groups the rows in the "bigquery-public-data.samples.natality" table by mother_age, then it count the number of births for each group and calculates the average weight for the babies in the group. The HAVING clause filters the group of mothers that gave birth for more than 1000 births.

Note that the having clause can only be used with aggregate function, thus you can use it to filter on the output of any aggregate function not like a normal filter using the WHERE statement.
