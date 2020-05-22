# Strangler

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
- the big-bang (cut-over) rewrite of the legacy application is extremely risky and will likely end in failure.

## Solution
### Concepts
- Incrementally refactor the legacy application to the new application and services.

### Implementation
- General advices
   - Migrate the high-value areas of the legacy application to the new application first.
   - Avoid making widespread changes to the legacy applicaton when migrating to the new application.
   - Design the new application in such a way as to make it easier for it to be strangled (refactored) in the future.

## Pros & Cons
### Pros
- Reduce the risk of the big-bang (cut-over) rewrite of the legacy application.
- Demonstrate the value of refactoring the legacy application early and often.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Collaboration | How to collaborate between the legacy application and the new application during the migration. | <li>Implementing an anti-corruption layer (ACL) between the legacy application and the new application.<li>Create a façade that route requests either to the legacy application or the new application. |

## When To Use

## References
- Book: [Chris R.(2018). Chapter 13 Refactoring to microservices, *Microservices Patterns* (pp. 428-471). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Strangler application | https://microservices.io/patterns/refactoring/strangler-application.html](https://microservices.io/patterns/refactoring/strangler-application.html)
- Web Article: [StranglerFigApplication | https://martinfowler.com/bliki/StranglerFigApplication.html](https://martinfowler.com/bliki/StranglerFigApplication.html)
- Web Article: [Legacy Application Strangulation : Case Studies | https://paulhammant.com/2013/07/14/legacy-application-strangulation-case-studies/](https://paulhammant.com/2013/07/14/legacy-application-strangulation-case-studies/)
- Web Article: [Strangler pattern | https://docs.microsoft.com/en-us/azure/architecture/patterns/strangler](https://docs.microsoft.com/en-us/azure/architecture/patterns/strangler)
