# Memory Sheet

## Concepts
- **Theory**
   - *CAP Theorem*
- **Evaluation dimensions**
   - *Scalability*
      - Concept
      - Type of scaling
         - Concepts
         - Cons
      - How to achieve high scalability
   - *Availability*
      - Concept
      - How to achieve high availability
      - Metrics
   - *Consistency*
      - Models
   - *Performance*
      - Metrics
- **API**
   - *API architectural styles*
      - SOAP, REST, gRPC, GraphQL, WebSocket, Webhook.
      - Concept, pros, cons, use cases.
   - *API design*
      - REST API design best practices.

## Components
### Database
- **Types**
   - Main types
   - Subtypes for NoSQL
   - Concepts, pros, cons, use case, examples.
   - Factors for choosing database.
- **Index**
   - Main categories
   - Types
   - Best practices
- **Techniques**
   - *Replication*
      - Types
   - *Partitioning*
      - Types
      - Common issues and solutions
         - Join operation
         - Hot spot
      - Split data into multiple databases or multiple tables?
   - *Sharding*
      - Types
      - How to query
         - On sharding key
         - On non-sharding columns (3 solutions)
- **Design**
   - *Schema design*
      - Steps
      - Normalization
         - 1NF, 2NF, 3NF
      - Denormalization

### Message queue
- **Basics**
   - Pros and cons
   - Selections
      - Factors
      - Differences and use cases between RabbitMQ and Kafka
   - Common problems and solutions
      - How to guarantee message order? (1 solution)
      - How to handle duplicated message? (2 solutions)
   - Use cases (5)
- **Kafka**
   - Terminologies
      - Topic, partitions, consumer groups
   - Patitions
      - Concepts, relationship between partions and consumer group.
   - Why Kafka fast?      