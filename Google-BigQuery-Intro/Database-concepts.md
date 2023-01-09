# Database Concepts

Without delving deeply into the topic, we discussed the current context of data technologies.

Content:
- [Starting with WHY](Database-concepts.md#starting-with-why)
- [Databases Timeline](Database-concepts.md#databases-timeline)
- [What is SQL](Database-concepts.md#what-is-sql)
- [OLTP, OLAP and HTAP](Database-concepts.md#oltp-olap-and-htap)

## Starting with WHY

>*Motto*: Having a reason to learn about something is crucial to really learning it. 
>Knowing the topic's **"why"** can provide this meaning and make class more interesting and worthwhile.  
>The "why" of data is **competitive advantage** and a lot more.

It is commonly stated that **"every company is a data company"** due to the importance of data and analytics in the modern corporate world. This implies that companies of all sizes and types can benefit from collecting, storing, and analyzing data in order to make educated decisions and accomplish their objectives.

Several sorts of analytics can be used by businesses to acquire insights from their data:
- **Descriptive analytics**  
This type of analytics entails examining previously acquired data and summarizing it in a way that facilitates comprehension of what has occurred in the past. This could involve the creation of reports, charts, and graphs to illustrate trends and patterns.
- **Diagnostic analytics**  
This type of analytics entails delving deeper into the data to determine the underlying reasons of particular outcomes or events. This can assist organizations in identifying problems or improvement opportunities.  
- **Predictive analytics**  
Utilizing data and statistical models, this sort of analytics predicts future outcomes or occurrences. This can aid organizations in planning for the future and making decisions based on probabilities.
- **Prescriptive analytics**  
This type of analytics uses data and advanced analytics techniques to not only anticipate what may occur, but also to recommend actions that can be taken to attain a desired outcome.

### Instead of a conclusion (for this segment)
One of the most important reasons why businesses require databases is to store and manage the data utilized for these types of analytics. A database is a structured collection of electronically stored data that can be accessed, updated, and queried with relative ease. By keeping data in a database, businesses can analyze and acquire insights from their data more readily.

## Databases timeline

Here are the steps taken by modern databases from flat files to the present:

- The initial type of database, **flat files** consisted of a single table of data with no relationships to other tables. They were inefficient for storing and retrieving huge volumes of data because they lacked indexing and search capabilities.  
Some examples are CSV files, Excel spreadsheets, and text files.

- The next step in the evolution of databases was the development of **relational databases**. They were created in the 1970s and are based on the relational model, which organizes data into tables. Relational databases are more effective than flat files because they support indexing and searching and permit structured data queries.  
As examples for this category we have MySQL, Oracle, and Microsoft SQL Server.

- **NoSQL** databases were developed as an alternative to relational databases in the late 1990s and early 2000s. They are designed to manage vast quantities of unstructured data and can extend horizontally across several servers. NoSQL databases are built on a flexible, non-relational data model and are frequently employed for web-scale applications and big data analytics.  
In this category are included MongoDB, Cassandra, and Couchbase.

- **Big data technologies**: The term **"big data"** refers to the increasing volume, diversity, and velocity of data generated and collected by businesses. To manage and analyze enormous data, a number of big data technologies, such as Hadoop, Spark, and NoSQL databases, have been developed. These technologies enable enterprises to store and process vast quantities of data in a distributed and scalable manner.  
Hadoop, Spark, and Apache Flink are examples of the BigData technologies.


- **Cloud databases** are hosted and managed by a cloud service provider, such as Amazon Web Services (AWS), Microsoft Azure, or Google Cloud. The benefits of cloud databases include scalability, flexibility, and reduced maintenance expenses.  
A few popular cloud database solutions are Amazon DynamoDB, Microsoft Azure Cosmos DB, and Google Cloud Bigtable.

## What is SQL

SQL is similar to a recipe for database interaction. SQL instructs a database service on how to arrange and handle data, much like a recipe instructs on how to combine components for a delicious dish.

Imagine a database as a large filing cabinet, with each "drawer" representing a table of data and each "folder" representing a row in that table. SQL enables you to search through these drawers and folders, locate specific information, and even modify it.
A database can also be viewed as a collection of tables, with each table including rows and columns, with each row representing an entity (such as a client, an order, or a student) and each column reflecting the item's attributes (such as name, location, time).

For instance, SQL can be used to:
- Find all the consumers who reside in a particular city
- Count the amount of orders each customer has placed.
- Update the price of a product across all stores in a region.

## OLTP, OLAP and HTAP
