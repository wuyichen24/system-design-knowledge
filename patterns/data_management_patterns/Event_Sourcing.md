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
## Consideration
## When To Use
## References
