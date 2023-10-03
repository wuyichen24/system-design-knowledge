# Database Techniques

- [**Replication**](#replication)
- [**Partitioning**](#partitioning)

## Replication
| | Master-slave | Master-master |
|---|---|---|
| Architecture | ![C9ioGtn](https://user-images.githubusercontent.com/8989447/116644854-b334b680-a931-11eb-9ff5-60f57652b09d.png) | ![krAHLGg](https://user-images.githubusercontent.com/8989447/116644889-cc3d6780-a931-11eb-956d-c6eebf2f218f.png) |
| Alias | Single-leader | Multi-leader |
| Write operations | Master only  | Masters |
| Read operations | Master and slaves | Masters |
| Failure handling | <li>If the master is down, one of the slave will be promoted to be a new master. | <li>If one master is down, other masters can still handle reads and writes. |

## Partitioning
- **Types**
   - Horizontal partitioning (Sharding): Split data by row.
   - Vertical partitioning: Split data by column.
   - Functional partitioning (Federation): Split data into multiple databases by business boundary.
- **Pros**
   - Less read and write traffic to a single database/shard.
   - If one database/shard is down, other databases/shards will be still operational.
   - More writes in parallel to increase throughput.
- **Cons and solutions**
   | Cons | Solution |
   |----|----|
   | Join operation is complex. | Denormalize the database so that queries can be performed in a single table (See [Denormalization](Database_Design.md#denormalization-materialized-view)) |
   | Rebalance is complex. | |
   | Introduce hot spots (celebrity problem). | Allocate a partition for each celebrity. Each partition might even require further partition. |
- **When to use**
   - *When to split data into multiple databases* (分库)
      - When the concurrency is high (because number of database connections is limited).
      - When the data needs to be archived (create a new database for storing archived data).
   - *When to split data into multiple tables* (分表)
      - When the data size is huge.

## Sharding
### Strategies
#### By mod of key
- **Concept**
   - Use the mod of key to decide which partition to store the data.
- **Example**
   - If we want to separate data into 128 tables, we just get the mod of the key. If the mod of a key is 2, so store the record into the `table_002`.

#### By key range
- **Concept**
   - Assign a range of keys to each partition.
- **Pros**
   - Range queries are easy.
- **Cons**
   - Certain access patterns can lead to hot spots (A partition with disproportionately high load).
           
![ddia_0602](https://user-images.githubusercontent.com/8989447/116647540-09a4f380-a938-11eb-9621-eeeff91e442c.png)
        
#### By hash of key
- **Concept**
   - Assign a range of hashes to each partition.
- **Pros**
   - Keys distributing is fair among the partitions.
- **Cons**
   - Lose the ability to do efficient range queries.

![ddia_0603](https://user-images.githubusercontent.com/8989447/116647659-525cac80-a938-11eb-847f-c44bfec9f68a.png)

#### By consistent hashing
- **Concept**
   - Consistent hashing is a distributed hashing scheme that operates independently of the number of servers or objects in a distributed hash table by assigning them a position on an abstract circle, or hash ring.
- **Pros**
   - When adding or removing servers, the number of keys that need to be relocated is minimized.
![conhash](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/ff7c85d1-3d84-43fd-8a3d-ea93c0c0094f)

#### Directory based sharding
- **Concepts**
    - Place a lookup service in front of the sharded databases.
       - The lookup service knows the current partitioning scheme.
       - The lookup service keeps a map of each entity and which database shard it is stored on.
     - When we need to query the database, query the lookup service first to figure out which shard has the data we want.
- **Pros**
    - Loose coupling: Any partitioning scheme changes will encapsulated and will not impact on the application.
   
![dss](https://user-images.githubusercontent.com/8989447/117697354-9d1fc500-b17f-11eb-895d-4164124c4b01.png)
  
### How to query after sharding**
- **Query on the sharding key**
   - Use the sharding key to locate the certain shard (table) easily.
- **Query on the non-sharding columns**
   - Solution 1: Add the non-sharding column as part of the sharding key.
      - Example: For the `order` table, the sharding key is `orderID`. But if we frequently query the `order` table by `userID`, we could add `userID` as part of the sharding key. So the final sharding key will be `orderID + userID`.
   - Solution 2: Double-write (write the same data into 2 different shards): One shard can be queried by some non-sharding columns, another shard can be queried by some other non-sharding columns.
      - Example: For the `order` table, the sharding key of one shard is "orderID + userID" (this can be queried by `orderID` and `userID`), the sharding key of another shard is "sellerID" (this can be queried by `sellerID`)
   - Solution 3: No sharding, create a better index with better hardward resources.
