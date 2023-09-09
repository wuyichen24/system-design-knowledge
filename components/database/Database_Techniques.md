# Database Techniques

- [**Replication**](#replication)
- [**Partitioning**](#partitioning)
- [**Denormalization (Materialized View)**](#denormalization-materialized-view)

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
   - Functional partitioning (Federation): Split data into multiple databases by function (table).
- **Pros**
   - Less read and write traffic to a single database/shard.
   - If one database/shard is down, other databases/shards will be still operational.
   - More writes in parallel to increase throughput.
- **Cons and solutions**
   | Cons | Solution |
   |----|----|
   | Join operation is complex. | De-normalize the database so that queries can be performed in a single table (See [Denormalization](#denormalization-materialized-view)) |
   | Rebalance is complex. | |
   | Introduce hot spots (celebrity problem). | Allocate a partition for each celebrity. Each partition might even require further partition. |
- **Sharding**
   - Strategies
     | | By key range | By hash of key |
     |---|---|---|
     | Example | ![ddia_0602](https://user-images.githubusercontent.com/8989447/116647540-09a4f380-a938-11eb-9621-eeeff91e442c.png) | ![ddia_0603](https://user-images.githubusercontent.com/8989447/116647659-525cac80-a938-11eb-847f-c44bfec9f68a.png) |
     | Concept | Assign a range of keys to each partition. | Assign a range of hashes to each partition. |
     | Pros | <ul><li>Range queries are easy.</ul> | <ul><li>Keys distributing is fair among the partitions.</ul> |
     | Cons | <ul><li>Certain access patterns can lead to hot spots (A partition with disproportionately high load).</ul> | <ul><li>Lose the ability to do efficient range queries.</ul> |
   - Directory based sharding
      - Concepts
         - Place a lookup service in front of the sharded databases.
            - The lookup service knows the current partitioning scheme.
            - The lookup service keeps a map of each entity and which database shard it is stored on.
         - When we need to query the database, query the lookup service first to figure out which shard has the data we want.
      - Pros
         - Loose coupling: Any partitioning scheme changes will encapsulated and will not impact on the application.
   
           ![dss](https://user-images.githubusercontent.com/8989447/117697354-9d1fc500-b17f-11eb-895d-4164124c4b01.png)

## Denormalization (Materialized View)
   
   ![materialized-view-pattern-diagram](https://user-images.githubusercontent.com/8989447/154134405-95c792a7-ce84-4b8b-94a9-6dbdf145fb44.png)
   
- **Concept**
   - Add redundant copies of data or by grouping data to improve the read performance of a database
- **Pros**
   - Improve read performance.
- **Cons**
   - Degrade write performance.
   - Increase complexity of database design.
   - Data is duplicated.