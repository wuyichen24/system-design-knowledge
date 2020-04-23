# Event Sourcing

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
   - [Add-ons](#add-ons)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)
   

## Motivation
- Only store the current state of an entity is not enough.

## Solution
### Concepts
- Persists an entity as a sequence of events.
- Each event represents a state change of the entity that has happened.
- The current state of an entity will be reconstructed by replaying the events.
- Events are persisted in an event store, which is a database or table of events.

### Implementation
- A simple template of of the table storing events
  | Column | Description |
  |----|----|
  | Event ID | The identifier of the event. |
  | Event Type | The type of the event. |
  | Entity Type | The type of the the entity. |
  | Entity ID | The identifer of the entity. |
  | Event Data | The serialized data, such as JSON. |

### Add-ons
- **Snapshot**
   - Problem
      - An entity may have a large number of events and it is inefficient to load those events.
   - Concepts
      - Periodically persist a snapshot of the entity’s state.
      - The current state of an entity will be reconstructed by loading the most recent snapshot and only the fewer events that have occurred since the snapshot was created.
- **Optimistic locking**
   - Problem
      - Two or more requests to simultaneously update the same entity.
   - Concepts
      - Uses a version column to detect whether an aggregate has changed since it was read.
      - The version will be incremented by 1 whenever the entity is updated.
      - Each update statement will only succeed if the version is unchanged from when the application read the entity.
 
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
- Data storage
   - It takes a large amount of space to store every event.
- Performance
   - It takes a long time to replay all the events for reconstructing the current state of an entity.
   - Consider to use snapshots to improve performance.
   - Consider to use cache (in-memory key-value store) to improve performance.

## When To Use
## References
- Book: [Chris R.(2018). Chapter 6 Developing business logic with event sourcing, *Microservices Patterns* (pp. 183-219). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Event sourcing https://microservices.io/patterns/data/event-sourcing.html](https://microservices.io/patterns/data/event-sourcing.html)
- Web Video: [Event Sourcing for Enterprise, 2019 (updated) https://www.youtube.com/watch?v=xQ5YkMBPe0o](https://www.youtube.com/watch?v=xQ5YkMBPe0o)
