# Metrics

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

## Availability
### Mapping between availability percentage and service downtime
| Availability % | Number of nines | Downtime per year | Downtime per month | Downtime per week |
|-----|-----|-----|-----|-----|
| 90% | 1 nine | 36.5 days | 72 hours | 16.8 hours |
| 99% | 2 nines | 3.65 days | 7.2 hours | 1.68 hours |
| 99.5% | | 1.83 days | 3.6 hours | 50.4 minutes |
| 99.9% | 3 nines | 8.76 hours | 43.8 minutes | 10.1 minutes |
| 99.95% | | 4.38 hours | 21.56 minutes | 5.04 minutes |
| 99.99% | 4 nines | 52.56 minutes | 4.32 minutes | 1.01 minutes |
| 99.999% | 5 nines | 5.26 minutes | 25.9 seconds | 6.05 seconds |
| 99.9999% | 6 nines | 31.5 seconds | 2.59 seconds | 0.605 seconds |
| 99.99999% | 7 nines | 3.15 seconds | 0.259 seconds | 0.0605 seconds |

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
