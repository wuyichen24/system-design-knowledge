# Saga

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
- A sequence of local transactions.
   - Each local transaction updates data within a single service.
   - A service publishes an asynchronous message when a local transaction completes. The message triggers the local transaction in the next service.
- Use compensating transactions to rollback changes
   - Each local transaction has a compensating transaction to undo the change.
   - If one transaction fails, the saga needs to execute the compensating transaction of preceding transactions in reverse order.

### Implementation
#### Types of Saga
- Choreography
- Orchestration

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
