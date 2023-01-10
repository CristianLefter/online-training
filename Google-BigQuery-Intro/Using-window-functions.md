# Using Window Functions

**WINDOW** functions (or analytical functions) are another type of aggregate function in BigQuery that allows you to perform calculations on a set of rows that are related to the current row. The set of rows is defined by a window frame, which can be based on the values in one or more columns of the table.

The general form of a window function is as follows:

```sql
SELECT col1, col2, aggregate_function(col3) OVER (PARTITION BY col4 ORDER BY col5 ROWS/RANGE BETWEEN ... AND ...) as result
FROM mytable
```

In the above query:
- aggregate_function is an aggregate function, such as SUM, AVG, COUNT, MIN or MAX.
- OVER keyword is used to define the window function.
- PARTITION BY is used to divide the rows of the table into groups, or partitions, based on the values in one or more columns. The aggregate function is applied to each partition separately.
- ORDER BY is used to order the rows within each partition.
- ROWS/RANGE BETWEEN is used to define the window frame, which is the set of rows that the function operates on.
