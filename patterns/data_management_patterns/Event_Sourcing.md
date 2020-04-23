# Event Sourcing

## Motivation

## Solution
### Concepts
- Persists an entity as a sequence of events.
- Each event represents a state change of the entity that has happened.
- The current state of an entity will be reconstructed by replaying the events.
- Events are persisted in an event store, which is a database or table of events.

### Implementation
### Add-ons
- **Snapshot**
   - Concepts
      - Periodically persist a snapshot of the entity’s state.
      - The current state of an entity will be reconstructed by loading the most recent snapshot and only the fewer events that have occurred since the snapshot was created.

## Pros & Cons
### Pros
- Reliably publishes domain events.
- Preserves the history of entities.
   - Provides an audit log of entities.
- Avoids the object‑relational impedance mismatch problem.


### Cons
- Has a learning curve.
- Increases the complexity of an application.
- Deleting data is tricky.
- Evolving events can be tricky.
- Querying the event store is challenging.

## Consideration
## When To Use
## References
- Chris R.(2018). Chapter 6 Developing business logic with event sourcing, *Microservices Patterns*. Manning Publications
