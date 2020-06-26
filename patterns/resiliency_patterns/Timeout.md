# Timeout

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
- Set a limited period of time to wait for a response.

### Implementation
#### Advice
- Timeout often works with retry, circuit breaker and fallback patterns.

## Pros & Cons
### Pros
- Avoid waiting forever for a response that might never come.
- Unbounded result sets by preventing the client from processing the entire result set.
- Avoid cascading failures.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
- Book: [Michael N.(2018). Chapter 5 Stability Patterns, *Release It!* (pp. 91-128). Pragmatic Bookshelf](https://pragprog.com/titles/mnee2/)
