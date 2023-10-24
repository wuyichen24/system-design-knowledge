# Redis

## Concepts
- **Architecture**
   - In-memory key-value store.

## Data structures
### Summary

| Data structure | Concept | Use cases | Operations |
|----|----|----|----|
| String | String value for storing string and number (integer or float) | <li>Cache<li>Counter<li>Distributed locks<li>Sessions |
| List | Ordered collection of strings | <li>Message queue |
| Hash | Unordered hash table of key-value pairs | <li>Cache<li>Shopping carts |
| Set | Unordered collection of unique strings
| Sorted Set |
| BitMap |
| HyperLogLog |
| Geo |
| Stream |

### String

<img width="500" alt="Screen Shot 2023-10-24 at 2 45 15 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/6da7d16d-0015-4d34-be8b-2da6b980f8ea">

- Concepts
   - String value for storing string and number (integer or float).
- Implementation
   - SDS (Simple Dynamic Strings)

### List
- Concepts
   - Ordered collection of strings.
- Implementatio
   - quicklist
   - listpack

### Hash

<img width="500" alt="Screen Shot 2023-10-24 at 2 45 23 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/4e3ad5b6-70e4-4b92-8d18-b4b3d5f720ba">

- Concepts
   - Unordered hash table of key-value pairs
- Implementation
   - listpack

## Data persistence options
- **AOF (Append Only File)**
   - AOF works like a commit log, recording each write operation to Redis.
   - When the server is restarted, the write operations can be replayed and the dataset can be reconstructed.
- **RDB (Redis Database)**
   - RDB performs point-in-time snapshots at a predefined interval.
- **AOF and RDB**
   - This persistence method combines the advantages of both AOF and RDB.
- **No persistence**
   - Persistence can be entirely disabled in Redis.

## Performance
