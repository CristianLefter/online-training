# **02 - Types of Data**

## **📘 Overview**
Data can be classified into three main categories: **Structured, Semi-Structured, and Unstructured Data**. Each type has specific characteristics, storage formats, and use cases.

---

## **1. Structured, Semi-Structured, and Unstructured Data**

### **a) Structured Data**
- Data that follows a **fixed schema** (rows & columns).
- Easily stored in **relational databases (SQL-based systems).**
- Optimized for querying and data integrity.

#### **Examples:**
- Customer records in an **Azure SQL Database**.
- Inventory data in **MySQL or PostgreSQL**.
- Financial transactions in an **ERP system**.

#### **Use Cases:**
✅ Business applications with structured queries.  
✅ Data analysis in **Azure Synapse Analytics**.  
✅ CRM and ERP systems requiring relational integrity.  

---

### **b) Semi-Structured Data**
- Does not follow a strict schema but has some structure.
- Uses flexible formats such as **JSON, XML, and YAML**.
- Ideal for web applications, APIs, and NoSQL databases.

#### **Examples:**
- JSON files used in **REST APIs**.
- XML-based **configuration files**.
- Sensor data stored in **Azure Cosmos DB**.

#### **Use Cases:**
✅ **Web applications** and dynamic content storage.  
✅ **IoT data storage** in NoSQL solutions like **Cosmos DB**.  
✅ Flexible schema requirements in cloud-native applications.  

---

### **c) Unstructured Data**
- Data that has **no predefined schema or format**.
- Typically **binary or free text data**.
- Requires specialized storage solutions like **Azure Blob Storage**.

#### **Examples:**
- Images, videos, and audio files.
- Social media posts and customer reviews.
- Emails, logs, and PDF documents.

#### **Use Cases:**
✅ Media streaming platforms (video/audio storage).  
✅ Storing and analyzing **big data** in **Azure Data Lake**.  
✅ Processing logs and text analytics using **Azure Cognitive Services**.  

---

## **2. Common Data Formats & Differences**

| Format  | Type | Characteristics | Use Cases |
|---------|------|----------------|-----------|
| **JSON**  | Semi-Structured | Human-readable, text-based, flexible schema | APIs, NoSQL databases, web applications |
| **Parquet** | Structured (Columnar) | Optimized for analytics, high compression, efficient query performance | Big Data, data lakes, analytics workloads |
| **ORC** | Structured (Columnar) | Similar to Parquet but optimized for Hive, efficient compression | Hadoop ecosystem, Big Data processing |
| **Avro** | Semi-Structured (Row-Based) | Binary format, schema evolution support, compact | Streaming data, event-driven architectures, data serialization |

---

## **3. Choosing the Right Format**

| Use Case | Best Format |
|----------|------------|
| API Communication, Config Files | JSON |
| Large-scale Analytics, Data Lakes | Parquet or ORC |
| Data Warehousing in Hadoop | ORC |
| Streaming, Schema Evolution | Avro |

---

## **🔗 Next Steps**
📌 Learn about **Relational Data in Azure** in the next module.  
📌 Explore **Azure Data Storage solutions** for handling different data formats.  

🚀 Keep Learning & Exploring! 😊
