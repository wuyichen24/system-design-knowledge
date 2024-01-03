# Batch And Stream Processing

## Comparison
| | Batch | Stream processing |
|----|----|----|
| Responsiveness | No response to the client needed | No response to the client needed |
| Input | Bounded input with finite size. A large amount of data | Input has no boundary (infinite streams) |
| Output | Materialized views, aggregated metrics, etc. | Materialized views, aggregated metrics, etc. |
| Performance measurement | Throughput | Throughput, latency |
| Fault tolerance | Better (a fixed set of input data) | More challenging (the input data keeps flowing in) |
| Example | MapReduce | Flink |
