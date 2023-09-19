# API Performance

## How to improve API performance
- **Optimize database**
   - *Optimize queries*
      - Add indexes to tables.
      - Process denormalization.
   - *Optimize connection*
      - Implement connection pooling to manage and reuse database connections efficiently, reducing overhead in opening and closing connections for each request.
- **Caching**
   - Implement caching mechanisms to store frequently accessed data in memory.
- **Reduce payload size**
   - Enable compression (e.g., gzip or Brotli)
   - Use efficient serialization formats like JSON or Protocol Buffers (protobuf).
   - Using pagination, filtering.
- **Load balancing and horizontal scaling**
   - Use load balancers to distribute incoming API requests across multiple server instances.
   - Add more API server instances to handle increased traffic. Implement auto-scaling to dynamically adjust server instances based on demand.
- **Rate limiting**
   - Implement rate limiting to restrict the number of requests from a single client within a given time frame. 
- **Asynchronous processing**
   - Offload time-consuming or non-blocking tasks to background jobs or queues, freeing up API resources to handle more requests.
   - Implement asynchronous APIs when appropriate, especially for long-running operations.
- **Content Delivery Networks (CDNs)**
   - Use CDNs to distribute and cache static assets like images, videos, and files.
- **Asynchronous logging**
   - Synchronous logging deals with the disk for every call and can slow down the system.
   - Asynchronous logging sends logs to a lock-free buffer first and immediately returns. The logs will be flushed to the disk periodically. This significantly reduces the I/O overhead.

## Metrics
### Response time (Latency)
- **Concepts**
   - Response time measures the time it takes for the API to process a request and send back a response.
   - It is often broken down into server processing time and network transfer time.
- **Metrics**
   - Average response time
   - 90th or 95th percentile response time
   - Maximum response time

### Throughput
- **Concepts**
   - Throughput measures the number of requests the API can handle per unit of time (e.g., requests per second or requests per minute). It indicates the API's capacity.
- **Metrics**
   - Requests Per Second (RPS)
   - Requests Per Minute (RPM)

### Concurrency
- **Concepts**
   - Concurrency measures the number of simultaneous requests the API can handle without degrading performance.
- **Metrics**
   - Concurrent connections
   - Concurrent users

### Data transfer rate
- **Concepts**
   - Data transfer rate measures the rate at which data is sent or received by the API, which can impact network performance.
- **Metrics**
   - Data sent per second
   - Data received per second
