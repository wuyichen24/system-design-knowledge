# Kafka

## Concepts
### Message, key, offset, batch
- **Message**
   - The unit of data.
- **Key**
   - The messages with the same key are always written to the same partition.
- **Offset**
   - The consumer keeps track of which messages it has already consumed by keeping track of the offset of messages.
- **Batch**
   - A collection of messages.

### Topic, partition, stream
- **Topic**
   - Messages in Kafka are categorized into topics.
   - One topic can have one or multiple partitions.
- **Partition**
   - Each partition of the same topic can be hosted on a different server (A single topic can be scaled horizontally across multiple servers)
   - One partition can be only consumed by one consumer within a single consumer group.
   - One partition can be consumed by multiple consumers in different consumer group.

### Producer, consumer
### Broker, cluster
### Retention

## Partition
- **Concept**
- **Characteristics**
   - Each partition of the same topic can be hosted on a different server (A single topic can be scaled horizontally across multiple servers)
   - One partition can be consumed by only one consumer from one consumer group.
   - One partition can be consumed by multiple consumers from different consumer groups.
