# Cache

- [**Types**](#types)
   - [Client-side caching](#client-side-caching)
   - [Server-side caching](#server-side-caching)
- [**Replacement Policies**](#replacement-policies)
- [**Strategies**](#strategies)
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

## Deployment
| Type | Description | Examples | Diagram |
|----|----|----|----|
| In-Process cache | A cache is located within the application itself.<li>Limited capacity<li>No persistence | <li>Ehcache<li>Caffine<li>Google Guava Cache | ![in-process](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/b5e12ab0-de7f-48ac-9e52-c8120ff3e994) |
| Inter-process cache | A cache is located in a separate process on the same machine. | <li>Redis<li>Memcached<li>Tair<li>RocksDB<br><br>(In standalone mode) | ![inter-process](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/ad0be29a-2d13-4f07-990f-25de9c9c025a) |
| Remove cache | A cache is deployed on a separate machine from the application, usually composed of multiple machines deployed together. | <li>Redis<li>Memcached <br><br>(Deployed on remote servers) | ![remote](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/9f324b85-44c4-4bdf-8588-e9a62d7449bf) |

## Replacement And Invalidation
| Algorithm | Description |
|----|----|
| Least recently used (LRU) | Discards the least recently used items first. | 
| Most recently used (MRU) | Discards the most recently used items first. |
| First in first out (FIFO) | Like queue, the cache evicts the blocks in the order they were added, without any regard to how often or how many times they were accessed before. |
| Last in first out (LIFO) | Like stack, the cache evicts the block added most recently first without any regard to how often or how many times it was accessed before. |
| Random replacement (RR) | Randomly selects a candidate item and discards it to make space when necessary. |
| Least-frequently used (LFU) | Discards the least often used items first. |

## Strategies
- [**Cache-Aside**](../../patterns/cache_patterns/Cache_Aside.md)
- [**Cache-As-SOR**](../../patterns/cache_patterns/Cache_As_Sor.md)
   - Read-Through
   - Write-Through
   - Write-Behind
   - Refresh-Ahead

## Common Problems And Solutions
| Problem | Scenario | Cause | Solutions |
|---|---|---|---|
| Cache avalanche | Lots of cached data expire at the same time or the cache instance is down. | Suddenly all queries hit the database and cause the database to crash down. | <li>Use distributed cache cluster (Redis cluster) to achieve high availability.<li>Use Hystrix's circuit breaker and rate limit to avoid the database crash down by high load.<li>Use the combination of in-process cache and distributed cache.<li>Adjust the expiration time for different keys so that they will not expire at the same time. |
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
