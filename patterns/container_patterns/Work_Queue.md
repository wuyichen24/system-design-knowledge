# Work Queue

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
![](../../diagrams/png/work_queue_small.png)
- A scalable master-worker framework for distributing millions of tasks to thousands of remote workers drawn from clusters, clouds, and grids.
- The framework consists of
   - **Master process**
      - Defines tasks.
      - Submits tasks to the queue.
   - **Worker process**
      - Arranges for data transfer.
      - Executes tasks
      - Returns the results
   - **Task**

### Implementation
#### Structure
![](../../diagrams/png/work_queue_structure.png)
- Master process
   - Work queue manager container
   - Work queue source container
- Worker process
   - Worker manager container: Integrates with the generic work queue framework.
   - Application implementation container: Implements application-specific logic.

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
- Thesis: [Brendan, D. (2016) *Design patterns for container-based distributed systems*. Google](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45406.pdf)
- Web Article: [Work Queue: A Scalable Master/Worker Framework | http://ccl.cse.nd.edu/software/workqueue/](http://ccl.cse.nd.edu/software/workqueue/)
- Web Article: [Work Queue User's Manual | https://cctools.readthedocs.io/en/latest/work_queue/](https://cctools.readthedocs.io/en/latest/work_queue/)
