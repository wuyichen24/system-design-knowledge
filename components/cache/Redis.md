# Redis

## Concepts
- **Architecture**
   - In-memory key-value store.

## Data structures
### Summary

| Data structure | Concept | Use cases | Operations |
|----|----|----|----|
| String | String value for storing string and number (integer or float) | <li>Cache<li>Counter<li>Distributed locks<li>Sessions |
| List | A list of strings | <li>Message queue |
| Hash |
| Set |
| Sorted Set |
| BitMap |
| HyperLogLog |
| Geo |
| Stream |

## String
- Concepts
- Implementation
   - SDS (Simple Dynamic Strings)

## List
- Concepts
- Implementation
   - Before Redis 7.0
      - ZipList
   - After Redis 7.0
      - quicklist
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
