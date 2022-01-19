# Message Queue

- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**Solutions**](#solutions)
   - [Message Ordering](#message-ordering)
   - [Duplicate Messages](#duplicate-messages)
- [**Standards**](#standards)
   - [Protocols](#protocols)
   - [APIs](#apis)
- [**References**](#references)

## Pros & Cons
### Pros
- **Asynchronous**
   - A sender doesn’t wait for the message to be delivered.
- **Loose coupling**
   - Senders are completely unaware of receivers (Don't have to know the IPs and ports of receivers).
- **Message buffering**
   - It can act as a buffer if the receiver is unavailable or overloaded.

### Cons
- **Single point of failure**
   - The message queue can be a potential single point of failure.
- **Increase complexity**
   - Increase system complexity and operational complexity.

## Consideration
When choosing a message queue product or designing a message queue architecture, the following aspects need to be considered:
- **Supported programming languages**
- **Message ordering**
   - The order of messages can be preserved by the queue or not.
- **Message retention/expiration**
   - The limited period of time the message will be retained in the queue before being discarded.
- **Delivery guarantees**
   - *At-least-once*: Every message from the source system will reach its destination, but sometimes retries will cause duplicates (delivery times >= 1).
   - *Exactly-once*: Every message from the source system will reach the destination with no possibility for loss or duplication (delivery times = 1).
   - *At-most-once*: Every message from the source system may reach the destination with no possibility for duplication (delivery times <= 1).
- **Availability**
- **Scalability**
- **Latency**

## Solutions
### Message Ordering
If a message queue cannot preserve the order of messages on its own, how to keep messages delivered in order (FIFO).
- **Solution 1**: Add sequencing information into each message.

### Duplicate Messages
If there are duplicate messages in a message queue, how the receiver handles duplicate messages (Achieve exactly-once delivery guarantee from at-least-once delivery guarantee).
- **Solution 1**: Make the receiver idempotent.
   - The receiver can process the same message multiple times without no additional effect.
- **Solution 2**: Track each message which has been processed into a data store and discard duplicates.
   - Add a unique identifier into each message.

## Standards
### Protocols
- AMQP (Advanced Message Queuing Protocol)
- STOMP (Streaming Text Oriented Messaging Protocol)
- MQTT (Message Queuing Telemetry Transport)
- XMPP (Extensible Messaging and Presence Protocol)

### APIs
- JMS (Java Message Service)

## References
- Book: [Chris R.(2018). Chapter 3. Interprocess communication in a microservice architecture, *Microservices Patterns* (pp. 65-109). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Book: [Neha N.,Gwen S.,Todd P.(2017). Chapter 7. Building Data Pipelines, *Kafka: The Definitive Guide* (pp. 135-156). O'Reilly Media](https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/)
- Book: [Martin K.(2017). Chapter 4 Encoding and Evolution, *Designing Data-Intensive Applications* (pp. 111-150). O'Reilly Media](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/)
- Web Article: [Asynchronous Messaging Primer | https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589781(v=pandp.10)](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589781(v=pandp.10))
