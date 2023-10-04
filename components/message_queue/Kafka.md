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

### Topic, partition
- **Topic**
   - Messages in Kafka are categorized into topics.
   - One topic can have one or multiple partitions.
- **Partition**
   - Each partition of the same topic can be hosted on a different server (A single topic can be scaled horizontally across multiple servers)
   - One partition can be only consumed by one consumer within a single consumer group.
   - One partition can be consumed by multiple consumers in different consumer group.

### Consumer group
- **Consumer group**
   - A group of consumers that consume the same topic.
  
### Broker, cluster
- **Broker**
   - A single Kafka server.
- **Cluster**
   - A collection of brokers.
- **Controller**
   - A broker can be elected as a controller among a cluster.
   - The controller is responsible for administrative operations, including assigning partitions to brokers and monitoring for broker failures.

## Partition
- **Concept**
   - A partition is the smallest storage unit that holds a subset of messages owned by a topic.
- **Characteristics**
   - Each partition of the same topic can be hosted on a different server.
   - One partition can be consumed by only one consumer from one consumer group.
   - One partition can be consumed by multiple consumers from different consumer groups.
- **Implementation**
   - Each partition is a single log file where records are written to it in an append-only fashion.
- **Characteristics**
   - Create topics with a large number of partitions so that more consumer can consume messages at the same time.

## Common problems and solutions
### Message loss
- Which scenarios will have message loss

### Message duplication

## Use cases
- **Log processing**
   - **Kafka**
      - Collects log streams from each instance.
   - **ElasticSearch**
      - Consumes the logs from Kafka and indexes them for full-text search.
   - **Kibana**
      - Provides a search and visualization UI on top of ElasticSearch

  ![log_processing](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/e113277e-139c-4039-9ce9-3d7fc49e2ade)
  
- **Data streaming**
   - **Kafka**
      - Collects clickstream data.
   - **Flink**
      - Aggregates clickstream data.
   - **Data lake**
      - Stores aggregated data for training machine learning models.

  ![data_streaming copy](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/87ae0cb6-8aad-4bd4-8b6f-1b0f4401db06)

- **System monitoring and alerting**

  ![monitoring](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/cbe37ccc-0037-4a33-b903-185e38a652fb)

- **Change data capture**
   - Observes database transaction logs and streaming changes to Kafka.
   - Downstream systems like search, caches, and replicas are updated from Kafka.

  ![cdc](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/03712ab9-c19f-4342-9ad9-ad4bc9183bb6)
