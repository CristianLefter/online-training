# **02 - Azure Blob & Table Storage**

## **📘 Overview**
Azure Storage provides **highly scalable, secure, and durable storage** for different data types. It includes **Blob Storage, File Storage, Table Storage, and Data Lake Storage**, each suited for specific workloads.

---

## **1. Azure Storage Account**
An **Azure Storage Account** is the foundation of Azure Storage, allowing users to store and manage multiple types of data efficiently.

### **Types of Azure Storage:**
- **Azure Blob Storage** – Object storage for unstructured data.
- **Azure File Storage** – Fully managed file shares in the cloud.
- **Azure Table Storage** – NoSQL key-value store for semi-structured data.
- **Azure Data Lake Storage** – Optimized for big data analytics.

---

## **2. Azure Blob Storage**
Azure Blob Storage is an **object storage solution** for large amounts of unstructured data, such as text, images, and video files.

### **Blob Types & Use Cases**
| Blob Type | Description | Best Use Case |
|-----------|------------|--------------|
| **Block Blob** | Stores data in blocks, optimized for large files | Video streaming, backups, media storage |
| **Append Blob** | Optimized for appending operations, cannot modify existing data | Logging, telemetry, auditing |
| **Page Blob** | Used for virtual hard disks (VHDs), supports random read/write | Virtual machine disks, databases |


### 1. Block Blob

#### **Characteristics:**
- **Optimized for:** Storing large files like images, videos, documents, and backups.
- **Data Structure:** Data is stored in **blocks** (up to **100 MB** per block).
- **Maximum Blob Size:** **Up to 5 TiB** (each block blob can have **50,000 blocks**).
- **Upload Method:** Data is uploaded in chunks (blocks), and commits can be done in parallel.
- **Performance:** Great for **high-throughput streaming and large-scale ingestion**.

#### **Use Cases:**
✅ **Media Storage:** Storing images, videos, and audio files (e.g., website assets, streaming content).  
✅ **Backup & Archive:** Storing backups from applications and databases.  
✅ **Big Data & AI:** Storing training datasets for ML models.  
✅ **Static Website Hosting:** Can serve as a web server to host static HTML, CSS, and JavaScript files.  

---

### 2. Page Blob

#### **Characteristics:**
- **Optimized for:** Random read/write operations (frequent updates).
- **Data Structure:** Data is stored in **pages** (512-byte units).
- **Maximum Blob Size:** **Up to 8 TiB**.
- **Upload Method:** Efficient for partial updates; pages can be modified individually.
- **Performance:** Low-latency read/write, making it ideal for **disk-like** workloads.

#### **Use Cases:**
✅ **Virtual Hard Disks (VHDs) for Azure VMs:** Stores Azure VM OS and data disks (managed/unmanaged).  
✅ **Database Storage:** Used for NoSQL databases or database transaction logs.  
✅ **Persistent Storage for Cloud Applications:** Ideal for workloads needing fast, random access.  

---

### 3. Append Blob

#### **Characteristics:**
- **Optimized for:** Log writing and sequential data append operations.
- **Data Structure:** Composed of blocks but **only supports append operations** (existing data cannot be modified).
- **Maximum Blob Size:** **Up to 5 TiB** (same as Block Blob).
- **Upload Method:** Data is always appended at the end.
- **Performance:** Designed for scenarios where **new data is continuously added**.

#### **Use Cases:**
✅ **Logging & Auditing:** Writing logs from applications, services, or IoT devices.  
✅ **Event Streaming Data:** Capturing sensor data, telemetry, or real-time events.  
✅ **Financial Transactions & Audits:** Recording sequential events for compliance.  
✅ **Chat or Messaging Systems:** Storing sequential chat history without modifying previous entries.  

---

### Comparison Table

| Blob Type   | Max Size | Structure | Best For | Modifiable Data? |
|------------|---------|-----------|----------|------------------|
| **Block Blob** | 5 TiB | Blocks (100MB each) | Large file storage, media, backups, websites | Yes (replaces blocks) |
| **Page Blob**  | 8 TiB | Pages (512 bytes) | Azure VM disks, databases | Yes (random access updates) |
| **Append Blob** | 5 TiB | Blocks (append-only) | Logging, event data, transaction history | No (only appends new data) |

---

### **Final Thoughts**
- **Choose Block Blob** for general-purpose file storage.
- **Use Page Blob** when you need random read/write access (like virtual disks or databases).
- **Go with Append Blob** when logging or appending new data in a sequential manner.

---

### **Containers in Blob Storage**
- Blobs are stored in **containers**, which organize and manage related blobs.
- **Access control** can be set at the container level (private, public, or restricted access).

✅ **Best for media storage, backups, and web content hosting**.

---

## **3. Azure File Storage**
Azure File Storage provides **fully managed SMB & NFS file shares** in the cloud.

### **Key Features:**
- Supports **Server Message Block (SMB) & NFS** protocols.
- Can be **mounted on Windows, Linux, and macOS**.
- Integration with **Azure File Sync** for hybrid file storage.

✅ **Best for shared storage, lift-and-shift file migration, and application file shares**.

---

## **4. Azure Table Storage**
Azure Table Storage is a **NoSQL key-value store**, optimized for fast lookups and large-scale semi-structured data storage.

### **Key Features:**
- **Massive scalability**, supporting millions of records.
- **Schema-less design**, allowing flexible data modeling.
- **Fast query performance** with partitioned indexing.

### **Use Cases:**
✅ IoT telemetry and logging.  
✅ Storing user profile metadata.  
✅ Persisting application configuration settings.  

---

## **5. Azure Data Lake Storage**
Azure Data Lake Storage is optimized for **big data analytics** and is built on top of **Azure Blob Storage**.

### **Key Features:**
- **Hierarchical namespace** for file system-like management.
- Supports **Hadoop-compatible APIs** for analytics workloads.
- Provides **enterprise-grade security & access control**.

### **Use Cases:**
✅ Big data processing with **Azure Synapse Analytics**.  
✅ AI/ML model training datasets.  
✅ Large-scale log and telemetry storage.  

---

## **6. Choosing the Right Azure Storage Solution**
| Storage Type | Best Use Case |
|-------------|--------------|
| **Blob Storage** | Large-scale unstructured data (media, backups, logs) |
| **File Storage** | Shared file systems for applications and users |
| **Table Storage** | High-speed NoSQL key-value data storage |
| **Data Lake Storage** | Advanced analytics and big data workloads |

---


## **🔗 Next Steps**
📌 Learn about **security best practices for Azure Storage**.  
📌 Explore **Blob Lifecycle Management** for automated cost savings.  
📌 Implement **Azure Data Lake for scalable big data processing**.  

🚀 Keep Learning & Exploring! 😊
