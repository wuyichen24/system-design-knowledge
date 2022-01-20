# CAP Theorem

- [Concepts](#concepts)
- [Combinations](#combinations)
- [References](#references)

## Concepts
- Any distributed data store can only provide two of the following three guarantees:
   - **Consistency (C)**: All nodes can see the same data at the same time.
   - **Availability (A)**: Every request receives a (non-error) response, without the guarantee that it contains the most recent write.
   - **Partition tolerance (P)**: The system continues to work despite message loss or partial failure.

     ![CAP-Theorem-Explained](https://user-images.githubusercontent.com/8989447/150275056-ecdea92d-fe35-4a15-9c77-16b0f9ece6b4.png)

## Combinations
| Combination | Property Set | Behavior when a network partition failure happens |
|----|----|----|
| CP (Consistency over Availability) | ACID | The system will return an error or a time out if particular information cannot be guaranteed to be up to date. |
| AP (Availability over Consistency) | BASE | The system will always try to return the most recent available version of the information, but the information cannot be guaranteed to be up to date. |
| CA (This is possible)  | | |

> Note: The choice is between consistency and availability only when a network partition or failure happens. When there is no network failure, both availability and consistency can be satisfied.

## References
- [Wikipedia: CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem)
