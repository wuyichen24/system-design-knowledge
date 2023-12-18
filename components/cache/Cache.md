# Cache

- [**Types**](#types)
   - [Client-side caching](#client-side-caching)
   - [Server-side caching](#server-side-caching)
   - [Deployment](#deployment)
- [**Replacement And Invalidation**](#replacement-and-invalidation)
   - [Replacement](#replacement)
   - [Invalidation](#invalidation)
- [**Strategies**](#strategies)
   - [Overview](#overview)
   - [Read strategies](#read-strategies)
      - [Cache-aside](#cache-aside)
      - [Read-through](#read-through)
   - [Write strategies](#write-strategies)
      - [Write-around](#write-around)
      - [Write-through](#write-through)
      - [Write-back / Write-behind](#write-back--write-behind)
      - [Refresh-ahead](#refresh-ahead)
   - [Combinations](#combinations)
- [**Common Problems And Solutions**](#common-problems-and-solutions)
- [**Related Concepts**](#related-concepts)
- [**References**](#references)

## Types

![cache drawio](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/76e17651-5d23-4a77-9e92-1a3b804b1fb4)

### Client-side caching
| Type | Description |
|----|----|
| Browser caching | Web browsers on the client side can cache some web content. |
| App caching | Applications (mobile or PC) on the client side can cache some content. |

### Server-side caching
| Type | Description | Examples |
|----|----|----|
| CDN caching | CDNs can cache some static resources (web page, media file, etc.). | |
| Reverse proxy caching | Reverse proxy server can cache responses to clients. | | 
| Database caching | Databases include some level of caching. | <li>Buffer cache<li>Result cache<li>Query cache<li>Metatdata cache<li>Session cache |
| Page/Disk caching | A transparent cache for the pages originating from a secondary storage device (HDD or SSD). | |
| CPU caching | A hardware cache used by CPU to reduce the average cost to access data from the main memory. | <li>L1<li>L2<li>L3 |

### Deployment
| Type | Description | Examples | Diagram |
|----|----|----|----|
| In-Process cache | A cache is located within the application itself.<li>Limited capacity<li>No persistence | <li>Ehcache<li>Caffine<li>Google Guava Cache | ![in-process](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/b5e12ab0-de7f-48ac-9e52-c8120ff3e994) |
| Inter-process cache | A cache is located in a separate process on the same machine. | <li>Redis<li>Memcached<li>Tair<li>RocksDB<br><br>(In standalone mode) | ![inter-process](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/ad0be29a-2d13-4f07-990f-25de9c9c025a) |
| Remove cache | A cache is deployed on a separate machine from the application, usually composed of multiple machines deployed together. | <li>Redis<li>Memcached <br><br>(Deployed on remote servers) | ![remote](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/9f324b85-44c4-4bdf-8588-e9a62d7449bf) |

## Replacement And Invalidation
### Replacement
| Algorithm | Description |
|----|----|
| Least recently used (LRU) | Discards the least recently used items first. | 
| Most recently used (MRU) | Discards the most recently used items first. |
| First in first out (FIFO) | Like queue, the cache evicts the blocks in the order they were added, without any regard to how often or how many times they were accessed before. |
| Last in first out (LIFO) | Like stack, the cache evicts the block added most recently first without any regard to how often or how many times it was accessed before. |
| Random replacement (RR) | Randomly selects a candidate item and discards it to make space when necessary. |
| Least-frequently used (LFU) | Discards the least often used items first. |
| Allowlist policy | Data items in the allowlist will not be evicted from the cache (suitable for specific business scenarios with known hot keys). |

### Invalidation
| Strategy | Description | Diagram |
|----|----|----|
| Invalidation when modifying | Invalidate the data in cache when the application modifies the data in storage (widely used technique). | <img width="229" alt="Screenshot 2023-12-07 at 2 08 08 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/9b7bb6b0-0a89-4839-a83c-f769ebc1ffc5"> |
| Invalidation when reading | The application checks the validity of the data when it retrieves it from the cache. If the data is stale, it is read from the storage and written to the cache. | <img width="258" alt="Screenshot 2023-12-07 at 2 08 40 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/5b7924cc-81c9-47b7-b74c-1b01e5d5303c"> |
| Time-to-live (TTL) | The application sets a lifetime for the cached data, and the data is removed or marked as invalid once the TTL expires. | <img width="176" alt="Screenshot 2023-12-07 at 2 09 04 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/e69ebdf7-1494-413c-a229-f2ce43d761b5"> |

## Strategies
### Overview
| | Read strategies | Write strategies | Diagram |
|----|----|----|----|
| Cache-aside | <li>Cache-aside | <li>Write-around | <img width="220" alt="cache-aside" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/503e4192-2042-4e40-8210-ec5e0f88d0e6"> |
| Cache-as-SOR (inline cache) | <li>Read-through<li>Refresh-ahead | <li>Write-through<li>Write-back/Write-behind<li>Refresh-ahead | <img width="80" alt="cache-sor" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/006d692a-e878-493a-97d6-bcd0395941b9"> |

### Read strategies
#### Cache-aside

  <img width="700" alt="cache-aside" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/486969ab-4f25-4b01-a1b6-2d329cc8d666">

- **Concept**
   - The application directly communicates with both the cache and storage systems.
   - Applications take the responsibility of maintaining data in the cache.
   - The cache does not interact with database directly.
- **Steps**
   - The application requests a key from the cache.
   - If the key is found in the cache (cache hit)
       - The data is returned to the application.
   - If the key is not found in the cache (cache miss),
       - The application retrieves the data from storage and return it.
       - The application stores the data into the cache for future reads.
- **Pros**
   - The system can tolerate cache failures, as it can still read from the storage.
   - The data model in the cache can differ from that in the storage, providing flexibility for a variety of use cases.
- **Cons**
   - More complexity, because the application needs to manage both cache and storage.
   - Ensuring data consistency between cache and storage is challenging (Solution: TTL).
   - Each cache miss causes a noticeable delay.

#### Read-through

  <img width="500" alt="read-through" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/28edab21-53cf-4e28-8be7-d12a4ffd605b">

- **Concept**
   - The cache serves as an intermediary between the application and the storage system, handling all read requests.
   - Read-through is particularly suitable for read-heavy workloads
- **Steps**
   - The application requests a key from the cache.
   - If the key is found in the cache (cache hit)
       - The data is returned to the application.
   - If the key is not found in the cache (cache miss),
       - The cache retrieves the data from storage and save it.
       - The cache return the data to the application.
- **Pros**
   - Less complexity, because the application only need to access the cache.
- **Cons**
   - The cache will be a single point of failure.
   - The cache and storage systems must share the same data model, limiting the flexibility in handling different use cases. 

### Write strategies
#### Write-around

  <img width="300" alt="write-around" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/75de17cf-c71c-4f2e-af84-a8ab83e01ecc">

- **Concept**
   - The application writes data directly to the storage system, bypassing the cache.
- **Steps**
   - The application writes data directly to the storage system.
   - The application invalids the data in cache.
- **Pros**
   - Less complexity
   - The system can tolerate cache failures, as it can still write to the storage.
- **Cons**
   - If data is written once and then read again, the storage system will be accessed twice, potentially causing performance issues.
   - When data is frequently updated and read, the storage system is accessed multiple times, rendering cache operations less effective.

#### Write-through

  <img width="500" alt="write-through" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/c0566596-798e-4d65-8831-dd91108861a3">

- **Concept**
   - The cache serves as an intermediary between the application and the storage system, handling all write requests.
   - After application writes data to cache, cache **synchronously** writes the same data to database.
- **Steps**
   - The application writes to the cache endpoints.
   - The cache writes the data to the storage system.
   - The cache updates itself if the write operation is successful.
- **Pros**
   - Less complexity, because the application only need to access the cache.
- **Cons**
   - Introduces additional write latency, as the operation must be performed on both the cache and storage systems.
   - If data is successfully written to the storage but not updated in the cache, the cached data becomes stale (Solution: The cache can first invalidate the key, then request to write the data to the storage).

#### Write-back / Write-behind

  <img width="500" alt="write-back" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/899b8103-1441-4244-b9bf-ee9afc2d697d">

- **Concept**
   - The cache serves as an intermediary between the application and the storage system, handling all write requests.
   - After application writes data to cache, cache **asynchronously** writes the same data to database (When satisfy a certain criteria).
- **Steps**
   - The application writes data to the cache, and the data is persisted in the cache.
   - The cache periodically writes updated records to the storage system in batches.
- **Pros**
   - The strategy offers lower write latency compared to write-through, resulting in better performance for write operations.
   - The strategy reduces the overall number of writes to the storage system and provides resilience to storage failures.
- **Cons**
   - There may be temporary data inconsistency between the cache and storage systems.
   - If the cache fails before writing data to the storage, the latest updated records may be lost (Solution: Cache system can persist write operations on the cache side. When the cache restarts, it can replay the unfinished operations to recover the cache and write data to the storage system).

#### Refresh-ahead

  <img width="100" alt="refresh-ahead" src="https://github.com/wuyichen24/system-design-knowledge/blob/master/diagrams/png/refresh_ahead_small.png">

- **Concept**
   - Cache automatically and asynchronously reloads (refreshs) any recently accessed cache entry from database before its expiration.
- **Steps**
- **Pros**
   - Refresh-ahead offers reduced latency compared to read-through.
   - Refresh-ahead is especially useful if objects are being accessed by a large number of users.
- **Cons**

### Combinations
- Cache-aside + Write-around (Common)
- Read-through + Write-through (Common)
   - Examples: DynamoDB Accelerator (DAX)
- Read-through + Write-back (Common)
- Read-through + Write-around
- Cache-aside + Write-through

## Common Problems And Solutions
| Problem | Scenario | Cause | Solutions |
|---|---|---|---|
| Cache avalanche | <li>Lots of cached data expire at the same time<li>The cache instance is down | Suddenly all queries hit the database and cause the database to crash down. | <li>Use distributed cache cluster (Redis cluster) to achieve high availability.<li>Use circuit breaker and rate limiter to avoid the system crash down by high load.<li>Use the combination of in-process cache and distributed cache.<li>Use staggered expiration by combining a base time-to-live (TTL) value with a random delta so that they will not expire at the same time. |
| Cache stampede (Thundering herd) | A sudden influx of requests overwhelms the system | <li>Cache misses on popular items<li>A sudden spike in user traffic<li>Service restarts after maintenance | |
| Cache penetration | Lots of queries for the data which doesn't exist in the database. | For those queries, database doesn't have the data and cache doesn't have too. But those queries will eventually the hit the database. If the amount of the queries is very large, it would cause the database to crash down. | <li>Let the cache still store the null result for the query (with short expiration time).<li>Use Bloom filter to filter out some queries which cannot have data in the database at all. |
| Cache breakdown | A very hot data entry expires in the cache. | Suddenly lots of queries for that that very hot data entry will hit the database eventually and cause the database to crash down. | <li>Add a lock on that data entry and the lock only allows a very limited amount of queries to search the data entry from the database and update the cache. After releasing the lock, other queries can get that data entry from the cache directly.<li>Asynchronously update that data entry from database so that the data entry will never expire.<li>Don't set the expiration time on that data entry if it will never be changed. |

## Related Concepts
- **Distributed Cache**
   - A distributed cache may span multiple servers so that it can grow in size and in transactional capacity.
- **Cache Coherence**
   - The uniformity of shared resource data that is stored in multiple local caches.
   - If one client updates the memory block, another client could be left with an invalid cache of memory without any notification of the change.

     <img width="304" alt="Cache_Coherency_Generic" src="https://user-images.githubusercontent.com/8989447/118202935-310bbe00-b418-11eb-9fbb-547fe155e05b.png">
- **Cold Cache, Warm Cache and Cache Warming**
   - Cold Cache: The cache has no data in it and cannot provide cache hits.
   - Warm Cache: The cache has data it it can can provide cache hits.
   - Cache Warming: Manually pre-fill a cold cache with data so that it can provide cache hits when receiving real requests.
   - Cache Warmer: The tools for warning caches.
      - Examples: Magento, Wordpress.
   
## References
- https://docs.microsoft.com/en-us/azure/architecture/best-practices/caching
- https://www.pixelstech.net/article/1586522853-What-is-cache-penetration-cache-breakdown-and-cache-avalanche
- https://github.com/doocs/advanced-java/blob/main/docs/high-concurrency/redis-caching-avalanche-and-caching-penetration.md
- https://github.com/dunwu/blog/blob/master/source/_posts/theory/cache.md
- https://docs.oracle.com/cd/E15357_01/coh.360/e15723/cache_rtwtwbra.htm#COHDG198
