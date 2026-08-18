---
link:
  - "[[DynamoDB]]"
---
Think of a DynamoDB table like a massive, highly organized **digital filing cabinet system**.

Because DynamoDB handles massive amounts of data, it can't just put everything in one giant pile. It splits your data across multiple physical storage servers, which are called **partitions**.

Here is how the different keys work to keep that filing cabinet organized:

### 1. Partition Key (The "Cabinet Number")

The Partition Key is the most important attribute. DynamoDB feeds this key's value into an internal hash function to determine the exact physical storage server (partition) where the data will live.

- **What it does:** It tells DynamoDB _where_ to go look.
- **The Goal:** You want a **high-cardinality** attribute (a fancy way of saying a property with tons of unique values, like a `User_ID`, `Order_ID`, or `Device_UUID`).
- **Why it matters:** If you use something with low-cardinality (like `Status` which might only be _Active_ or _Inactive_), millions of rows get crammed onto the exact same physical server. This causes a **"hot partition"** (uneven workload), slowing your database to a crawl.
    

### 2. Sort Key (The "Alphabetical Folder")

The Sort Key is optional. If you use one, DynamoDB takes all the items that landed in the same partition and sorts them in order by this key.

- **What it does:** It groups related data together so you can search through it efficiently using operators like "begins with," "greater than," or "between."
- **Example:** If your Partition Key is `User_ID`, your Sort Key could be `Timestamp`. This allows you to easily fetch a specific user's history and say, _"Show me all transactions for User X from the last 30 days."_

### 3. Primary Key (The "Unique Identifier")

In DynamoDB, the **Primary Key** is simply the unbending rule that uniquely identifies an item. No two items in a table can have the exact same Primary Key.

DynamoDB gives you two ways to design a Primary Key:

| **Primary Key Type**      | **Structure**                    | **How uniqueness is determined**                                                                                                                                                                                                                                                           |
| ------------------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Simple Primary Key**    | **Partition Key** only           | The Partition Key value _must_ be completely unique for every single row (e.g., a table where `User_ID` is the only key, so a user can only have one row).                                                                                                                                 |
| **Composite Primary Key** | **Partition Key** + **Sort Key** | The combination of both keys must be unique. You can have the _same_ Partition Key multiple times, as long as the Sort Key is different (e.g., `User_123` with `Timestamp_01` and `User_123` with `Timestamp_02`). It is suggested for improved performance and to prevent 'hot partition' |
