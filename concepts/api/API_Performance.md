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
## Metrics
