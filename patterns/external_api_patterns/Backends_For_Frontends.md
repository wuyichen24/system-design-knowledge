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
- Has different API gateways (backends) for different types of clients (frontends).

### Implementation

## Pros & Cons
### Pros
- Improves reliability - Each API gateway is isolated from others.
- Improves observability - Different API gateways can have different processes.
- Each API gateway is independently scalable.
- Reduces startup time for each API gateway.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Code Reusability | Code might be duplicated for common functionalities among API gateways. | <li>Consider to use the same technology stack for all API gateways. <li>Consider to put common functionalities into a shared library so that all the API gateways can use them.<li>Consider to put common functionalities into a new standalone service. |

## When To Use
## References
- Book: [Chris R.(2018). Chapter 8 External API patterns, *Microservices Patterns* (pp. 253-291). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [The Back-end for Front-end Pattern (BFF) | https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html](https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html)
