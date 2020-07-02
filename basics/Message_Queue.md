# Message Queue

## Pros & Cons
### Pros
### Cons

## Consideration
When choosing a message queue product or designing a message queue architecture, the following aspects need to be considered:
- **Supported programming languages**
- **Message ordering**
   - The order of messages can be preserved by the queue or not.
- **Message retention**
   - The period of time message will be retained in the queue before being removed.
- **Delivery guarantees**
   - *At-least-once*: Every message from the source system will reach its destination, but sometimes retries will cause duplicates.
   - *Exactly-once*: Every message from the source system will reach the destination with no possibility for loss or duplication.
- **Scalability**
- **Latency**

## Solutions
### Message Ordering
If a message queue cannot preserve the order of messages on its own

### Duplicate Messages

## References
