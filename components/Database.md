# Database (DB)

- [**Types**](#types)
   - [Overview](#overview)
   - [Details of main types](#details-of-main-types)
      - [Relational databases](#relational-databases)
      - [NoSQL databases](#nosql-databases)
      - [NewSQL databases](#newsql-databases)
      - [Time-series databases](#time-series-databases)
   - [Comparisons](#comparisons)
- [**Selection**](#selection)
   - [Factors](#factors)
      - [Scalability](#scalability)
      - [Performance](#performance)
      - [Consistency](#consistency)
- [**Techniques**](#techniques)
   - [Replication](#replication)
   - [Partitioning](#partitioning)
   - [Denormalization (Materialized View)](#denormalization-materialized-view)

## Types
### Overview

![cb5bb38f-5383-495d-aed8-cf1d0a44e03b_1600x1600](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a25e8586-14b1-45f4-8ae0-6f6beb736973)

- Relational databases
- NoSQL databases
- NewSQL databases
- Time-series

### Details of main types
#### Relational databases
- **Key points**
   - Relational databases are based on the relational model, which organizes data into tables with rows and columns.
   - Relational databases is suitable for storing structured data.
- **Pros**
   - *Structured data*
      - Data in relational databases is stored in tables with a predefined schema, enforcing a consistent structure throughout the database.
   - *Relationships and referential integrity*
      - The relationships between tables in a relational database are defined by primary and foreign keys, ensuring referential integrity.
   - *SQL support*
      - Relational databases use Structured Query Language (SQL) for querying, manipulating, and managing data. SQL is a powerful and widely adopted language that enables developers to perform complex queries and data manipulations.
   - *Transactions and ACID properties*
      - Relational databases support transactions, which are sets of related operations that either succeed or fail as a whole. This feature ensures the ACID properties are maintained, guaranteeing data consistency and integrity.
   - *Indexing and optimization*
      - Relational databases offer various indexing techniques and query optimization strategies, which help improve query performance and reduce resource consumption.
- **Cons**
   - *Limited scalability*
      - Scaling relational databases horizontally (adding more nodes) can be challenging.
   - *Low flexibility*
      - The predefined schema in relational databases can make it difficult to adapt to changing requirements, as altering the schema may require significant modifications to existing data and applications.
   - *Performance issues*
      - As the volume of data grows, relational databases may experience performance issues, particularly when dealing with complex queries and large-scale data manipulations.
   - *Inefficient for unstructured or semi-structured data*
      - Relational databases may not be suitable for managing unstructured or semi-structured data, such as social media data or sensor data.
- **Common products**
   - MySQL
   - PostgreSQL
   - Oracle Database
   - Microsoft SQL Server
   - Amazon RDS
   - SQLite
   - IBM Bb2
   - MariaDB

  ![b5d5235c-260c-4cf6-969b-efa2af2265bb_1600x402](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/c602649c-ee04-4313-8b8f-6ce463cdec8f)

#### NoSQL databases
- **Key points**
   - NoSQL databases can store data in various formats, which makes them suitable for a diverse range of use cases.
   - NoSQL databases is suitable for storing semi-structured data.
- **Sub-types**
   - *Document-oriented*
      - Concept
         - Documents encapsulate and encode data in some standard formats or encodings (JSON,XML,YAML,BSON).
      - Pros
         - Flexibility (Schemaless)
      - Use cases
         - Need to store hierarchical or nested data (JSON, XML).
      - Products
         - MongoDB
         - CouchDB
         - Terrastore
         - OrientDB
         - RavenDB
   - *Column-oriented (Wide-column)*
      - Concept
         - Organize data by columns rather than rows.
      - Pros
         - Provides improved compression and better read performance.
      - Use cases
         - Need to store and query large amounts of data across many nodes (Popular choice for big data and analytics).
         - Need to handle high write and read workloads.
      - Products
         - Cassandra
         - HBase
         - Hypertable
         - Amazon SimpleDB
   - *Key–value*
      - Concepts
         - Store data as key-value pairs.
      - Pros
         - High read and write performance.
         - Horizontal scalability.
      - Use cases
         - Needs to handle high-speed reads and writes
            - Caching layers
            - Session stores
            - Configuration storage
         - Needs to have low-latency access to data
            - Gaming platforms
            - Real-time analytics systems
            - Recommendation engines
      - Products
         - Redis
         - Memcache
         - Amazon DynamoDB
         - Cassandra
         - Couchbase
   - *Graph*
      - Concepts
         - Store data as nodes and edges in a graph
      - Pros
         - Efficient processing of complex relationships, traversals, and graph-based algorithms.
         - Provide powerful querying capabilities for traversing and analyzing interconnected data.
      - Use cases
         - Need to involve intricate relationships between entities.
            - Social networks
            - Fraud detection systems
            - Recommendation engines
      - Products
         - Neo4J
         - Amazon Neptune
         - Infinitegraph
         - OrientDB
         - FlockDB
- **Cons**
   - *Lack of standardization*
      - NoSQL databases often use their own query languages or APIs. This can lead to increased learning curves and difficulties.
   - *Weaker consistency*
      - Many NoSQL databases employ eventual consistency models to achieve higher performance and availability.
   - *Limited support for complex queries and transactions*
      - Some NoSQL databases are not designed for complex queries or multi-record transactions.

   ![2ee12dc5-0546-4f35-8ad3-df051bb47c6a_1600x399](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/32723127-e7f1-49fc-b0f0-3871186e3878)

#### NewSQL databases
- **Key points**
   - Modern approach to combining the strengths of both relational and NoSQL databases.
      - They maintain the relational model, ACID properties, and SQL support.
      - They offer improved scalability, distributed architecture, and performance enhancements.
- **Pros**
   - *Distributed architecture*
      - NewSQL databases are distributed. They leverage data partitioning and replication across multiple nodes or even data centers. This architecture allows for better fault tolerance, high availability, and global scale.
   - *Horizontal scalability*
      - NewSQL databases can scale horizontally (Adding more nodes to the system).
   - *Concurrency control*
      - NewSQL databases use advanced concurrency control mechanisms (e.g. multi-version concurrency control (MVCC) or optimistic concurrency control). These mechanisms allow efficient handling of a large number of simultaneous transactions.
   - *SQL support*
      - NewSQL databases support SQL for querying and manipulating data.
         - Simplify the learning curve for developers.
         - Provide compatibility with existing relational databases and tools.
         - simplify the migration process.
- **Cons**
   - *Complexity*
      - NewSQL databases can introduce additional complexity in terms of configuration, maintenance, and troubleshooting.
   - *Vendor lock-in*
      - Some NewSQL databases are offered as managed services by specific vendors, which may lead to vendor lock-in and limit the flexibility to switch providers.
   - *Lack of maturity*
      - NewSQL databases may lack the maturity and extensive ecosystem.
- **Products**
   - Google Cloud Spanner
   - CockroachDB
   - NuoDB
   - VoltDB
   - TiDB

  ![1234](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/6c675949-ba81-48c9-a2a7-677bc99f4fa8)
   
#### Time-series databases
- **Key points**
   - Specialize in handling time-stamped (time-series) data.
- **Pros**
   - *High write and query performance*
      - Time-series databases are optimized for handling high-velocity data streams, which require efficient write performance.
      - Time-series databases provide fast query performance, allowing for real-time or near-real-time analysis of time-series data.
   - *Data compression*
      - Due to the large volume of data generated by time-series workloads, time-series databases use various data compression techniques to reduce storage requirements.
   - *Data retention policies*
      - Time-series databases enable easy management of data retention policies based on time. This feature allows for automatic data aging, which helps to maintain storage efficiency and ensure data relevance.
   - *Built-in time-series functions*
      - Time-series databases typically include built-in functions and tools to facilitate time-series data analysis, such as aggregation, downsampling, and forecasting.
   - *Horizontal scalability*
      - Time-series databases are designed to scale horizontally, allowing them to handle large volumes of data and high ingestion rates.
- **Products**
   - InfluxDB
   - TimescaleDB
   - Prometheus
   - Graphite

  ![f4f988a0-8cd6-4a5d-a228-00f0fd2b4fc6_1286x1382](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/d877e131-592e-4b24-af8c-a2fca53f4a3c)

### Comparisons
- Relational and NoSQL database

| | Relational database | NoSQL database |
|---|---|---|
| Schema | Fixed | Dynamic |
| Query Language | SQL | UnQL (Unstructured Query Language) |
| Scalability | Vertically scalable | Horizontally scalable |
| Transaction Guarantee | ACID | BASE (for performance and scalability) |
| Sub-types | | <li>Document<li>Wide-column<li>Key-value<li>Graph<li>Object<li>Tuple |
| When to use | <li>Structured data<li>Need for complex joins<li>Need for ACID guarantee<li>The scale of data is small/medium and consistent | <li>Semi-structured or unstructured data<li>No need for complex joins<li>No need for ACID guarantee<li>The scale of data is huge (TB or PB) and grows massively (high scalability)<li>Need for high performance (high throughput, super-low latency) |

## Selection
### Factors

![d05f286e-16e5-457c-aee3-cc6b960c796d_1600x755](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/cb04f20f-5b22-4a0d-876e-3652bca94cb4)

#### Scalability
- **Methods of scaling**
   - *Vertical scaling*
      - Add resources (CPU, memory, etc.) to a single server.
   - *Horizontal scaling*
      - Add more servers to the system.
- **Characteristics**
   - Relational databases often have low scalability but high consistency.
      - Relational databases can struggle with horizontal scaling.
   - NoSQL databases often have high scalability but low consistency.
      - NoSQL databases often excel in horizontal scaling.
   - NewSQL databases aim to balance scalability and consistency.
   - Time-series databases often provide good scalability.
- **Considerations**
   - Consider the expected growth of the project and how well the database can handle such expansion.
   - Assess the database's ability to scale vertically or horizontally to handle for handling increasing data volumes and traffic loads.

#### Performance
- **Considerations**
   - Consider the performance requirements of the project.
   - Consider the balance between read and write performance.
      - Some databases may be optimized for read-heavy workloads.
      - Some other databases may be optimized for write-heavy workloads.
   - Consider the query efficiency.
      - Query efficiency means the capability to handle complex queries and aggregation with good performance.
- **Characteristics**
   - Relational databases usually provide better querying efficiency
      - Relational databases offer structured schema and support for SQL.
   - NoSQL databases can offer faster write speeds but may have low query efficiency.
      - NoSQL databases have simpler data models and more flexible schemas.
   - NewSQL databases aim to provide both high query efficiency and high write performance.
      - NoSQL databases often employ innovative techniques, such as distributed query processing and advanced indexing.
   - Time-series databases often provide good write performance.
      - Time-series databases need to handle time-based data.

#### Consistency
- **Theorem**
   - *CAP theorem*
      - A distributed database system can only achieve two out of the three properties: Consistency, Availability, and Partition tolerance.
   - *PACELC theorem*
      - An extension to the CAP theorem.
      - In case of network partitioning (P) in a distributed system, one has to choose between availability (A) and consistency (C) (as per the CAP theorem), but else (E), even when the system is running normally in the absence of partitions, one has to choose between latency (L) and consistency (C).
- **Levels**
   - *Strong consistency*
      - All nodes in the system see the same version of data at the same time. 
      - Based on [ACID](../concepts/Transaction.md#acid-consistency-over-availability) properties (Atomicity, Consistency, Isolation and Durability).
   - *Eventual consistency*
      - All nodes will eventually converge to the same state, but it's possible for different nodes to have different views of the data for a certain period of time.
      - Based on [BASE](../concepts/Transaction.md#base-availability-over-consistency---eventual-consistency) properties (Basically Available, Soft state and Eventually consistent).
   - *Causal Consistency*
      - All nodes see updates that are causally related in the same order.
- **Considerations**
   - Consider the performance requirements of the project.
      - Financial applications need strong consistency.
      - For other applications, eventual consistency is enough.
- **Characteristics**
   - Relational databases typically emphasize strong consistency.
   - NoSQL databases often lean towards eventual consistency.


#### Data model
- **Structured levels**
   - *Structured*
      - Structured data refers to data that follows a predefined schema or format.
      - It is organized into rows and columns, similar to a table, and each data element has a well-defined data type.
      - Examples: Data stored in relational databases, spreadsheets, CSV, TSV.
   - *Semi-structured*
      - Semi-structured data is less rigidly organized compared to structured data.
      - It doesn't conform to a fixed schema, but it does have some form of hierarchy or organization.
      - Examples: Data stored in NoSQL databases, JSON, XML.
   - *Unstructured*
      - Unstructured data lacks a predefined structure or format.
      - Examples: Text documents, social media posts, images, videos, audios.
- **Considerations**
   - Consider schema flexibility.
   - Consider support for complex data relationships.
- **Characteristics**
   - Relational databases use a fixed schema and support complex data relationships.
   - NoSQL databases often offer more flexible schemas and can be better suited for flexible data relationships.
 
#### Security
- **Considerations**
   - Consider the authentication and authorization mechanisms.
      - Databases should provide robust mechanisms for managing user accounts, roles, and permissions.
   - Consider the encryption and data protection capabilities.
      - Use strong encryption algorithms, such as AES-256
      - Databases could provide additional data protection features (e.g. data masking or redaction).
   - Consider to integrate databases with built-in security mechanisms (e.g. identity providers, firewalls, and intrusion detection systems).

#### Cost
- **Considerations**
   - Consider fee and cost:
      - Licensing fee.
      - Hosting fee.
      - Maintenance and management cost.
         - Software and hardware upgrades.
         - Staff training.
   - Evaluate the cost against the benefits they provide.
- **Examples**
   - Open-source databases (free)
      - MySQL
      - PostgreSQL
   - Proprietary databases (paid)
      - Oracle Database
      - Microsoft SQL Server
    
<img width="794" alt="Screenshot 2023-09-08 at 10 34 26 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/1561ffcf-aec8-4573-8b15-89dbbe6e31f5">
  
#### Community and ecosystem
- **Considerations**
   - Consider community
      - Documentation, tutorials, and communication channels (forums, mailing list, chat platforms).
      - Easier to troubleshoot issues, learn best practices, and optimize the database's performance.
   - Consider ecosystem
      - Integration with other technologies, tools, and services.
      - Simplify the process of incorporating the database into the existing technology stack.

<img width="802" alt="Screenshot 2023-09-08 at 10 42 45 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/70aa19bf-cb27-438a-b969-28619de3dc32">

## Techniques
### Replication
| | Master-slave | Master-master |
|---|---|---|
| Architecture | ![C9ioGtn](https://user-images.githubusercontent.com/8989447/116644854-b334b680-a931-11eb-9ff5-60f57652b09d.png) | ![krAHLGg](https://user-images.githubusercontent.com/8989447/116644889-cc3d6780-a931-11eb-956d-c6eebf2f218f.png) |
| Alias | Single-leader | Multi-leader |
| Write operations | Master only  | Masters |
| Read operations | Master and slaves | Masters |
| Failure handling | <li>If the master is down, one of the slave will be promoted to be a new master. | <li>If one master is down, other masters can still handle reads and writes. |

### Partitioning
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

### Denormalization (Materialized View)
   
   ![materialized-view-pattern-diagram](https://user-images.githubusercontent.com/8989447/154134405-95c792a7-ce84-4b8b-94a9-6dbdf145fb44.png)
   
- **Concept**
   - Add redundant copies of data or by grouping data to improve the read performance of a database
- **Pros**
   - Improve read performance.
- **Cons**
   - Degrade write performance.
   - Increase complexity of database design.
   - Data is duplicated.
