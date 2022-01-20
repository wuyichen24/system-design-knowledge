# Patterns

## Brief Introduction
### Data Management Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Command Query Responsibility Segregation (CQRS)*](data_management_patterns/Command_Query_Responsibility_Segregation.md) | ![](../diagrams/png/command_query_responsibility_segregation_small.png) | Use separated models for different types of operations: Command (update data) and Query (read data). |
| [*Event Sourcing (ES)*](data_management_patterns/Event_Sourcing.md) | ![](../diagrams/png/event_sourcing_small.png) | Use a sequence of events to capture a series of changes to data. |
| [*API Composition*](data_management_patterns/API_Composition.md) | ![](../diagrams/png/api_composition_small.png) | Use an API composer to retrieve data from multiple services and combine the results for query operations. |

### Transaction Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Two-Phase Commit (2PC)*](transaction_patterns/Two_Phase_Commit.md) | ![](../diagrams/png/2pc_small.png) | The coordinator uses 2 phases (prepare phase and commit phase) to coordinates participants on whether to commit or abort (roll back) a distributed transaction. |
| [*Three-Phase Commit (3PC)*](transaction_patterns/Three_Phase_Commit.md) | ![](../diagrams/png/3pc_small.png) | <li>Add a new phase (prepared to commit phase) in the middle of the original 2 phases in 2PC.<li>Provide a dependable recovery solution if a participant failure or both coordinator and participant failure during commit phase. |
| [*Saga*](transaction_patterns/Saga.md) | ![](../diagrams/png/saga_small.png) | <ul><li>A sequence of asynchronous local transactions.<li>Each service<ul><li>Starts its action by getting a event/message from the previous service.<li>Sends a event/message to the next service when it completes its action.</ul><li>If one action fails, executes compensating transactions to rollback the changes.</ul> |
| [*Try-Confirm/Cancel (TCC)*](transaction_patterns/Try_Confirm_Cancel.md) | ![](../diagrams/png/try_confirm_cancel_small.png) | <li>Use 2 phases (try phase and confirm phase) to change a state.<li>Add an intermediate state (pending state or reserved state) in the middle of those 2 phases. |

### External API Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*API Gateway*](external_api_patterns/API_Gateway.md) | ![](../diagrams/png/api_gateway_small.png) | Implement a service that’s the entry point into the microservices-based application for external API clients. |
| [*Backends for Frontends (BFF)*](external_api_patterns/Backends_For_Frontends.md) | ![](../diagrams/png/backends_for_frontends_small.png) | Separate backend services for different frontend applications or interfaces. |

### Resiliency Patterns
| Pattern Name | Description |
| ---- | ---- |
| [*Circuit Breaker*](resiliency_patterns/Circuit_Breaker.md) |Detects failures and prevents a failure from constantly recurring. |
| [*Bulkhead*](resiliency_patterns/Bulkhead.md) | Isolate the misbehaving service and avoid to take down the entire application by exhausting all the resources. |
| [*Fallback*](resiliency_patterns/Fallback.md) | When a request to a service fails, return an alternative response to the request. |
| [*Retry*](resiliency_patterns/Retry.md) | Retry a falling operation. |
| [*Timeout*](resiliency_patterns/Timeout.md) | Set a limited period of time to wait for a response. |

### Messaging Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Claim Check*](messaging_patterns/Claim_Check.md) | ![](../diagrams/png/claim_check_small.png) | When sending a large message from one service to another, store the large message into a data store, only send the reference as the claim check to the receiver service for retrieving the large message from the data store. |
| [*Publishing Events Using Local Transactions*](messaging_patterns/Publishing_Events_Using_Local_Transactions.md) | ![](../diagrams/png/publishing_events_using_local_transactions_small.png) | <li>Uses the event table to store the events need to be published.<li>Bundles the operation of inserting new record into a business entity table and the operation of inserting a new event to the event table as a single local database transaction.<li>Event publisher publishes events by polling the event table periodically. |
| [*Transaction Log Tailing*](messaging_patterns/Transaction_Log_Tailing.md) | ![](../diagrams/png/transaction_log_tailing_small.png) | <li>Publish messages by tailing the database’s transaction log.<li>A transaction log miner reads the transaction log and publish each change as a message to the message broker. |

### Legacy System Patterns
| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| [*Anti-Corruption Layer (ACL)*](legacy_system_patterns/Anti_Corruption_Layer.md) | ![](../diagrams/png/anti_corruption_layer_small.png) | Place an adapter layer between 2 domain models and translate communications between them. | 
| [*Strangler*](legacy_system_patterns/Strangler.md) | ![](../diagrams/png/strangler_small.png) | Incrementally refactor the legacy application to the new application and services. |

### Cache Patterns
| Category Name | Diagram | Description | Sub-Patterns |
|----|----|----|----|
| [*Cache-Aside*](cache_patterns/Cache_Aside.md) | ![](../diagrams/png/cache_aside_small.png) | Application interacts with both cache and database (No interaction between cache and database). |  |
| [*Cache-As-SOR*](cache_patterns/Cache_As_Sor.md) | ![](../diagrams/png/cache_as_sor_small.png) | Application only interacts with cache. | <ul><li>Read-Through<li>Write-Through<li>Write-Behind<li>Refresh-Ahead</ul> |

### Container Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*Sidecar*](container_patterns/Sidecar.md) | ![](../diagrams/png/sidecar_small.png) | <ul><li>Place an independent sidecar container next to the main application container for providing supportive works to the main application container.</ul> |
| [*Ambassador*](container_patterns/Ambassador.md) | ![](../diagrams/png/ambassador_small.png) | <ul><li>Place an ambassador container between the main application container and the external system for simplifying the view of the external system.</ul> |
| [*Adapter*](container_patterns/Adapter.md) | ![](../diagrams/png/adapter_small.png) | <ul><li>Place an adapter container between the main application container and the external system for standardizing the view of the internal application.</ul> |
| [*Leader Election*](container_patterns/Leader_Election.md) | ![](../diagrams/png/leader_election_small.png) | <ul><li>Elect one instance as the leader for coordinating and monitoring the other instances.</ul> |
| [*Work Queue*](container_patterns/Work_Queue.md) | ![](../diagrams/png/work_queue_small.png) |A scalable master-worker framework for distributing millions of tasks to thousands of remote workers drawn from clusters, clouds, and grids. |
| [*Scatter/Gather*](container_patterns/Scatter_Gather.md) | ![](../diagrams/png/scatter_gather_small.png) | <ul><li>The root node scatters out the original request to a group of servers to perform a set of tasks in parallel.<li>The root node gathers the partial data from each server and return a single response to the original request.</ul> |

### Configuration Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*External Configuration Store*](configuration_patterns/External_Configuration_Store.md) | | Externalize all application configuration properties to a centralized location. |

### Other Patterns
| Pattern Name | Diagram | Description |
|----|-------|----|
| [*Health Check API*](other_patterns/Health_Check_API.md) | | A service exposes a health check API endpoint which returns the health of the service. |
