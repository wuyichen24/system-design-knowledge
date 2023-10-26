# Scalability

- [**Concepts**](#concepts)
- [**Types of scaling**](#types-of-scaling)
   - [Limitations for vertical scaling](#limitations-for-vertical-scaling)
- [**How to achieve high scalability**](#how-to-achieve-high-scalability)

## Concepts
- System can handle more load or increase performance by adding more resources.

## Types of scaling
- **Vertical scaling (Scale up)**
   - Add more resources (CPU, memory, etc.) into a single node.
- **Horizontal scaling (Scale out)**
   - Add more nodes into a system.

### Limitations for vertical scaling
- Vertical scaling has a hard limit (It is impossible to add unlimited CPU and memory to a single server).
- Vertical scaling doesn't have failover and redundancy.
- The overall cost of vertical scaling is high.

## How to achieve high scalability
- *Loose coupling*
   - Decouple different components of the system so they can be scaled independently.
- *Horizontal scaling*
   - Distribute the load across multiple servers or nodes.
- *Asynchronous processing*
   - Offload time-consuming and resource-intensive tasks to background processes or worker queues.
- *Caching*
   - Implement caching strategies to reduce the load on the database or other data sources.
- *Database scaling*
   - Employ database scaling techniques, such as sharding, replication, and partitioning, to distribute data across multiple database servers.
   - Use database clustering solutions to manage high availability and failover.
- *Auto-scaling*
   - Set up auto-scaling mechanisms that automatically adjust the number of servers based on metrics like CPU usage, request rate, or other performance indicators.
- *Considering scalability from the start*
   - Design your system with scalability in mind from the beginning.
- *Load testing and profiling*
   - Continuously perform load testing to identify performance bottlenecks and areas that need optimization.
   - Use profiling tools to analyze and fine-tune the performance of critical components.
