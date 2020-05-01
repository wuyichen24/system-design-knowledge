# Command Query Responsibility Segregation (CQRS)

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
      - [Database](#database)
      - [Synchronization](#synchronization)
      - [CQRS + Event Sourcing](#cqrs--event-sourcing)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation
- Read and write workloads are often asymmetrical, with very different performance and scale requirements.

## Solution
### Concepts
- Separate a service into two parts: the command side and the query side.
- The command side modules and data model implement create, update, and delete operations (CUD).
- The query-side modules and data model implement queries (R).
- The query side keeps its data model synchronized with the command-side data model.

### Implementation
#### Database
- Command-side database and query-side database can use one database or separated databases.
   - One database.
      - ![](../../diagrams/png/command_query_responsibility_segregation_small_1db.png)
   - Separated database.
      - ![](../../diagrams/png/command_query_responsibility_segregation_small_2db.png)
- If separate command-side and query-side databases are used:
   - They can use different types of database. For example, one database might be SQL, another one might be No-SQL.
   - They can use different data schema. For example, the schema of query-side database can be optimized for queries.
   - They can be scaled differently.
   
#### Synchronization
- If separate command-side and query-side databases are used, they must be kept in sync.
- There are several options for synchronization:
   - **By event**: The query-side subscribes to the events published by the command-side.
      - ![](../../diagrams/png/command_query_responsibility_segregation_small_event.png)
   - **By read-only replica**: The query-side uses the read-only replica of the command-side database.
      - ![](../../diagrams/png/command_query_responsibility_segregation_small_replica.png)
      
#### CQRS + Event Sourcing
- CQRS is often used along with Event Sourcing.
- The command-side uses event sourcing. 
   - The command-side persists application state by storing sequence of events in the event store. 
   - The event store is the official source of information.
- The same event in the command-side can be used to notify other components, in particular, to notify the query-side.

## Pros & Cons
### Pros
- The command-side and the query-side can be designed and tuned differently.
   - The command-side and the query-side may have difference requirements in performance, scalability (workload), security, etc.
- Simplify the command-side and the query-side in design and implementation.
- Supports multiple denormalized views of data.

### Cons
- Increased complexity.
- Dealing with the replication lag  between the command-side and the query-side.

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Concurrency | Multiple concurrent updates to the same database record. | <li>Consider to use pessimistic or optimistic locking. |
| Messaging | If the query-side keep synchronized with the command-side by events, the event handler in the query-side must be able to handle duplicated events and event message failures. | <li>Consider to record the IDs of events that it has processed in the query-side database. |
| Eventual consistency | A client that updates the command side and then immediately executes a query might not see its own update. The client needs to detect the query data is stale or not. | <li>Consider to use this approach: A command-side operation returns a token containing the ID of the published event to the client. The client then passes the token to a query operation, which returns an error if the view hasn’t been updated by that event. |

## When To Use

## References
- Book: [Chris R.(2018). Chapter 7 Implementing queries in a microservice architecture, *Microservices Patterns* (pp. 220-252). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Command Query Responsibility Segregation (CQRS) | https://microservices.io/patterns/data/cqrs.html](https://microservices.io/patterns/data/cqrs.html)
