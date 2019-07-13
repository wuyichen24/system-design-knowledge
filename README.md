# distributed-system-design-pattern

## Overview
Collect modern distributed system design patterns.

## Categories
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
### Container Patterns

| Pattern Name | Diagram | Description |
|----|----|----|
| *Ambassador* | ![](./diagrams/png/ambassador_small.png) | Place an ambassador container between the main application container and the external system for simplifying the view of the external system. |
| *Adapter* | ![](./diagrams/png/adapter_small.png) | Place an adapter container between the main application container and the external system for standardizing the view of the internal application. |
| *Sidecar* | ![](./diagrams/png/sidecar_small.png) | Place an independent sidecar container next to the main application container for providing supportive works to the main application container. |
| *Leader Election* |  | Elect one instance as the leader for coordinating and monitoring the other instances. |
| *Work Queue* |  | <ul><li>Group a work queue manager container and a work queue source container as a coordinator for managing the work queue and dispatch work items to workers.<li>Each worker consists of a worker manager container (for integrating with the generic work queue framework) and an application implementation container (for application-specific logic).</ul> |
