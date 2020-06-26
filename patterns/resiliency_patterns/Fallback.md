# Fallback

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
- When a request to a service fails, return an alternative response to the request.

### Implementation
#### Fallback Logic
- Basic ideas
   - Fallback logic typically does little or no processing, and return value.
   - Fallback logic must have little chance of failing.
- Approaches
   - Return previous cached value.
   
## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
- Web Article: [Fallback pattern | https://badia-kharroubi.gitbooks.io/microservices-architecture/patterns/communication-patterns/fallback-pattern.html](https://badia-kharroubi.gitbooks.io/microservices-architecture/patterns/communication-patterns/fallback-pattern.html)
- Web Article: [Resilience design patterns: retry, fallback, timeout, circuit breaker | https://blog.codecentric.de/en/2019/06/resilience-design-patterns-retry-fallback-timeout-circuit-breaker/](https://blog.codecentric.de/en/2019/06/resilience-design-patterns-retry-fallback-timeout-circuit-breaker/)
