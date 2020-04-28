# Command Query Responsibility Segregation (CQRS)

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation

## Solution
### Concepts
- Separate a service into two parts: the command side and the query side.
- The command side modules and data model implement create, update, and delete operations (CUD).
- The query-side modules and data model implement queries (R).
- The query side keeps its data model synchronized with the command-side data model by subscribing to the events published by - the command side.

## Pros & Cons
### Pros
- Improve the efficiency of query operations. 
- Simplify the query model and the command model.
- Supports multiple denormalized views of data.

### Cons
- Increased complexity.
- Dealing with the replication lag  between the command-side and the query-side.

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Concurrency | Multiple concurrent updates to the same database record. | <li>Consider to use pessimistic or optimistic locking. |
| Idempotency | An event handler may be invoked with the same event more than once. | <li>Consider to record the IDs of events that it has processed in the view datastore. |
| Data consistency | A client that updates the command side and then immediately executes a query might not see its own update. | <li>Consider to use this approach to let the client detect an inconsistency: A command-side operation returns a token containing the ID of the published event to the client. The client then passes the token to a query operation, which returns an error if the view hasn’t been updated by that event. |

## When To Use

## References
- Book: [Chris R.(2018). Chapter 7 Implementing queries in a microservice architecture, *Microservices Patterns* (pp. 220-252). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Command Query Responsibility Segregation (CQRS) | https://microservices.io/patterns/data/cqrs.html](https://microservices.io/patterns/data/cqrs.html)
