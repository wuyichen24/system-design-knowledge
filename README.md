# system-design-knowledge

[![License: CC BY-NC-ND 4.0](https://licensebuttons.net/l/by-nc-nd/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

## Overview
Accumulate system design knowledge (concepts, patterns, technology choices, etc.) from different resources (books, essays, web, etc.).

## Basics
- [**Message Queue**](basics/Message_Queue.md)
- [**Transaction**](basics/Transaction.md)
- [**Cache**](basics/Cache.md)

## Categories
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
   - [API Gateway](patterns/external_api_patterns/API_Gateway.md)
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

----

## Brief Introduction
### Data Management Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Command Query Responsibility Segregation (CQRS)*](patterns/data_management_patterns/Command_Query_Responsibility_Segregation.md) | ![](./diagrams/png/command_query_responsibility_segregation_small.png) | Use separated models for different types of operations: Command (update data) and Query (read data). |
| [*Event Sourcing (ES)*](patterns/data_management_patterns/Event_Sourcing.md) | ![](./diagrams/png/event_sourcing_small.png) | Use a sequence of events to capture a series of changes to data. |
| [*API Composition*](patterns/data_management_patterns/API_Composition.md) | ![](./diagrams/png/api_composition_small.png) | Use an API composer to retrieve data from multiple services and combine the results for query operations. |

### Transaction Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Two-Phase Commit (2PC)*](patterns/transaction_patterns/Two_Phase_Commit.md) | ![](./diagrams/png/2pc_small.png) | The coordinator uses 2 phases (prepare phase and commit phase) to coordinates participants on whether to commit or abort (roll back) a distributed transaction. |
| [*Three-Phase Commit (3PC)*](patterns/transaction_patterns/Three_Phase_Commit.md) | ![](./diagrams/png/3pc_small.png) | <li>Add a new phase (prepared to commit phase) in the middle of the original 2 phases in 2PC.<li>Provide a dependable recovery solution if a participant failure or both coordinator and participant failure during commit phase. |
| [*Saga*](patterns/transaction_patterns/Saga.md) | ![](./diagrams/png/saga_small.png) | <ul><li>A sequence of asynchronous local transactions.<li>Each service<ul><li>Starts its action by getting a event/message from the previous service.<li>Sends a event/message to the next service when it completes its action.</ul><li>If one action fails, executes compensating transactions to rollback the changes.</ul> |
| [*Try-Confirm/Cancel (TCC)*](patterns/transaction_patterns/Try_Confirm_Cancel.md) | ![](./diagrams/png/try_confirm_cancel_small.png) | <li>Use 2 phases (try phase and confirm phase) to change a state.<li>Add an intermediate state (pending state or reserved state) in the middle of those 2 phases. |

### External API Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*API Gateway*](patterns/external_api_patterns/API_Gateway.md) | ![](./diagrams/png/api_gateway_small.png) | Implement a service that’s the entry point into the microservices-based application for external API clients. |
| [*Backends for Frontends (BFF)*](patterns/external_api_patterns/Backends_For_Frontends.md) | ![](./diagrams/png/backends_for_frontends_small.png) | Separate backend services for different frontend applications or interfaces. |

### Resiliency Patterns
| Pattern Name | Description |
| ---- | ---- |
| [*Circuit Breaker*](patterns/resiliency_patterns/Circuit_Breaker.md) |Detects failures and prevents a failure from constantly recurring. |
| [*Bulkhead*](patterns/resiliency_patterns/Bulkhead.md) | Isolate the misbehaving service and avoid to take down the entire application by exhausting all the resources. |
| [*Fallback*](patterns/resiliency_patterns/Fallback.md) | When a request to a service fails, return an alternative response to the request. |
| [*Retry*](patterns/resiliency_patterns/Retry.md) | Retry a falling operation. |
| [*Timeout*](patterns/resiliency_patterns/Timeout.md) | Set a limited period of time to wait for a response. |

### Messaging Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Claim Check*](patterns/messaging_patterns/Claim_Check.md) | ![](./diagrams/png/claim_check_small.png) | When sending a large message from one service to another, store the large message into a data store, only send the reference as the claim check to the receiver service for retrieving the large message from the data store. |
| [*Publishing Events Using Local Transactions*](patterns/messaging_patterns/Publishing_Events_Using_Local_Transactions.md) | ![](./diagrams/png/publishing_events_using_local_transactions_small.png) | <li>Uses the event table to store the events need to be published.<li>Bundles the operation of inserting new record into a business entity table and the operation of inserting a new event to the event table as a single local database transaction.<li>Event publisher publishes events by polling the event table periodically. |
| [*Transaction Log Tailing*](patterns/messaging_patterns/Transaction_Log_Tailing.md) | ![](./diagrams/png/transaction_log_tailing_small.png) | <li>Publish messages by tailing the database’s transaction log.<li>A transaction log miner reads the transaction log and publish each change as a message to the message broker. |

### Legacy System Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Anti-Corruption Layer (ACL)*](patterns/legacy_system_patterns/Anti_Corruption_Layer.md) | ![](./diagrams/png/anti_corruption_layer_small.png) | Place an adapter layer between 2 domain models and translate communications between them. | 
| [*Strangler*](patterns/legacy_system_patterns/Strangler.md) | ![](./diagrams/png/strangler_small.png) | Incrementally refactor the legacy application to the new application and services. |

### Cache Patterns
| Category Name | Diagram | Description | Sub-Patterns |
|----|----|----|----|
| [*Cache-Aside*](patterns/cache_patterns/Cache_Aside.md) | ![](./diagrams/png/cache_aside_small.png) | Application interacts with both cache and database (No interaction between cache and database). |  |
| [*Cache-As-SOR*](patterns/cache_patterns/Cache_As_Sor.md) | ![](./diagrams/png/cache_as_sor_small.png) | Application only interacts with cache. | <ul><li>Read-Through<li>Write-Through<li>Write-Behind<li>Refresh-Ahead</ul> |

### Container Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*Sidecar*](patterns/container_patterns/Sidecar.md) | ![](./diagrams/png/sidecar_small.png) | <ul><li>Place an independent sidecar container next to the main application container for providing supportive works to the main application container.</ul> |
| [*Ambassador*](patterns/container_patterns/Ambassador.md) | ![](./diagrams/png/ambassador_small.png) | <ul><li>Place an ambassador container between the main application container and the external system for simplifying the view of the external system.</ul> |
| [*Adapter*](patterns/container_patterns/Adapter.md) | ![](./diagrams/png/adapter_small.png) | <ul><li>Place an adapter container between the main application container and the external system for standardizing the view of the internal application.</ul> |
| [*Leader Election*](patterns/container_patterns/Leader_Election.md) | ![](./diagrams/png/leader_election_small.png) | <ul><li>Elect one instance as the leader for coordinating and monitoring the other instances.</ul> |
| [*Work Queue*](patterns/container_patterns/Work_Queue.md) | ![](./diagrams/png/work_queue_small.png) |A scalable master-worker framework for distributing millions of tasks to thousands of remote workers drawn from clusters, clouds, and grids. |
| [*Scatter/Gather*](patterns/container_patterns/Scatter_Gather.md) | ![](./diagrams/png/scatter_gather_small.png) | <ul><li>The root node scatters out the original request to a group of servers to perform a set of tasks in parallel.<li>The root node gathers the partial data from each server and return a single response to the original request.</ul> |

### Configuration Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*External Configuration Store*](patterns/configuration_patterns/External_Configuration_Store.md) | | Externalize all application configuration properties to a centralized location. |

### Other Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*Health Check API*](patterns/other_patterns/Health_Check_API.md) | | A service exposes a health check API endpoint which returns the health of the service. |
