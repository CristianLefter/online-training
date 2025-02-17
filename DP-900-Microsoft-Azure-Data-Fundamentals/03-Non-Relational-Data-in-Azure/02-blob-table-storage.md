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

### **Key Concepts in Azure Blob Storage**
#### **a) Storage Accounts**
- Blob Storage is part of an **Azure Storage Account**.
- **Storage Account Types:**
  - **General-purpose v2 (GPv2)** – Recommended for most scenarios.
  - **Premium Block Blob Storage** – High-performance storage for latency-sensitive applications.

#### **b) Containers**
- Containers **organize blobs** within a storage account.
- A **storage account can have multiple containers**, each storing **multiple blobs**.
- **Access Control:**
  - **Private** (default, requires authentication)
  - **Blob (Public Read Access)** (only blobs are public)
  - **Container (Full Public Read Access)** (entire container is public)

#### **c) Blob Types & Use Cases**
| Blob Type | Description | Best Use Case |
|-----------|------------|--------------|
| **Block Blob** | Stores data in blocks, optimized for large files | Video streaming, backups, media storage |
| **Append Blob** | Optimized for appending operations, cannot modify existing data | Logging, telemetry, auditing |
| **Page Blob** | Used for virtual hard disks (VHDs), supports random read/write | Virtual machine disks, databases |

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

## **7. Best Practices for Azure Storage**
### **a) Security & Access Control**
- **Use Managed Identities & Azure AD** for authentication.
- **Enable Private Endpoints** to restrict storage access.
- **Implement Role-Based Access Control (RBAC)** for least-privilege access.

### **b) Performance Optimization**
- **Use Content Delivery Network (CDN)** for faster access to blobs.
- **Enable Soft Delete** to recover accidentally deleted blobs.
- **Use Asynchronous Uploads** for large files.
- **Optimize Block Sizes** to improve throughput.

### **c) Cost Optimization**
- **Use Lifecycle Management** to automatically move data between tiers.
- **Monitor Storage Metrics** to track usage patterns.
- **Enable Compression & Deduplication** to save storage space.

### **d) Backup & Disaster Recovery**
- **Enable Blob Versioning** to track changes and restore previous versions.
- **Use Geo-Redundant Storage (GRS)** for disaster recovery.
- **Set up Cross-Region Replication** for high availability.

---

## **8. Summary**
| Feature | Description |
|---------|------------|
| **Blob Types** | Block Blob (files, media), Page Blob (VM disks), Append Blob (logs). |
| **Storage Tiers** | Hot (frequent use), Cool (infrequent use), Archive (rarely used). |
| **Security** | Use **RBAC, Private Endpoints, Azure AD** for access control. |
| **Performance** | Use **CDN, Soft Delete, Lifecycle Policies** to optimize cost. |
| **Use Cases** | Static website hosting, backup & archiving, big data analytics, IoT, ML. |

---

## **🔗 Next Steps**
📌 Learn about **security best practices for Azure Storage**.  
📌 Explore **Blob Lifecycle Management** for automated cost savings.  
📌 Implement **Azure Data Lake for scalable big data processing**.  

🚀 Keep Learning & Exploring! 😊
