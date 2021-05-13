# Cache-Aside

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation
- Some caching systems don't provide read-through and write-through/write-behind operations.

## Solution
### Concepts
![](../../diagrams/png/cache_aside_small.png)
- Applications take the responsibility of using the cache to maintain data.
- The cache does not interact with database directly.

### Implementation
#### Read Operation
- Check the requested record is held in the cache or not:
   - If the requested record is held in the cache:
      - Return the record directly.
   - If the requested record is not in the cache:
      - Read the record from the database and return it.
      - Store the copy of the record in the cache.
      
#### Write Operation
- Write the record into the database.
- Invalidate the corresponding record in the cache.

## Pros & Cons
### Pros
- Improve performance on read operations.

### Cons
- Cost more efforts on development (Applications need to handle both cache and database).

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use
- The cache doesn't provide read-through and write-through/write-behind operations.
- The application performs more read operations than write operations.

## References
- Web Article: [Cache-Aside pattern | https://docs.microsoft.com/en-us/azure/architecture/patterns/cache-aside](https://docs.microsoft.com/en-us/azure/architecture/patterns/cache-aside)
- Web Article: [缓存更新的套路 | https://coolshell.cn/articles/17416.html)
