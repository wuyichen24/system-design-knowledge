# Health Check API

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

## Solution
### Concepts
- A service exposes a health check API endpoint which returns the health of the service.
- A health check client periodically invokes the endpoint to check the health of the service instance.
- A health check client can be
   - Monitoring service
   - Service registry
   - Load balancer

### Implementation
- Basic measurements of the application's availability and performance:
   - The response code.
   - The content of response.
   - The response time (network latency + request processing time).

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Security | Protect the health check API from public access | <li>Eable authentication for accessing the health check API.<li>Expose the health check API on a different IP address.<li>Configure the health check API on a non-standard HTTP port. |

## When To Use

## References
- Book: [Chris R.(2018). Chapter 11 Developing production-ready services, *Microservices Patterns* (pp. 348-382). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Health Check API | https://microservices.io/patterns/observability/health-check-api.html](https://microservices.io/patterns/observability/health-check-api.html)
