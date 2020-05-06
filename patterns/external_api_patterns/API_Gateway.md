# API Gateway

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Functions](#functions)
   - [Solution Options](#solution-options)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation
- The client must keep track of multiple services.
- Each service must handle some cross-cutting tasks, like authentication, authorization, etc.

## Solution
### Concepts
- Implements a service that’s the single entry point into the backend services from external clients.
- Offloads cross-cutting functionalities from individual services to the API gateway.

### Functions
- **Core functions**
   - **Request Routing**: Routes requests to one or more backend services, using layer 7 routing.
      - It can be based on method (GET, POST, etc.), IP, port, header, or URL.
   - **API Composition/Aggregation**: Aggregates multiple individual requests into a single request.
- **Cross-cutting functions**
   - **Monitoring**
      - Metrics collection: Collects metrics on API usage
      - Logging: Log requests.
   - **Security**
      - Authentication: Verifies the identity of the client making the request.
      - Authorization: Verifies that the client is authorized to perform that particular operation.
      - SSL termination: Decrypts the SSL-encrypted requests from clients and pass on unencrypted requests to the internal services.
      - Certificate management
   - **Proxy**
      - Protocol translation: Translates external requests in one protocol to internal requests in another protocol.
   - **Throttling**
      - Rate limiting: Limits how many requests per second from either a specific client and/or from all clients.
      - User quota
   - **Resiliency**: The mechanisms to detect failures and recover quickly from failures
   - **Response Caching**: Caches responses to reduce the number of requests made to the internal services.
   - **Filtering**: 
      - IP whitelisting
      - IP blacklisting

### Solution Options
- Use an API gateway or API management product.
   - See [API Management Products]() for more information.
- Develop an API gateway based on an API gateway framework.
   - [Netflix Zuul](https://github.com/Netflix/zuul)
   - [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway)

## Pros & Cons
### Pros
- Encapsulates internal structure of the application.
- Centralize the cross-cutting functionalities (authentication, authorization, etc.) into one place.
- Reduces the number of requests/roundtrips by API Composition/Aggregation.

### Cons
- Introduce single point of failure
- Must update the API gateway in order to expose a new services’s API.

## Consideration

## When To Use
## References
- Book: [Chris R.(2018). Chapter 8 External API patterns, *Microservices Patterns* (pp. 253-291). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: API Gateway / Backends for Frontends | https://microservices.io/patterns/apigateway.html](https://microservices.io/patterns/apigateway.html)
- Web Article: [Using API gateways in microservices | https://docs.microsoft.com/en-us/azure/architecture/microservices/design/gateway](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/gateway)
