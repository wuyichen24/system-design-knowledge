# distributed-system-design-pattern

## Overview
Collect modern distributed system design patterns.

## Categories
- [**Architecture Pattern**](#architecture-patterns)
   - Anti-Corruption Layer (ACL)
   - Backends for Frontends (BFF)
- [**Cache Pattern**](#cache-patterns)
   - Cache-Aside
   - Cache-As-SOR
      - Read-Through
      - Write-Through
      - Write-Behind
      - Refresh-Ahead
- **Configuration Patterns**
   - [External Configuration Store](patterns/configuration_patterns/External_Configuration_Store.md)
   - [Runtime Reconfiguration](patterns/configuration_patterns/Runtime_Reconfiguration.md)
- [**Container Patterns**](#container-patterns)
   - Single-node, multi-container patterns
      - [Sidecar](patterns/container_patterns/Sidecar.md)
      - [Ambassador](patterns/container_patterns/Ambassador.md)
      - [Adapter](patterns/container_patterns/Adapter.md)
   - Multi-node patterns
      - Leader Election
      - Work Queue
      - Scatter/Gather
- **Data Management Patterns**
   - Command Query Responsibility Segregation (CQRS)
   - Event Sourcing
   - API Composition
   - Database Per Service
   - Shared Database
- [**Messaging Patterns**](#messaging-patterns)
   - Claim Check
- [**Resiliency Patterns**](#resiliency-patterns)
   - Circuit Breaker
   - Fallback
   - Bulkhead
   - Retry
- **Security Patterns**
   - Valet Key
- **Transaction Patterns**
   - Two-Phase Commit (2PC)
   - Three-Phase Commit (3PC)
   - Saga

----

## Brief Introduction

### Architecture Patterns

| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| *Anti-Corruption Layer* (ACL) | ![](./diagrams/png/anti_corruption_layer_small.png) | Place an adapter layer between 2 domain models and translate communications between them. | 
| *Backends For Frontends* (BFF) | ![](./diagrams/png/backends_for_frontends_small.png) | Separate backend services for different frontend applications or interfaces. |

### Cache Patterns

#### Cache Pattern Categories

| Category Name | Diagram | Description | Patterns |
|----|----|----|----|
| *Cache-Aside* | ![](./diagrams/png/cache_aside_small.png) | Application interacts with both cache and database (No interaction between cache and database). |  |
| *Cache-As-SOR* | ![](./diagrams/png/cache_as_sor_small.png) | Application only interacts with cache. | <ul><li>Read-Through<li>Write-Through<li>Write-Behind<li>Refresh-Ahead</ul> |

#### Cache-As-SOR Patterns

| Pattern Name | Diagram | Description | 
|----|----|----|
| *Read-Through* | ![](./diagrams/png/read_through_small.png) | If requested data is not in cache, cache will load the data from database and let application read **synchronously**. |
| *Write-Through* | ![](./diagrams/png/write_through_small.png) | After application writes data to cache, cache **synchronously** write the same data to database. |
| *Write-Behind* | ![](./diagrams/png/write_behind_small.png) | After application writes data to cache, cache **asynchronously** write the same data to database (When satisfy a certain criteria). |
| *Refresh-Ahead* | ![](./diagrams/png/refresh_ahead_small.png) | Cache automatically and **asynchronously** reloads (refreshs) any recently accessed cache entry from database before its expiration. |

### Container Patterns

| Pattern Name | Diagram | Description |
|----|-------|----|
| *Ambassador* | ![](./diagrams/png/ambassador_small.png) | <ul><li>Place an ambassador container between the main application container and the external system for simplifying the view of the external system.</ul> |
| *Adapter* | ![](./diagrams/png/adapter_small.png) | <ul><li>Place an adapter container between the main application container and the external system for standardizing the view of the internal application.</ul> |
| *Sidecar* | ![](./diagrams/png/sidecar_small.png) | <ul><li>Place an independent sidecar container next to the main application container for providing supportive works to the main application container.</ul> |
| *Leader Election* | ![](./diagrams/png/leader_election_small.png) | <ul><li>Elect one instance as the leader for coordinating and monitoring the other instances.</ul> |
| *Work Queue* | ![](./diagrams/png/work_queue_small.png) | <ul><li>Group a work queue manager container and a work queue source container as a coordinator for managing the work queue and dispatch work items to workers.<li>Each worker consists of a worker manager container (for integrating with the generic work queue framework) and an application implementation container (for application-specific logic).</ul> |
| *Scatter/Gather* | ![](./diagrams/png/scatter_gather_small.png) | <ul><li>The root node scatters out the original request to a group of servers to perform a set of tasks in parallel.<li>The root node gathers the partial data from each server and return a single response to the original request.</ul>

### Data Management Patterns

| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| *Command Query Responsibility Segregation* (CQRS) | ![](./diagrams/png/command_query_responsibility_segregation_small.png) | Use separated models for different types of operations: Command (update data) and Query (read data). |
| *Event Sourcing* | ![](./diagrams/png/event_sourcing_small.png) | Use a sequence of events to capture a series of changes to data. |
| *API Composition* |  |  |
| *Database Per Service* |  |  |
| *Shared Database* |  |  |

### Messaging Patterns

| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| *Claim Check* | ![](./diagrams/png/claim_check_small.png) | When sending a large message from one service to another, store the large message into a data store, only send the reference as the claim check to the receiver service for retrieving the large message from the data store. |

### Resiliency Patterns

| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| *Circuit Breaker* |  | Prevent an application from performing an operation that is likely to fail based on a certain criteria. |
| *Bulkhead* |  | Isolate the misbehaving service and avoid to take down the entire application by exhausting all the resources. |
| *Fallback* |  | When a service call fails, execute the alternative action. |
| *Retry* |  | Retry a failed operation. |

### Transaction Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| Two-Phase Commit (2PC) |  | <ul><li>**Commit-Request/Voting Phase**<ul><li>Each participants execute the transaction and send back the aggreement message (the transcation is successful) or the abort message (the transcation is fail) to the the coordinator.</ul><li>**Commit/Completion Phase**<ul><li>**Success**: If the coordinator received an agreement message from all participants:<ul><li>The coordinator sends a commit message to all the participants.<li>Each participant commits the transcation and releases all the locks.<li>Each participant sends an acknowledgement to the coordinator.</ul><li>**Failure**: If any participant sent a abort message to the coordinator:<ul><li>The coordinator sends a rollback message to all the participants.<li>Each participant undos the transaction and release all the locks.<li>Each participant sends an acknowledgement to the coordinator.</ul></ul></ul> |
| Three-Phase Commit (3PC) |  |  |
| Saga |  | <ul><li>A sequence of asynchronous local transactions.<li>Each service<ul><li>Starts its action by getting a event/message from the previous service.<li>Sends a event/message to the next service when it completes its action.</ul></ul> |
