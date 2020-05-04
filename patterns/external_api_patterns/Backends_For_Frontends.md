# Backends For Frontends (BFF)

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
- The requirements are different significantly for serving different frontends.

## Solution
### Concepts
- Uses different backends for different types of frontends.

### Implementation

## Pros & Cons
### Pros
- Each backend is smaller, less complex and faster than one general backend.
- Each Abackend is isolated from others.
   - Each backend can have different processes.
   - Each backend is independently scalable.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Code Reusability | Code duplication across backends is highly likely | <li>Consider to use the same technology stack for all backends. <li>Consider to put common functionalities into a shared library so that all the backends can use them.<li>Consider to put common functionalities into a new standalone service. |

## When To Use
## References
- Book: [Chris R.(2018). Chapter 8 External API patterns, *Microservices Patterns* (pp. 253-291). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [The Back-end for Front-end Pattern (BFF) | https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html](https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html)
