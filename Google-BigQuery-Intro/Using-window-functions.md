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

Here's an example of how you can use a window function to calculate the running total of pageviews for each day in the Google Analytics public dataset:

```sql
WITH data AS (
  SELECT date, pageviews
  FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  WHERE _TABLE_SUFFIX BETWEEN '20160801' AND '20160831'
)
SELECT date, pageviews, SUM(pageviews) OVER (ORDER BY date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) as running_total
FROM data
ORDER BY date;
```

This query first selects the date and pageviews columns from the Google Analytics public dataset for the month of August 2016, then it calculates the running total of pageviews by using the SUM function over the sorted rows. the ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW Defines the window frame as all rows from the first row to the current one.

Another example:

```sql
WITH data AS (
  SELECT date, country, channelGrouping, SUM(totals.pageviews) as pageviews
  FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  WHERE _TABLE_SUFFIX BETWEEN '20160801' AND '20160831'
  GROUP BY date, country, channelGrouping
)
SELECT date, country, channelGrouping, pageviews, 
  RANK() OVER (PARTITION BY country ORDER BY pageviews DESC) as rank
FROM data
ORDER BY date, country, rank;
```

This query first group the data by date, country, and channelGrouping and sums up the pageviews, then it calculates the rank of each group based on the pageviews by using the RANK function over the ordered partitions by country.

There are many other window functions available in BigQuery, like ROW_NUMBER, LEAD, LAG, and more. These functions allow you to perform a wide range of calculations and analyses on your data, such as calculating running totals, finding the maximum value in a sliding window of rows, and more.
