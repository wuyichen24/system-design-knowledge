# Message Queue (MQ)

- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Selection**](#selection)
   - [Factors](#factors)
   - [Comparison](#comparison)
   - [How to choose](#how-to-choose)
- [**Common problems and solutions**](#common-problems-and-solutions)
   - [How to guarantee message order](components/Message_Queue.md#how-to-guarantee-message-order)
   - [How to handle duplicated message](#how-to-handle-duplicated-message)
- [**Use cases**](#use-cases)
- [**References**](#references)

## Pros & Cons
### Pros
- **Asynchronous**
   - A producer doesn’t wait for the message to be processed.
- **Decoupling**
   - Producers are completely unaware of consumers (Don't have to know the IPs and ports of receivers).
   - Producers or consumers can be modified and deployed independently.
- **Buffering/Rate limiting**
   - It can act as a buffer if the consumer is unavailable or overloaded.
- **Fan-out**
   - The producer simply drops the message on the queue, and the multiple consumers process the message based on their needs at their own pace.

### Cons
- **Single point of failure**
   - The message queue can be a potential single point of failure.
- **Increase complexity**
   - Increase system complexity and operational complexity.

## Selection
### Factors
- **Supported programming languages**
- **Message ordering**
   - The order of messages can be preserved by the queue or not.
- **Message retention/expiration**
   - The limited period of time the message will be retained in the queue before being discarded.
- **Delivery guarantees**
  | | At-least-once | Exactly-once | At-most-once |
  |----|----|----|----|
  | Concept | Every message from the source system will reach its destination, but sometimes retries will cause duplicates | Every message from the source system will reach the destination with no possibility for loss or duplication | Every message from the source system may reach the destination with no possibility for duplication |
  | Delivey times | >= 1 | = 1 | <= 1 |
  | Use case | <ul><li>Data duplication is not a big issue<li>Deduplication is possible</ul> | <ul><li>Financial-related use cases (payment, trading, accounting, etc.)<li>Duplication is not acceptable<li>The downstream service or third party doesn’t support idempotency.</ul> | <ul><li>A small amount of data loss is acceptable (Monitoring metrics)</ul> |
  | Diagram | <img width="714" alt="Screenshot 2023-10-04 at 4 56 20 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/3f075e9e-b5a4-4a3d-a143-477233595a8e"> | <img width="714" alt="Screenshot 2023-10-04 at 4 56 08 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/b29551e5-7d53-4abd-abf4-d9944d3c6e25"> | <img width="714" alt="Screenshot 2023-10-04 at 4 56 08 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a97db3eb-f655-4d46-a319-6401934993de"> |
  
- **Availability**
- **Scalability**
- **Latency**

### Comparison
| | RabbitMQ | Kafka |
|----|----|----|
| Protocol | AMQP | Binary protocol over TCP |
| Message routing | Support multiple routing rules | Single |
| Message consumption | push | pull |
| Message ordering | Ordered at queue level | Ordered at partition level (Not topic level) |
| Message deleteion | Delete on ACK | Delete on retention period expires |
| Message deleyed delivery | Support | Not support |
| Message delivery gurantees | <li>At-most-once<li>At-least-once | <li>At-most-once<li>At-least-once<li>Exactly-once (by idempotent producers, transactional consumers) |
| Message persistence | Less | Strong (persisting messages to disk) |
| Client API | <li>Java<li>Ruby<li>JavaScript<li>Go<li>C<li>Swift<li>Spring<li>Elixir<li>PHP<li>.NET | <li>Java<li>Ruby<li>Python<li>Node.js |
| Federated queues | Yes | No |
| Complexity | Less | More |
| Throughput | 20K / sec | Millions / sec |
| Scaling strategies | Mostly vertical scaling | Horizontal scaling |
| Learning curve | Gentle | Steep |
| Ecosystem | Smaller | Larger |

### How to choose
- Choose *RabbitMQ* if
   - Multiple routing mechanisms
   - Low complexity and flat learning curve
- Choose *Kafka* if
   - Higher throughput
   - Persistence of messages

## Common problems and solutions
### How to guarantee message order
If a message queue cannot preserve the order of messages on its own, how to keep messages delivered in order (FIFO).
- **Solution 1**: Add sequencing information into each message.

### How to handle duplicated message
If there are duplicate messages in a message queue, how the receiver handles duplicate messages (Achieve exactly-once delivery guarantee from at-least-once delivery guarantee).
- **Solution 1**: Make the receiver idempotent.
   - The receiver can process the same message multiple times without no additional effect.
- **Solution 2**: Track each message which has been processed into a data store and discard duplicates.
   - Add a unique identifier into each message.

## Use cases
- [Use cases for Kafka](Kafka.md#use-cases)

## References
- Book: [Chris R.(2018). Chapter 3. Interprocess communication in a microservice architecture, *Microservices Patterns* (pp. 65-109). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Book: [Neha N.,Gwen S.,Todd P.(2017). Chapter 7. Building Data Pipelines, *Kafka: The Definitive Guide* (pp. 135-156). O'Reilly Media](https://www.oreilly.com/library/view/kafka-the-definitive/9781491936153/)
- Book: [Martin K.(2017). Chapter 4 Encoding and Evolution, *Designing Data-Intensive Applications* (pp. 111-150). O'Reilly Media](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/)
- Web Article: [Asynchronous Messaging Primer | https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589781(v=pandp.10)](https://docs.microsoft.com/en-us/previous-versions/msp-n-p/dn589781(v=pandp.10))
- [CloudAMQP | Comparison: Apache Kafka VS RabbitMQ](https://www.cloudamqp.com/blog/apachekafka-vs-rabbitmq.html)
- [How to choose between Kafka and RabbitMQ](https://tarunbatra.com/blog/comparison/How-to-choose-between-Kafka-and-RabbitMQ/#:~:text=Both%20Kafka%20and%20RabbitMQ%20offer,the%20consumers%20is%20more%20complex.)
