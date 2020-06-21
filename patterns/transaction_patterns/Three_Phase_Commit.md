# Three-Phase Commit (3PC)

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
- 2PC cannot dependably recover from a failure of both the coordinator and a participant during the commit phase.

## Solution
### Concepts
- Add a new phase (prepared to commit phase) in the middle of the original 2 phases in 2PC.
- Provide a dependable recovery solution from a participant failure or both coordinator and participant failure during commit phase.

### Implementation

## Pros & Cons
### Pros
- It is a non-blocking protocol.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
