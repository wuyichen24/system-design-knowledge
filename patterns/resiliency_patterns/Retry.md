# Retry

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
- Retry an operation for transient faults.

### Implementation
#### Retry Strategies
| Strategy Name | Situation | Operation |
|----|----|----|
| **Cancel** | The failure isn't transient or is unlikely to be successful if repeated. | Cancel the operation and report an exception. |
| **Retry** | The failure is unlikely to be repeated. | Retry the failing request again immediately. |
| **Retry after delay** | The failure is unlikely to be repeated after a short period of time. | Wait for a suitable time before retrying the request. |

#### Retry Policies
- The time between retries should be specified.
   - fixed time
   - increasing time
- The maximum number of retries should be specified.

#### Advice
- For some noncritical operations, it's better to fail fast rather than retry several times and impact the throughput of the application.
- It's useful for the retry policy to adjust the time between retry attempts based on the type of the exception.

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Duplicate execution | Retries could cause the operation to be executed more than once, with unintended side effects. | <li>Consider to make the operation idempotent (If the operation is idempotent, it would be inherently safe to retry). |
   
## When To Use

## References
