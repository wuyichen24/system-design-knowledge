# Leader Election

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
      - [Goal of election algorithm](#goal-of-election-algorithm)
      - [Common election algorithms](#common-election-algorithms)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation

## Solution
### Concepts
![](../../diagrams/png/leader_election_small.png)
- Elect one container as the leader for coordinating and monitoring the other containers.

### Implementation
#### Goal of election algorithm
- Elect only one instance as leader based on the best attribute value.
- Let other instances know who is the leader when the election is finished.
- The election should be initiated to re-elect a new leader when the original leader is unavailable.

#### Common election algorithms
- Ring Algorithm
- Bully Algorithm

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
- Thesis: [Brendan, D. (2016) *Design patterns for container-based distributed systems*. Google](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45406.pdf)
