# API Composition

- [**Motivation**](#motivation)
- [**Solution**](#solution)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation
- Need to retrieve data from multiple services in a microservice architecture.

## Solution
### Concepts
- Uses an API composer to retrieve data from multiple services and combine the results.
- An API composer can be a client or a service.
   - A service can a API gateway or a standalone service.
   
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
| Availability | One service may be unavailable during a query operation. | <li>The API composer to return previously cached data from the unavailable service.<li>The API composer to return incomplete data. |


