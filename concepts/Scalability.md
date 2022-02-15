# Scalability

- [Concepts](#concepts)
- [Types](#types)
- [Limitations for vertical scaling](#limitations-for-vertical-scaling)

## Concepts
- System can handle more load or increase performance by adding more resources.

## Types
- **Vertical scaling (Scale up)**
   - Add more resources (CPU, memory, etc.) into a single node.
- **Horizontal scaling (Scale out)**
   - Add more nodes into a system.

## Limitations for vertical scaling
- Vertical scaling has a hard limit (It is impossible to add unlimited CPU and memory to a single server).
- Vertical scaling doesn't have failover and redundancy.
- The overall cost of vertical scaling is high.

## Solutions for enhancing scalability
- **Loose coupling**
   - Decouple different components of the system so they can be scaled independently.

## Related concepts
- **Autoscaling (Auto scaling or Auto-scaling)**
   - Dynamically adjusts the amount of computational resources based on the load on the server farm.
