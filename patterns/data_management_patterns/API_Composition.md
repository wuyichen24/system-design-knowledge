# API Composition

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation
- Problem of retrieving data from multiple services in a microservice architecture.

## Solution
### Concepts
- Uses an API composer to retrieve data from multiple services and combine the results.
- An API composer can be a client or a service.
   - A service can a API gateway or a standalone service.
   
### Implementation
- Decide who plays the role of the API composer
  | Decision | Situation |
  |----|----|
  | Not a client | <ul><li>Clients that are outside of the firewall and access services via a slower network.</ul> |
  | A standalone service | <ul><li>The data combination logic is complex. <li>The query operation is also used internally by other services.</ul> |
  | API gateway | <ul><li>The data combination logic is simple. <li>The query operation is for external calls.</ul> |
   
## Pros & Cons
### Pros
- Simple and useful.

### Cons
- Increased overhead (larger network latency and buring more system resources).
- Risk of reduced availability (One service may be unavailable during the query operation).
- A query operation may return inconsistent data.

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Scalability | The data needs to be combined can be large. | |
| Complexity | The data combination logic can be complex. | <ul><li>Consider to put the API composer as a standalone service (The logic is too complex to be part of an API gateway).</ul> |
| Availability | One service may be unavailable during a query operation. | <ul><li>Consider to let the API composer return previously cached data from the unavailable service.<li>Consider to let the API composer return incomplete data.</ul> |
| Performance | The latency can be increased by calling multiple services. | <ul><li>Consider to let the API composer call multiple services in parallel if there are no dependencies between the service calls (Sometime it may be impossible, an API composer needs the result of one service in order to invoke another service).</ul> |

## When To Use
## References
- Book: [Chris R.(2018). Chapter 7 Implementing queries in a microservice architecture, *Microservices Patterns* (pp. 220-252). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: API Composition | https://microservices.io/patterns/data/api-composition.html](https://microservices.io/patterns/data/api-composition.html)
