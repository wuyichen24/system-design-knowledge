# Message Queue

## Pros & Cons
### Pros
- **Asynchronous**
- **Loose coupling**
- **Message buffering**

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
If a message queue cannot preserve the order of messages on its own, how to keep messages delivered in order (FIFO).
- **Solution 1**: Add sequencing information into each message.

### Duplicate Messages
If there are duplicate messages in a message queue, how the consumer handles duplicate messages (Achieve exactly-once delivery guarantee from at-least-once delivery guarantee).
- **Solution 1**: Make the consumer idempotent.
   - The consumer can consume the same message multiple times without no additional effect.
- **Solution 2**: Track each message which has been consumed into a data store and discard duplicates.
   - Add a unique identifier into each message.

## References
- Book: [Chris R.(2018). Chapter 3. Interprocess communication in a microservice architecture, *Microservices Patterns* (pp. 65-109). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Book: [Neha N.,Gwen S.,Todd P.(2017). Chapter 7. Building Data Pipelines, *Kafka: The Definitive Guide* (pp. 135-156). O'Reilly Media](https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/)
