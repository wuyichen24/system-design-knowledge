# Circuit Breaker

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
- Detects failures and prevents a failure from constantly recurring.

### Implementation
- Basic mechanism
   - Adds circuit breaker in the middle of a client and service.
   - Circuit breaker monitors failures by tracking the number of failures.
   - Once the error rate exceeds some threshold, the circuit breaker will trip so that all further calls fail immediately.
- Circuit breaker retains a state over a series of calls, there are 3 common value:
   - Closed
   - Open
   - Half open
- Self-resetting: Needs an external intervention to reset the circuit breaker when things are well again.

## Pros & Cons
### Pros
- Prevents a failure from constantly recurring.
### Cons
- Negatively affects on performance.

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
