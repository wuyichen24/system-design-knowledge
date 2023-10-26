# system-design-knowledge

[![License: CC BY-NC-ND 4.0](https://licensebuttons.net/l/by-nc-nd/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

## Overview
Accumulate system design knowledge (concepts, patterns, technology choices, etc.) from different resources (books, essays, web, etc.).

## Concepts
- **Theory**
   - [CAP Theorem](concepts/CAP_Theorem.md)
- **Evaluation dimensions**
   - [Scalability](concepts/Scalability.md)
   - [Availability](concepts/Availability.md)
   - [Consistency](concepts/Consistency.md)
- **Network**
   - [OSI model](concepts/network/OSI_Model.md)
   - [TCP and UDP](concepts/network/TCP_UDP.md)
   - [HTTP](concepts/network/HTTP.md)
- **Microservice**
   - [Service Discovery](concepts/Service_Discovery.md)
- **Algorithms**
   - [Consistent Hashing](concepts/Consistent_Hashing.md)
   - Token bucket (rate limiter)
   - Leaky bucket (rate limiter)
   - Geohash (location based service)
   - Quadtree (location based service)
- [**Data Encoding Formats (XML,JSON,CSV,Protobuf..)**](concepts/Data_Encoding_Formats.md)
- **API**
   - [*API Architectural Styles*](concepts/api/API_Architectural_Styles.md)
      - [SOAP](concepts/api/API_Architectural_Styles.md#soap)
      - [REST](concepts/api/API_Architectural_Styles.md#rest)
      - [RPC](concepts/api/API_Architectural_Styles.md#rpc)
         - [gRPC](concepts/api/API_Architectural_Styles.md#grpc)
         - [Avro RPC](concepts/api/API_Architectural_Styles.md#avro-rpc)
      - [GraphQL](concepts/api/API_Architectural_Styles.md#graphql)
      - [WebSocket](concepts/api/API_Architectural_Styles.md#websocket)
      - [Webhook](concepts/api/API_Architectural_Styles.md#webhook)
   - *API Design*
      - [REST API Design Best Practices](concepts/api/REST_API_Design_Best_Practices.md)
      - [API Design Mindset](concepts/api/API_Design_Mindset.md)
   - [*API Performance*](concepts/api/API_Performance.md)
      - [How to improve API performance](concepts/api/API_Performance.md#how-to-improve-api-performance)
      - [Metrics](concepts/api/API_Performance.md#metrics)
- **Security**
   - Authentication
   - Authorization
- **Basic knowledge**
   - [Metrics](concepts/Metrics.md)
      - [Storage](concepts/Metrics.md#storage)
      - [Performance](concepts/Metrics.md#performance)
- **Cloud service**
   - [AWS](concepts/cloud_service/AWS.md)

## Components
### Database (DB)
- [**Types**](components/database/Database_Types.md)
   - [Overview](components/database/Database_Types.md#overview)
   - [Details of main types](components/database/Database_Types.md#details-of-main-types)
      - [Relational databases](components/database/Database_Types.md#relational-databases)
      - [NoSQL databases](components/database/Database_Types.md#nosql-databases)
      - [NewSQL databases](components/database/Database_Types.md#newsql-databases)
      - [Time-series databases](components/database/Database_Types.md#time-series-databases)
   - [Comparisons](components/database/Database_Types.md#comparisons)
- [**Selection**](components/database/Database_Selection.md)
   - [Factors](components/database/Database_Selection.md#factors)
   - [Process](components/database/Database_Selection.md#process)
- [**Indexing**](components/database/Database_Indexing.md)
   - [Concepts](components/database/Database_Indexing.md#concepts)
   - [Benefits](components/database/Database_Indexing.md#benefits)
   - [Data structure](components/database/Database_Indexing.md#data-structure)
   - [Main categories](components/database/Database_Indexing.md#main-categories)
   - [Types](components/database/Database_Indexing.md#types)
   - [Use cases](components/database/Database_Indexing.md#use-cases)
   - [Best practices](components/database/Database_Indexing.md#best-practices)
- [**Transaction**](components/database/Database_Transaction.md)
   - [Models](components/database/Database_Transaction.md#models)
   - [Isolation**](components/database/Database_Transaction.md#isolation)
   - [Distributed transactions](components/database/Database_Transaction.md#distributed-transactions)
- [**Techniques**](components/database/Database_Techniques.md)
   - [Replication](components/database/Database_Techniques.md#replication)
   - [Partitioning](components/database/Database_Techniques.md#partitioning)
   - [Sharding](components/database/Database_Techniques.md#sharding)
- [**Design**](components/database/Database_Design.md)
   - [Schema Design](components/database/Database_Design.md#schema-design)
      - [Steps](components/database/Database_Design.md#steps)
      - [Normalization](components/database/Database_Design.md#normalization)
      - [Denormalization (Materialized view)](components/database/Database_Design.md#denormalization-materialized-view)
      - [Best practices](components/database/Database_Design.md#best-practices)
- Todo
   - clustering and joins
   - DDL, DML and DCL
   - Different types of joins
   - Types Of Keys
   - view
   - multilevel indexing
   - Sparse indexing vs dense indexing
### Message Queue (MQ)
- [**Message Queue (MQ)**](components/message_queue/Message_Queue.md)
   - [Pros & Cons](components/message_queue/Message_Queue.md#pros--cons)
   - [Selection](components/message_queue/Message_Queue.md#selection)
   - [Common problems and solutions](components/message_queue/Message_Queue.md#common-problems-and-solutions)
   - [Use cases](components/message_queue/Message_Queue.md#use-cases)
- [**Kafka**](components/message_queue/Kafka.md)
- [**RabbitMQ**](components/message_queue/RabbitMQ.md)

### Cache
- [**Cache**](components/cache/Cache.md)
- [**Redis**](components/cache/Redis.md)

### Domain Name System (DNS)
- [Domain Name System (DNS)](components/Domain_Name_System.md)

### API Gateway, Load Balancer (LB)
- [API Gateway](components/API_Gateway.md)
- [Load Balancer (LB)](components/Load_Balancer.md)
- [Proxy And Reverse Proxy](components/Proxy_And_Reverse_Proxy.md)

### Content Delivery Network (CDN)
- [Content Delivery Network (CDN)](components/Content_Delivery_Network.md)

## Patterns
- [**Overview**](patterns/README.md)
- [**Data Management Patterns**](#data-management-patterns)
   - [Command Query Responsibility Segregation (CQRS)](patterns/data_management_patterns/Command_Query_Responsibility_Segregation.md)
   - [Event Sourcing (ES)](patterns/data_management_patterns/Event_Sourcing.md)
   - [API Composition](patterns/data_management_patterns/API_Composition.md)
- [**Transaction Patterns**](#transaction-patterns)
   - [Two-Phase Commit (2PC)](patterns/transaction_patterns/Two_Phase_Commit.md)
   - [Three-Phase Commit (3PC)](patterns/transaction_patterns/Three_Phase_Commit.md)
   - [Saga](patterns/transaction_patterns/Saga.md)
   - [Try-Confirm/Cancel (TCC)](patterns/transaction_patterns/Try_Confirm_Cancel.md)
- [**External API Patterns**](#external-api-patterns)
   - [Backends for Frontends (BFF)](patterns/external_api_patterns/Backends_For_Frontends.md)
- [**Resiliency Patterns**](#resiliency-patterns)
   - [Circuit Breaker](patterns/resiliency_patterns/Circuit_Breaker.md)
   - [Bulkhead](patterns/resiliency_patterns/Bulkhead.md)
   - [Fallback](patterns/resiliency_patterns/Fallback.md)
   - [Retry](patterns/resiliency_patterns/Retry.md)
   - [Timeout](patterns/resiliency_patterns/Timeout.md)
- [**Messaging Patterns**](#messaging-patterns)
   - [Claim Check](patterns/messaging_patterns/Claim_Check.md)
   - [Publishing Events Using Local Transactions](patterns/messaging_patterns/Publishing_Events_Using_Local_Transactions.md)
   - [Transaction Log Tailing](patterns/messaging_patterns/Transaction_Log_Tailing.md)
- [**Legacy System Patterns**](#legacy-system-patterns)
   - [Anti-Corruption Layer (ACL)](patterns/legacy_system_patterns/Anti_Corruption_Layer.md)
   - [Strangler](patterns/legacy_system_patterns/Strangler.md)
- [**Cache Patterns**](#cache-patterns)
   - [Cache-Aside](patterns/cache_patterns/Cache_Aside.md)
   - [Cache-As-SOR](patterns/cache_patterns/Cache_As_Sor.md)
- [**Container Patterns**](#container-patterns)
   - Single-node, multi-container patterns
      - [Sidecar](patterns/container_patterns/Sidecar.md)
         - [Ambassador](patterns/container_patterns/Ambassador.md)
         - [Adapter](patterns/container_patterns/Adapter.md)
   - Multi-node patterns
      - [Leader Election](patterns/container_patterns/Leader_Election.md)
      - [Work Queue](patterns/container_patterns/Work_Queue.md)
      - [Scatter/Gather](patterns/container_patterns/Scatter_Gather.md)
- [**Configuration Patterns**](#configuration-patterns)
   - [External Configuration Store](patterns/configuration_patterns/External_Configuration_Store.md)
- **Security Patterns**
   - [Valet Key](patterns/security_patterns/Valet_Key.md)
- [**Other Patterns**](#other-patterns)
   - [Health Check API](patterns/other_patterns/Health_Check_API.md)

## Best Practices
- [Keep numbers as string](best_practices/Keep_Numbers_As_String.md)
- [Non-technical factors need to be considered for selecting a storage solution](best_practices/Non_Technical_Factors_Need_To_Be_Considered_For_Selecting_Storage_Solution.md)
