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
![](../../diagrams/png/sidecar_small.png)
- Place an independent sidecar container next to the main application container for providing supportive works to the main application container.

### Implementation
- The main container and the sidecar container are on the same machine so that they can share resources:
   - File system
   - Hostname
   - Network
   - More
- Common supportive functionalities for a sidecar container:
   - Logging
   - Monitoring

## Pros & Cons
### Pros
- Several benefits to using separate containers:
   - Different containers can be allocated different quota of system resources
   - Divide responsibility for their development between two separate programming teams and allows them to be tested independently as well as together.
   - Sidecar containers can be reused for pairing with numerous different main containers.
   - One failing container may not affect the functionalities of other containers.
   - Different containers can be upgraded or downgraded independently.
- No significant latency when communicating between main containers and sidecar containers.
   
### Cons

## Consideration
- Before putting functionality into a sidecar container, consider whether it would be better to implement the functionality as 
  - A separate service.
  - A traditional daemon.
  - A traditional extension, like library.

## When To Use

## References
- Thesis: [Brendan, D. (2016) *Design patterns for container-based distributed systems*. Google](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45406.pdf)
- Web Article: [Sidecar pattern | https://docs.microsoft.com/en-us/azure/architecture/patterns/sidecar](https://docs.microsoft.com/en-us/azure/architecture/patterns/sidecar)
