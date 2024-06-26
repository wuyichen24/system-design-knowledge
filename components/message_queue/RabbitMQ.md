# RabbitMQ

- [**Message flow**](#message-flow)
- [**Concepts**](#concepts)
- [**Exchange types**](#exchange-types)
- [**References**](#references)

## Message flow
![exchanges-bidings-routing-keys](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/733d4a95-7a70-4c6c-92ab-a2878aebd0ca)

- The producer publishes a message to an exchange.
- The exchange routes the message by different attributes, depending on the exchange type.
- Bindings are created from the exchange to queues for routing the message to the queue.
- The messages stay in the queue until they are handled by a consumer.

## Concepts
- **Producer**
   - Application that sends the messages.
- **Consumer**
   - Application that receives the messages.
- **Queue**
   - Buffer that stores messages.
- **Message**
   - Information that is sent from the producer to a consumer through RabbitMQ.
- **Connection**
   - A TCP connection between your application and the RabbitMQ broker.
- **Channel**
   - A virtual connection inside a connection. When publishing or consuming messages from a queue - it's all done over a channel.
- **Exchange**
   - Receives messages from producers and pushes them to queues depending on rules defined by the exchange type. To receive messages, a queue needs to be bound to at least one exchange.
- **Binding**
   - A binding is a link between a queue and an exchange.
- **Routing key**
   - A key that the exchange looks at to decide how to route the message to queues. Think of the routing key like an address for the message.
- **AMQP**
   - Advanced Message Queuing Protocol is the protocol used by RabbitMQ for messaging.
- **Users**
   - It is possible to connect to RabbitMQ with a given username and password. Every user can be assigned permissions such as rights to read, write and configure privileges within the instance. Users can also be assigned permissions for specific virtual hosts.
- **Vhost/virtual host**
   - Provides a way to segregate applications using the same RabbitMQ instance. Different users can have different permissions to different vhost and queues and exchanges can be created, so they only exist in one vhost.

## Exchange types
- **Direct**
   - The message is routed to the queues whose binding key exactly matches the routing key of the message.
- **Fanout**
   - A fanout exchange routes messages to all of the queues bound to it.
- **Topic**
   - The topic exchange does a wildcard match between the routing key and the routing pattern specified in the binding.
- **Headers**
   - Headers exchanges use the message header attributes for routing.

## Common problems and solutions
### Message loss

![pubacks](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/0a5fb346-711f-4746-aeca-8307c6ad8da8)

- **Scenario 1**: Message cannot be published from producer to RabbitMQ
   - Solutions
      - Set publisher confirms as `true`.
      - Implement publisher confirm callback function.
- **Scenario 2**: Message cannot be routed to correct queue
   - Solutions
      - Set mandatory as `true` (turn on the failure notification).
      - Implement return callback function.
- **Scenario 3**: Meessage cannot be delivered from RabbitMQ to consumer.
   - Solutions
      - Set acknowledge mode as `manual` (Consumer needs to acknowledge manually after processing the message successfully).

### Message duplication

## References
- [Part 1: RabbitMQ for beginners - What is RabbitMQ?](https://www.cloudamqp.com/blog/part1-rabbitmq-for-beginners-what-is-rabbitmq.html)
- [Introducing Publisher Confirms](https://blog.rabbitmq.com/posts/2011/02/introducing-publisher-confirms)
