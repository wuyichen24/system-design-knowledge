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

## Architecture patterns
### Lambda
- **Concepts**
   - A system that contains two processing paths (batch and streaming) simultaneously.
- **Cons**
   - There are two codebases to maintain.
- **Diagram**
  
   ![figure-10-lambda-and-kappa-architectures-QONSAGXY](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/da62affc-548a-4e68-ac3a-6f55246118f4)

### Kappa
- **Concepts**
   - A system that combines the batch and streaming in one processing path.
   - Handle both real-time data processing and continuous data reprocessing using a single stream processing engine.
- **Diagram**

   ![figure-10-lambda-and-kappa-architectures-QONSAGXY](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/e8310c4a-5902-4be6-b9a5-d29cd97211c2)
