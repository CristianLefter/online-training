# Using subqueries

In Google BigQuery, a subquery is a SELECT statement that is nested within another SELECT, INSERT, UPDATE, DELETE, or SET statement. The inner SELECT statement (i.e., the subquery) executes first and returns a result that is used by the outer statement.

Here are a few examples using the public google_analytics_sample dataset:

- Subquery in the SELECT clause: This type of subquery is used to return data as part of the main query's result set. For example, to find the average number of sessions per user for each country, you could use the following query:
```sql
SELECT country, AVG(sessions) as avg_sessions_per_user
FROM (
  SELECT country, COUNT(DISTINCT fullVisitorId) as sessions
  FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  GROUP BY country
)
GROUP BY country
```
- Subquery in the FROM clause: This type of subquery is used to replace a table in the FROM clause of a SELECT, INSERT, UPDATE, or DELETE statement. For example, to find the number of sessions and users for each country, you could use the following query:
```sql
SELECT country, sessions, users
FROM (
  SELECT country, COUNT(DISTINCT fullVisitorId) as sessions, COUNT(DISTINCT userId) as users
  FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  GROUP BY country
)
```
- Subquery in the WHERE clause: This type of subquery is used to filter rows based on the result of the inner SELECT statement. For example, to find the number of sessions and users for each country where the number of sessions is greater than the average number of sessions per user, you could use the following query:
```sql
SELECT country, sessions, users
FROM (
  SELECT country, COUNT(DISTINCT fullVisitorId) as sessions, COUNT(DISTINCT userId) as users
  FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  GROUP BY country
)
WHERE sessions > (
  SELECT AVG(sessions)
  FROM (
    SELECT COUNT(DISTINCT fullVisitorId) as sessions
    FROM `bigquery-public-data.google_analytics_sample.ga_sessions_*`
    GROUP BY country
  )
)
```
