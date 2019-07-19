# distributed-system-design-pattern

## Overview
Collect modern distributed system design patterns.

## Categories
- **Architecture Pattern**
   - Anti-Corruption Layer
   - Backends for Frontends (BFF)
- **Cache Pattern**
   - Cache-Aside
   - Cache-As-SOR
      - Read-Through
      - Write-Through
      - Write-Behind
      - Refresh-Ahead
- **Data Management Patterns**
   - Command and Query Responsibility Segregation (CQRS)
- **Message Queue Patterns**
   - Competing Consumer
   - Priority Queue
- **Container Patterns**
   - Single-node, multi-container patterns
      - Sidecar
      - Ambassador
      - Adapter
   - Multi-node patterns
      - Leader Election
      - Work Queue
      - Scatter/Gather
- **Resiliency Patterns**
   - Circuit Breaker
   - Fallback
   - Bulkhead
   - Retry
- **Configuration Patterns**
   - External Configuration Store
   - Runtime Reconfiguration
- **Security Patterns**
   - Valet Key

## Brief Introduction
### Cache Patterns
| Category Name | Diagram | Description | Patterns |
| ---- | ---- | ---- | ---- |
| Cache-Aside |  | Application interacts and manages both cache and database. |  |
| Cache-As-SOR |  | Application only interact and manage cache. | <ul><li>Read-Through<li>Write-Through<li>Write-Behind<li>Refresh-Ahead</ul> |

| Pattern Name | Diagram | Description | 

### Container Patterns

| Pattern Name | Diagram | Description |
|----|-------|----|
| *Ambassador* | ![](./diagrams/png/ambassador_small.png) | <ul><li>Place an ambassador container between the main application container and the external system for simplifying the view of the external system.</ul> |
| *Adapter* | ![](./diagrams/png/adapter_small.png) | <ul><li>Place an adapter container between the main application container and the external system for standardizing the view of the internal application.</ul> |
| *Sidecar* | ![](./diagrams/png/sidecar_small.png) | <ul><li>Place an independent sidecar container next to the main application container for providing supportive works to the main application container.</ul> |
| *Leader Election* | ![](./diagrams/png/leader_election_small.png) | <ul><li>Elect one instance as the leader for coordinating and monitoring the other instances.</ul> |
| *Work Queue* | ![](./diagrams/png/work_queue_small.png) | <ul><li>Group a work queue manager container and a work queue source container as a coordinator for managing the work queue and dispatch work items to workers.<li>Each worker consists of a worker manager container (for integrating with the generic work queue framework) and an application implementation container (for application-specific logic).</ul> |
| *Scatter/Gather* | ![](./diagrams/png/scatter_gather_small.png) | <ul><li>The root node scatters out the original request to a group of servers to perform a set of tasks in parallel.<li>The root node gathers the partial data from each server and return a single response to the original request.</ul>

### Resiliency Patterns

| Pattern Name | Diagram | Description |
| ---- | ------ | ---- |
| *Circuit Breaker* |  | Prevent an application from performing an operation that is likely to fail based on a certain criteria. |
| *Bulkhead* |  | Isolate the misbehaving service and avoid to take down the entire application by exhausting all the resources. |
| *Fallback* |  | When a service call fails, execute the alternative action. |
| *Retry* |  | Retry a failed operation. |
