# Database Selection

- [**Factors**](#factors)
   - [Scalability](#scalability)
   - [Performance](#performance)
   - [Consistency](#consistency)
   - [Data model](#data-model)
   - [Security](#security)
   - [Cost](#cost)
   - [Community and ecosystem](#community-and-ecosystem)
- [**Process**](#process)

## Factors

![d05f286e-16e5-457c-aee3-cc6b960c796d_1600x755](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/cb04f20f-5b22-4a0d-876e-3652bca94cb4)

### Scalability
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

### Performance
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

### Consistency
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


### Data model
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
 
### Security
- **Considerations**
   - Consider the authentication and authorization mechanisms.
      - Databases should provide robust mechanisms for managing user accounts, roles, and permissions.
   - Consider the encryption and data protection capabilities.
      - Use strong encryption algorithms, such as AES-256
      - Databases could provide additional data protection features (e.g. data masking or redaction).
   - Consider to integrate databases with built-in security mechanisms (e.g. identity providers, firewalls, and intrusion detection systems).

### Cost
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
  
### Community and ecosystem
- **Considerations**
   - Consider community
      - Documentation, tutorials, and communication channels (forums, mailing list, chat platforms).
      - Easier to troubleshoot issues, learn best practices, and optimize the database's performance.
   - Consider ecosystem
      - Integration with other technologies, tools, and services.
      - Simplify the process of incorporating the database into the existing technology stack.

<img width="802" alt="Screenshot 2023-09-08 at 10 42 45 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/70aa19bf-cb27-438a-b969-28619de3dc32">

## Process

<img width="768" alt="Screenshot 2023-09-08 at 11 05 55 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/c8fae321-c8c4-4acd-912a-47a8b657cb46">

### Steps
- **Step 1**: Data model
   - Examine the types of data our project will handle.
      - Structured data
      - Semi-structured data
      - Unstructure data
- **Step 2**: Data patterns or relationship
   - Examine the data patterns or relationships that need to be captured.
- **Step 3**: Data volume
   - Examine the expected volume of data the project will generate, both now and in the future. 



