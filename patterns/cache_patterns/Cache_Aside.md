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
- Applications take the responsibility of using the cache to maintain data.

### Implementation
#### Read Operation
- Check the requested record is held in the cache or not:
   - If the requested record is held in the cache:
      - Return the record directly.
   - If the requested record is not in the cache:
      - Read the record from the database and return it.
      - Store the copy of the record in the cache.
      
#### Update Operation
- Update the record into the database.
- Invalidate the corresponding item in the cache.

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
