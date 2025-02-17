# Azure Synapse Analytics Practice Exercises

This section contains hands-on exercises to help you practice using **Azure Synapse Analytics** for data querying, transformation, and processing. These exercises cover **Synapse SQL, data ingestion, and Spark-based processing**.

---

## 1. Getting Started with Azure Synapse Analytics

Before starting the exercises, ensure you have:

- **An Azure Synapse Analytics workspace**.
- **Access to Synapse Studio** for running queries and managing resources.
- **A dedicated SQL pool** or **serverless SQL pool** for querying.
- **A sample dataset** such as `NYC Taxi Data` or `AdventureWorks`.

### **Connect to Your Synapse SQL Pool**

To connect to your Synapse SQL pool using T-SQL:

```sql
SELECT * FROM sys.tables;
```

---

## 2. Querying Data in Synapse SQL

### **Exercise 1: Query a Table**

Retrieve all records from a table in your Synapse SQL pool.

```sql
SELECT * FROM dbo.TripData;
```

- Modify the query to select only specific columns.

### **Exercise 2: Filtering Data**

Retrieve only the trips where the passenger count is greater than 2.

```sql
SELECT * FROM dbo.TripData WHERE PassengerCount > 2;
```

### **Exercise 3: Aggregating Data**

Find the average fare amount for all taxi trips.

```sql
SELECT AVG(FareAmount) AS AverageFare FROM dbo.TripData;
```

### **Exercise 4: Using Joins**

Join the `TripData` table with the `TaxiZones` table to get zone names.

```sql
SELECT t.TripID, t.PickupZoneID, z.ZoneName
FROM dbo.TripData t
JOIN dbo.TaxiZones z ON t.PickupZoneID = z.ZoneID;
```

---

## 3. Data Ingestion in Synapse

### **Exercise 5: Loading Data into Synapse SQL Pool**

Load a CSV file from Azure Data Lake Storage into Synapse.

```sql
COPY INTO dbo.TripData
FROM 'https://yourstorageaccount.dfs.core.windows.net/files/tripdata.csv'
WITH (
    FILE_TYPE = 'CSV',
    FIRSTROW = 2,
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n'
);
```

- Modify the query to load a different dataset.

### **Exercise 6: Creating an External Table**

Query data from an external file stored in Azure Data Lake without importing it into Synapse.

```sql
CREATE EXTERNAL TABLE dbo.ExternalTripData (
    TripID INT,
    FareAmount FLOAT,
    PassengerCount INT
)
WITH (
    LOCATION = 'tripdata.csv',
    DATA_SOURCE = my_external_data_source,
    FILE_FORMAT = my_csv_format
);
```

- Modify the table definition as needed.

---

## 4. Working with Apache Spark in Synapse

### **Exercise 7: Creating a Spark DataFrame**

Create a Spark DataFrame and display its content.

```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("SynapseExample").getOrCreate()
df = spark.read.csv("abfss://container@yourstorage.dfs.core.windows.net/tripdata.csv", header=True, inferSchema=True)
df.show()
```

### **Exercise 8: Performing Data Transformations**

Filter and aggregate data using PySpark.

```python
filtered_df = df.filter(df.PassengerCount > 2)
avg_fare = filtered_df.groupBy().avg("FareAmount")
avg_fare.show()
```

---

## 5. Performance Optimization in Synapse SQL

### **Exercise 9: Creating Indexes**

Improve query performance by creating an index on the `TripData` table.

```sql
CREATE INDEX idx_TripData_FareAmount ON dbo.TripData (FareAmount);
```

### **Exercise 10: Partitioning Tables**

Partition the `TripData` table to improve query efficiency.

```sql
CREATE TABLE dbo.PartitionedTripData
WITH (DISTRIBUTION = HASH(TripID))
AS SELECT * FROM dbo.TripData;
```

---

## Summary

These exercises cover **data querying, ingestion, transformation, and performance optimization** in **Azure Synapse Analytics**. Practicing these will help you build expertise in handling large-scale data processing using **Synapse SQL and Apache Spark**.

