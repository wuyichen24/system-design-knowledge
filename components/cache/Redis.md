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
| Geospatial | | <li>Store and query coordinates |
| Stream | Append only log | <li>Event sourcing<li>Sensor monitoring |

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

## Use cases
- **Distributed locks**

  <img width="478" alt="Screen Shot 2023-10-24 at 3 14 33 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/3ddd7406-db3d-4744-b830-c2812be82633">

- **Sessions store**
  
  <img width="426" alt="Screen Shot 2023-10-24 at 3 13 12 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/50415eda-1981-487c-a0b2-722345ae80d8">

- **Rate limiter**

  <img width="500" alt="Screen Shot 2023-10-24 at 3 15 12 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/bbc51e03-6523-45d3-a762-6038008ff3cb">

- **Ranking**

  <img width="443" alt="Screen Shot 2023-10-24 at 3 16 13 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/4611539a-3e21-403d-a7ca-86232cc86fbc">

- **Message queue**

  <img width="500" alt="6f31ddd1-38b6-45aa-9d16-2fe92f6600ba_1165x1449" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/24122af9-fa96-4eab-8d8e-b7e491fa6f16">

## Performance


