# CAP Theorem

## Concepts
- Any distributed data store can only provide two of the following three guarantees:
   - **Consistency (C)**: All nodes can see the same data at the same time.
   - **Availability (A)**: Every request receives a (non-error) response, without the guarantee that it contains the most recent write.
   - **Partition tolerance (P)**: The system continues to work despite message loss or partial failure.

     ![Screen Shot 2021-05-10 at 2 51 22 PM](https://user-images.githubusercontent.com/8989447/117723127-3b6f5300-b19f-11eb-893a-488ec6afbc46.png)

## Combinations
| Combination | Property Set | Error Handling |
|----|----|----|
| CP (Consistency over Availability) | ACID | The system will return an error or a time out if particular information cannot be guaranteed to be up to date. |
| AP (Availability over Consistency) | BASE | The system will always try to return the most recent available version of the information, but the information cannot be guaranteed to be up to date. |
| CA (This is possible)  | | |
