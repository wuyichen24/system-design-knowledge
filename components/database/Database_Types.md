# Database Types

- [**Overview**](#overview)
- [**Details of main types**](#details-of-main-types)
   - [Relational databases](#relational-databases)
   - [NoSQL databases](#nosql-databases)
   - [NewSQL databases](#newsql-databases)
   - [Time-series databases](#time-series-databases)
- [**Comparisons**](#comparisons)

## Overview

![cb5bb38f-5383-495d-aed8-cf1d0a44e03b_1600x1600](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a25e8586-14b1-45f4-8ae0-6f6beb736973)

- Relational databases
- NoSQL databases
- NewSQL databases
- Time-series

## Details of main types
### Relational databases
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

### NoSQL databases
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

### NewSQL databases
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
   
### Time-series databases
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

## Comparisons
- Relational and NoSQL database

| | Relational database | NoSQL database |
|---|---|---|
| Schema | Fixed | Dynamic |
| Query Language | SQL | UnQL (Unstructured Query Language) |
| Scalability | Vertically scalable | Horizontally scalable |
| Transaction Guarantee | ACID | BASE (for performance and scalability) |
| Sub-types | | <li>Document<li>Wide-column<li>Key-value<li>Graph<li>Object<li>Tuple |
| When to use | <li>Structured data<li>Need for complex joins<li>Need for ACID guarantee<li>The scale of data is small/medium and consistent | <li>Semi-structured or unstructured data<li>No need for complex joins<li>No need for ACID guarantee<li>The scale of data is huge (TB or PB) and grows massively (high scalability)<li>Need for high performance (high throughput, super-low latency) |
