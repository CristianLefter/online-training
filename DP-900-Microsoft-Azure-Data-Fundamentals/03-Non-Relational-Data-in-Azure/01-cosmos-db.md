# **01 - Azure Cosmos DB**

## **📘 Overview**
Azure Cosmos DB is a globally distributed, **multi-model NoSQL database** designed for **low-latency, high availability, and scalability**. It supports **multiple APIs**, allowing seamless integration with various data models and query languages.

---

## **1. Multi-Model & Multiple APIs**
Azure Cosmos DB provides **multiple APIs** to support different database paradigms:

| API | Description | Best Use Case |
|-----|------------|--------------|
| **Core (SQL) API** | Supports SQL-like queries on JSON data | Web & mobile apps, telemetry |
| **MongoDB API** | Compatible with MongoDB queries & tools | Migrating MongoDB workloads |
| **Cassandra API** | Supports Cassandra Query Language (CQL) | Big Data & distributed applications |
| **Gremlin API** | Graph database for relationships & networks | Social media, fraud detection |
| **Table API** | Key-value store similar to Azure Table Storage | IoT, logs, metadata storage |

---

## **2. Global Distribution & Low Latency**
Azure Cosmos DB is **designed for global distribution**, automatically replicating data across multiple Azure regions. This ensures:
- **Low-latency reads & writes** (sub-10ms response times).
- **High availability** with **99.999% SLA**.
- **Multi-region writes** for seamless scalability.

### **Key Features:**
✅ **Turnkey Global Distribution** – Scale databases across multiple regions effortlessly.  
✅ **Multi-Region Writes** – Improves write performance & resilience.  
✅ **Low Latency** – Ideal for real-time applications (IoT, financial transactions).  

---

## **3. Consistency Models**
Azure Cosmos DB provides **five tunable consistency levels**, allowing users to balance **performance and consistency**:

| Consistency Level | Guarantees | Best Use Case |
|------------------|------------|--------------|
| **Strong** | Strict consistency, always latest data | Financial transactions |
| **Bounded Staleness** | Reads within a defined lag | Leaderboards, real-time apps |
| **Session** | Guarantees consistency for a user session | Shopping carts, user profiles |
| **Consistent Prefix** | No out-of-order reads, but eventual consistency | Chat apps, IoT data |
| **Eventual** | High availability, minimal consistency | Social media feeds, logs |

---

## **4. Migration Options**
Migrating to Azure Cosmos DB is streamlined using **native tools and APIs**:
- **Azure Database Migration Service (DMS)** for MongoDB, Cassandra.
- **Bulk Executor Library** for high-volume data ingestion.
- **Change Feed** for real-time migration synchronization.

✅ **Seamless integration** with on-prem & cloud NoSQL databases.  
✅ **Schema-free design** allows flexible migrations without schema modifications.  

---

## **5. Key Benefits & Use Cases**
### **Benefits:**
- **Fully Managed & Serverless** – No infrastructure management.
- **Elastic Scaling** – Automatically scales reads & writes.
- **Security & Compliance** – Role-based access control (RBAC), encryption.

### **Use Cases:**
| Use Case | Cosmos DB Advantage |
|----------|------------------|
| IoT & Telemetry | High-speed writes, real-time processing |
| E-commerce | Multi-region availability for global users |
| Social Networks | Graph API for friend connections & feeds |
| AI & Machine Learning | Fast queries & low-latency predictions |

---

## **🔗 Next Steps**
📌 Explore **querying Cosmos DB with SQL API**.  
📌 Learn about **partitioning & indexing for performance optimization**.  
📌 Experiment with **multi-region replication settings**.  

🚀 Keep Learning & Exploring! 😊
