# Redis

## Concepts
- **Architecture**
   - In-memory key-value store.

## Data structures
### Summary

| Data structure | Concept | Use cases | Operations |
|----|----|----|----|
| String | String value for storing string and number (integer or float) | <li>Cache<li>Counter<li>Distributed locks<li>Session store |
| List | Ordered collection of strings | <li>Message queue |
| Hash | Unordered hash table of key-value pairs | <li>Cache<li>Shopping carts |
| Set | Unordered collection of unique strings | <li>Intersections<li>Union |
| Sorted Set (Zset) | Score-ordered collection of unique strings | <li>Ranking (Leaderboard)<li>Sorting | 
| BitMap | List of 1 and 0 | <li>Daily login status |
| HyperLogLog |
| Geo |
| Stream |

### String

<img width="500" alt="Screen Shot 2023-10-24 at 2 45 15 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/6da7d16d-0015-4d34-be8b-2da6b980f8ea">

- **Concepts**
   - String value for storing string and number (integer or float).
- **Implementation**
   - SDS (Simple Dynamic Strings)

### List

<img width="548" alt="Screen Shot 2023-10-24 at 2 47 50 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/0e32899f-4676-4172-a3e9-28595a0412b7">

- **Concepts**
   - Ordered collection of strings.
- **Implementation**
   - quicklist
   - listpack

### Hash

<img width="500" alt="Screen Shot 2023-10-24 at 2 45 23 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/4e3ad5b6-70e4-4b92-8d18-b4b3d5f720ba">

- **Concepts**
   - Unordered hash table of key-value pairs
- **Implementation**
   - listpack

### Set

<img width="500" alt="Screen Shot 2023-10-24 at 2 53 43 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/339f2bbc-733c-4886-b8e6-37510e859445">

- **Concepts**
   - Unordered collection of unique strings
- **Implementation**

### Sorted Set

<img width="500" alt="Screen Shot 2023-10-24 at 2 58 44 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/3288c6cb-da50-4618-8a27-a82b17cbd7e3">

- **Concepts**
   - Score-ordered collection of unique strings

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
