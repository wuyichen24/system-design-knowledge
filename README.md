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
| Ambassador |  | Place an ambassador module between the main application and the external system for simplifying the view of the external system. |
| Adapter |  | Place an ambassador module between the main application and the external system for standardizing the view of the internal application. |
| Sidecar |  | Place an independent sidecar module next to the main application for providing supportive works to the main application. |
