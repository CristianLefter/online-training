# **01 - Data Fundamentals**

## **📘 Overview**
Understanding **data fundamentals** is the first step in learning about **data processing, storage, and management** in Azure. This section provides insights into **types of data, structured vs. unstructured data, and key data concepts.**

---

## **1. What is Data?**
Data refers to **raw facts and figures** that can be processed to generate meaningful information. It can be classified into different types based on its structure and usage.

### **Types of Data:**
- **Structured Data:** Organized in a predefined schema (e.g., relational databases like SQL Server, MySQL).
- **Semi-Structured Data:** Has some structure but does not fit into a relational database (e.g., JSON, XML, CSV).
- **Unstructured Data:** No fixed schema or structure (e.g., images, videos, PDFs, social media posts).

### **Data Formats:**
| Format          | Description                             | Example |
|----------------|-----------------------------------------|---------|
| JSON          | Lightweight, human-readable format      | `{ "name": "John", "age": 30 }` |
| XML           | Data stored in a hierarchical structure | `<person><name>John</name></person>` |
| CSV           | Comma-separated values                  | `John,30,Developer` |
| Parquet/ORC   | Optimized for analytics workloads      | Used in Big Data processing |

---

## **2. Structured vs. Unstructured Data**
### **Key Differences:**
| Feature            | Structured Data           | Unstructured Data       |
|--------------------|--------------------------|-------------------------|
| **Schema**        | Predefined schema         | No fixed schema         |
| **Storage**       | Stored in tables          | Stored as files, blobs  |
| **Querying**      | SQL-based queries         | Needs specialized tools |
| **Examples**      | SQL databases             | Images, videos, logs    |

### **Use Cases:**
- **Structured Data:** Business transactions, customer records, inventory management.
- **Unstructured Data:** Video streaming, medical imaging, IoT sensor logs.

---

## **3. Key Data Concepts**
### **a) Data Processing**
- **Batch Processing:** Large amounts of data processed at once (e.g., ETL pipelines in Azure Data Factory).
- **Stream Processing:** Continuous, real-time data processing (e.g., Azure Stream Analytics for IoT data).

### **b) Data Storage**
- **Databases:** SQL (relational) and NoSQL (document, key-value stores).
- **Data Lakes:** Centralized storage for structured & unstructured data.
- **Data Warehouses:** Optimized for analytics and reporting.

### **c) Data Lifecycle**
1. **Ingestion** – Collecting data from sources.
2. **Storage** – Storing in a structured/unstructured format.
3. **Processing** – Transforming and analyzing data.
4. **Visualization** – Using BI tools like Power BI for insights.

---

## **4. Importance of Data in Business & AI**
- **Decision Making:** Data-driven insights improve business strategies.
- **Machine Learning & AI:** Models rely on high-quality, structured data.
- **Compliance & Security:** Proper governance ensures data privacy and regulatory adherence.

---

## **🔗 Next Steps**
📌 Learn about **Relational Data in Azure** in the next module.  
📌 Explore **Azure Storage Services** for handling structured & unstructured data.  

🚀 Keep Learning & Exploring! 😊
