# Redis

## Concepts
- **Architecture**
   - In-memory key-value store

## Data structures
### Summary

| Data structure | Concept | Use cases | Operations |
|----|----|----|----|
| String | 
| List |
| Set |
| Hash |
| Zset |
| BitMap |
| HyperLogLog |
| Geo |
| Stream |



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
