# Bulkhead

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
- Isolate the misbehaving service and avoid to take down the entire application by exhausting all the resources.

### Implementation
#### Partitioning Strategies
- Types
   - Partition service instances: Ensure that resources used to run one service instance don't affect the resources used to run another service instance.
- Technologies
   - Partition clients: Ensure that resources used to call one service don't affect the resources used to call another service.
- Technologies
   - For partitioning services, consider to use:
      - Virtual machines
      - Containers
      - Processes
   - For partitioning clients, consider to use
      - Processes
      - Thread pools
      - Semaphores

## Pros & Cons
### Pros
- Preserve some functionality in the event of a service failure.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
- Web Article: [Bulkhead pattern | https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead](https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead)
