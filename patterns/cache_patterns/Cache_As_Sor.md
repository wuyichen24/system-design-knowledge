# Cache-As-SOR

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

## Solution
### Concepts
### Sub-Patterns
| Pattern Name | Diagram | Description | 
|----|----|----|
| *Read-Through* | ![](../../diagrams/png/read_through_small.png) | If requested data is not in cache, cache will load the data from database and let application read **synchronously**. |
| *Write-Through* | ![](../../diagrams/png/write_through_small.png) | After application writes data to cache, cache **synchronously** write the same data to database. |
| *Write-Behind* | ![](../../diagrams/png/write_behind_small.png) | After application writes data to cache, cache **asynchronously** write the same data to database (When satisfy a certain criteria). |
| *Refresh-Ahead* | ![](../../diagrams/png/refresh_ahead_small.png) | Cache automatically and **asynchronously** reloads (refreshs) any recently accessed cache entry from database before its expiration. |

### Implementation

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
