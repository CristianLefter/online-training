# Common Table Expressions (CTEs)
A common table expression (CTE) is a named, temporary result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement. CTEs are similar to derived tables or subqueries, but they are defined separately from the main query and can be used multiple times.

Here are some examples using the Google Analytics public dataset:

- Calculate the total sessions for each day in the month of January 2021:

```sql
WITH daily_sessions AS (
  SELECT
    DATE_TRUNC(DATE(date), DAY) AS day,
    SUM(totals.sessions) AS sessions
  FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions`
  WHERE
    date BETWEEN '2021-01-01' AND '2021-01-31'
  GROUP BY
    day
)
SELECT *
FROM daily_sessions
ORDER BY day ASC
```

- Calculate the total page views and unique page views for each page:

```sql
WITH page_data AS (
  SELECT
    page.pagePath,
    SUM(totals.pageviews) AS pageviews,
    SUM(totals.uniquePageviews) AS unique_pageviews
  FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions`,
    UNNEST(hits) as hits
  GROUP BY
    page.pagePath
)

SELECT *
FROM page_data
ORDER BY unique_pageviews DESC
LIMIT 10
```

- Calculate the total sessions and session duration by device category:
```sql
WITH device_data AS (
  SELECT
    device.deviceCategory,
    SUM(totals.sessions) AS sessions,
    SUM(totals.timeOnSite) AS session_duration
  FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions`
  GROUP BY
    device.deviceCategory
)

SELECT *
FROM device_data
```
