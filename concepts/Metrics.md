# Metrics

- [**Storage**](#storage)
   - [Units of measurement for data storage](#units-of-measurement-for-data-storage)
- [**Performance**](#performance)
   - [Metrics](#metrics-1)
   - [QPS vs. TPS](#qps-vs-tps)
   - [Calculation](#calculation)

## Storage
### Units of measurement for data storage
| Name | Abbreviation | Size (base 2) | Conversion |
|----|----|----|----|
| bit | b | 1/8 | |
| Byte | B | 1 | 1 B = 8 b |
| Kilobyte | KB | 2<sup>10</sup> | 1 KB = 2<sup>10</sup> B |
| Megabyte | MB | 2<sup>20</sup> | 1 MB = 2<sup>10</sup> KB |
| Gigabyte | GB | 2<sup>30</sup> | 1 GB = 2<sup>10</sup> MB |
| Terabyte | TB | 2<sup>40</sup> | 1 TB = 2<sup>10</sup> GB |
| Petabyte | PB | 2<sup>50</sup> | 1 PB = 2<sup>10</sup> TB |
| Exabyte | EB | 2<sup>60</sup> | 1 EB = 2<sup>10</sup> PB |
| Zettabyte | ZB | 2<sup>70</sup> | 1 ZB = 2<sup>10</sup> EB |
| Yottabyte | YB | 2<sup>80</sup> | 1 YB = 2<sup>10</sup> ZB |

## Performance
### Metrics
- Queries per second (QPS): The number of queries (requests) a server can be responded to.
- Transactions per second (TPS): The number of transactions a server can handle.
- Response time (RT): The time period between the client sends a request and the client receives the response.
- Concurrency: The number of requests/transactions can be handle concurrently.

### QPS vs. TPS
- **QPS**
   - QPS is often associated with individual queries or requests
- **TPS**
   - TPS typically measures the rate of complete transactions, which may involve multiple requests.
- **Examples**
   - One transaction can be one access to a web page. But during this transaction, the client can send 3 requests to the server.
   
### Calculation
- `QPS = Councurrency / RT`
