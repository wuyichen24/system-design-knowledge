# Cache-As-SOR

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Sub-Patterns](#sub-patterns)
   - [Implementation](#implementation)
- [**Pros & Cons**](#pros--cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation

## Solution
### Concepts
### Sub-Patterns
| Pattern Name | Diagram | Description | 
|----|----|----|
| *Read-Through* | ![](../../diagrams/png/read_through_small.png) | If requested data is not in cache, cache will load the data from database and let application read **synchronously**. |
| *Write-Through* | ![](../../diagrams/png/write_through_small.png) | After application writes data to cache, cache **synchronously** writes the same data to database. |
| *Write-Behind* | ![](../../diagrams/png/write_behind_small.png) | After application writes data to cache, cache **asynchronously** writes the same data to database (When satisfy a certain criteria). |
| *Refresh-Ahead* | ![](../../diagrams/png/refresh_ahead_small.png) | Cache automatically and **asynchronously** reloads (refreshs) any recently accessed cache entry from database before its expiration. |

### Implementation

## Pros & Cons
- **Write-Through**
   - Pros
      - No risk of data loss.
   - Cons
      - Slow (cache can only ack back until writing data to database successfully).
      - When a new cache node is added, the new cache node will be empty until there is a update from the application.
- **Write-Behind**
   - Pros
      - Faster (cache can ack back without writing data to database).
   - Cons
      - Risk of data loss: Data may lose after cache goes down, but before it have been written to database.
      - More complex to implement.
- **Refresh-ahead**
   - Pros
      - Faster
   - Cons
      - Not accurately predicting which items are likely to be needed in the future can result in reduced performance than without refresh-ahead.
      

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
