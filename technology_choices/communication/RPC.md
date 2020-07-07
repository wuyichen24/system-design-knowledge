# RPC

| Product | Encoding Format | Features |
|---|---|---|
| gPRC | Protocol Buffer | <li>Supports streams, which is a series of requests and responses over time.|
| Thrift RPC | Thrift | |
| Avro RPC | Avro | |
| Finagle | Thrift | <li>Use futures (promises) to encapsulate asynchronous actions that may fail.<li>Futures also simplify situations where you need to make requests to multiple services in parallel, and combine their results. |
| Rest.li | JSON | <li>Use futures (promises) to encapsulate asynchronous actions that may fail.<li>Futures also simplify situations where you need to make requests to multiple services in parallel, and combine their results. |
