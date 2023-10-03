# RabbitMQ

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
