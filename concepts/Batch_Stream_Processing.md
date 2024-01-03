# Batch And Stream Processing

## Comparison
| | Batch processing | Stream processing |
|----|----|----|
| Responsiveness | No response to the client needed | No response to the client needed |
| Timelineness | On demand | Real-time |
| Input | Bounded input with finite size. A large amount of data | Input has no boundary (infinite streams) |
| Output | Materialized views, aggregated metrics, etc. | Materialized views, aggregated metrics, etc. |
| Performance measurement | Throughput | Throughput, latency |
| Fault tolerance | Better (a fixed set of input data) | More challenging (the input data keeps flowing in) |
| Example | MapReduce | Flink |
| Diagram | <img width="500" alt="Screenshot 2024-01-03 at 11 13 55 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/07616a59-26a7-40ea-b42f-53f0d7dfc9cc"> | <img width="500" alt="Screenshot 2024-01-03 at 11 14 05 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/e4cd5c4a-1854-4584-bfab-803b6f19b50d"> |


