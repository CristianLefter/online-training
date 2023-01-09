# Google BigQuery - Introduction

This repository comprises the online textbook for the Google BigQuery - Introduction course.
## Google BigQuery overview

Google BigQuery is a fully-managed, cloud-based data warehouse solution that enables lightning-fast SQL queries against huge and complicated datasets by leveraging Google's infrastructure processing power. It is a serverless Platform as a Service (PaaS) that supports ANSI SQL querying and can manage structured and semistructured data.

BigQuery is built to manage high volume and high concurrency at petabyte scale, making it an excellent option for enterprises that need to process a vast deal of data. It allows users to utilize SQL to examine data saved in Google Cloud Storage, Google Drive, and Google Cloud Bigtable.

BigQuery enables users to construct tables and load data in a number of ways, including by uploading a file, importing data from Google Cloud Storage or Google Drive, streaming data in real-time, or utilizing the BigQuery API to insert data. Once data is in BigQuery, users may generate reports and dashboards using a range of visualization tools, such as Google Data Studio and Google Sheets, or link to business intelligence tools such as Looker and Tableau to do more complex analysis.

BigQuery has two SQL dialects: [Google Standard SQL and legacy SQL](https://cloud.google.com/bigquery/docs/reference/standard-sql/migrating-from-legacy-sql). Google Standard SQL is the preferred dialect (and the one used in this course). It supports [SQL:2011](https://www.iso.org/standard/53681.html) and includes extensions that support geospatial analysis or Machine Learning (ML).

## Course structure

This course is broken up into:

- [Database concepts](Database-concepts.md)
- [BigQuery for the first time](BigQuery-for-the-first-time.md)
- [Using SQL commands to select, filter, and sort data](Select-filter-sort-data.md)
- [Understanding data types in BigQuery (e.g., INTEGER, FLOAT, STRING, TIMESTAMP)](Understanding-data-types-in-bigquery.md)
- [Retrieve data from multiple tables (joins)](Joins.md)
- [Using Subqueries](Using-subqueries.md)
- [Aggregating data in BigQuery](Aggregating-data.md)
- [Using GROUP BY and HAVING clauses](Using-group-by.md) 
- [Using Window Functions](Using-window-functions.md)
- [Common Table Expressions (CTEs)](Ctes.md)

## Reference
For details we can use the following links:
- [Free GCP Trial](https://cloud.google.com/free)  
- [Get started with the BigQuery sandbox](https://cloud.google.com/bigquery/docs/sandbox) 
- [Setting up the BigQuery sandbox (video)](https://youtu.be/JLXLCv5nUCE)
- [Bigquery documentation](https://cloud.google.com/bigquery/docs)  
- [Google Standard SQL - Data Types](https://cloud.google.com/spanner/docs/reference/standard-sql/data-types)  
- [Google Standard SQL - Data Definition Language](https://cloud.google.com/spanner/docs/reference/standard-sql/data-definition-language)  
- [Google Standard SQL - JOIN operator](https://cloud.google.com/spanner/docs/reference/standard-sql/query-syntax#join_types)  
[Google Standard SQLstring_functions)  
 - [Query Syntax](https://cloud.google.com/spanner/docs/reference/standard-sql/query-syntax)  
[Google Standard SQL - String Functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/


## License

Except as otherwise noted, the solutions within this repository are provided under the
[Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license. Please see
the [LICENSE](/LICENSE) file for more detailed terms and conditions.

## Disclaimer

This repository and its contents are not an official Google Product.
