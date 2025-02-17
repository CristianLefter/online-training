# Azure Cosmos DB Practice Exercises

This section provides hands-on exercises to help you practice working with **Azure Cosmos DB** using the **SQL API**. The exercises cover fundamental operations such as **creating databases and containers, inserting and querying items, and managing resources**.

---

## 1. Setting Up Azure Cosmos DB Environment

Before starting the exercises, ensure you have:

- **An Azure Cosmos DB account** with the SQL API.
- **Azure Portal** access or **Azure CLI** installed.
- **Azure Cosmos DB SDK** for your preferred programming language (e.g., Python, .NET, Java).

---

## 2. Creating a Database and Container

### **Exercise 1: Create a Database**

Create a new database named `SampleDB`.

**Using Azure Portal:**

1. Navigate to your Azure Cosmos DB account.
2. Click on **Data Explorer**.
3. Select **New Database** and enter `SampleDB` as the Database ID.
4. Click **OK** to create the database.

**Using Azure CLI:**

```bash
az cosmosdb sql database create \
    --account-name <your-account-name> \
    --resource-group <your-resource-group> \
    --name SampleDB
```

### **Exercise 2: Create a Container**

Within `SampleDB`, create a container named `ItemsContainer` with `/partitionKey` as the partition key.

**Using Azure Portal:**

1. In **Data Explorer**, expand `SampleDB`.
2. Click on **New Container**.
3. Enter `ItemsContainer` as the **Container ID**.
4. Set `/partitionKey` as the **Partition Key**.
5. Click **OK** to create the container.

```bash
az cosmosdb sql container create \
    --account-name <your-account-name> \
    --resource-group <your-resource-group> \
    --database-name SampleDB \
    --name ItemsContainer \
    --partition-key-path /partitionKey
```

## 3. Inserting and Querying Items

### **Exercise 3: Insert Items into the Container**

Insert a JSON document into `ItemsContainer`.

**Using Azure Portal:**

1. In **Data Explorer**, expand `ItemsContainer`.
2. Click on **Items** and then **New Item**.
3. Enter the following JSON:

    ```json
    {
        "id": "1",
        "name": "Sample Item",
        "description": "This is a sample item.",
        "partitionKey": "samplePartition"
    }
    ```

4. Click **Save** to insert the item.

**Using Azure SDK for Python:**

```python
from azure.cosmos import CosmosClient, PartitionKey

# Initialize the Cosmos client
client = CosmosClient("<your-account-uri>", "<your-account-key>")

# Create a database
database = client.create_database_if_not_exists(id="SampleDB")

# Create a container
container = database.create_container_if_not_exists(
    id="ItemsContainer",
    partition_key=PartitionKey(path="/partitionKey")
)

# Create an item
item = {
    "id": "1",
    "name": "Sample Item",
    "description": "This is a sample item.",
    "partitionKey": "samplePartition"
}

# Insert the item into the container
container.create_item(body=item)
```

## 3. Inserting and Querying Items

### **Exercise 4: Query Items from the Container**

Retrieve items where the `partitionKey` is `samplePartition`.

**Using Azure Portal:**

1. In **Data Explorer**, select **Items** under `ItemsContainer`.
2. Click on **New SQL Query** and enter:

    ```sql
    SELECT * FROM c WHERE c.partitionKey = 'samplePartition'
    ```

3. Click **Execute Query** to see the results.

**Using Azure SDK for Python:**

```python
from azure.cosmos import CosmosClient

# Initialize the Cosmos client
client = CosmosClient("<your-account-uri>", "<your-account-key>")

# Select the database and container
database = client.get_database_client("SampleDB")
container = database.get_container_client("ItemsContainer")

# Query the container
query = "SELECT * FROM c WHERE c.partitionKey = 'samplePartition'"
items = list(container.query_items(
    query=query,
    enable_cross_partition_query=True
))

for item in items:
    print(item)
```

## 4. Managing Resources

### **Exercise 5: Update an Item**

Update the `description` of the item with `id` 1.

**Using Azure SDK for Python:**

```python
from azure.cosmos import CosmosClient

# Initialize the Cosmos client
client = CosmosClient("<your-account-uri>", "<your-account-key>")

# Select the database and container
database = client.get_database_client("SampleDB")
container = database.get_container_client("ItemsContainer")

# Fetch the item
item = container.read_item(item="1", partition_key="samplePartition")

# Update the description
item["description"] = "This is an updated description."

# Replace the item in the container
container.replace_item(item=item, body=item)
```

### **Exercise 6: Delete an Item**

Delete the item with `id` 1.

**Using Azure SDK for Python:**

```python
from azure.cosmos import CosmosClient

# Initialize the Cosmos client
client = CosmosClient("<your-account-uri>", "<your-account-key>")

# Select the database and container
database = client.get_database_client("SampleDB")
container = database.get_container_client("ItemsContainer")

# Delete the item
container.delete_item(item="1", partition_key="samplePartition")
```
For more detailed instructions, refer to the official Azure documentation: [Azure Cosmos DB SQL API client library for Python](https://learn.microsoft.com/en-us/python/api/overview/azure/cosmos-readme?view=azure-python).

This documentation provides comprehensive guidance on using the Azure Cosmos DB SQL API client library for Python, including installation, authentication, and performing various database operations.



