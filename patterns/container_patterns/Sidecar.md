# Sidecar

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
- Place an independent sidecar container next to the main container for providing supportive works to the main container.

### Implementation
- The main container and the sidecar container are on the same machine so that they can share a local disk volume.

## Pros & Cons
### Pros
- Several benefits to using separate containers:
   - Different containers can be allocated different quota of system resources
   - Divide responsibility for their development between two separate programming teams and allows them to be tested independently as well as together.
   - Sidecar containers can be reused for pairing with numerous different main containers.
   - One failing container may not affect the functionalities of other containers.
   - Different containers can be upgraded or downgraded independently.
   
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
