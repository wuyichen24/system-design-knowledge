# Consistency

## Consistency model categories
- **Strong consistency**
   - Make a system appear as if there is only a single copy of the data.
   - Every read from the system is the most recent, up-to-date value, and doesn’t come from a stale cache or replica.
- **Weak consistency**
   - Any consistency model weaker than sequential consistency.
   - Subsequent read operations may not see the most recent value.

## Common models
### Strict consistency

### Sequential consistency

### Causal consistency
- Concepts
   - Operations are in order: Which operation happened before which other operation (cause comes before effect).
   - Causality defines a partial order, not a total order.

### Eventual consistency 
