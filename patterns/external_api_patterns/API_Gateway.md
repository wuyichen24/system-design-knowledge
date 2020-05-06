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

## Solution
### Concepts
- Implement a service that’s the entry point into the microservices-based application from external API clients

### Functions
- **Routing**: Routes some requests to the corresponding service.
- **API Composition/Aggregation**: Aggregate multiple individual requests into a single request.
- **Monitoring**
   - Metrics collection: Collect metrics on API usage
   - Logging: Log requests.
- **Security**
   - Authentication: Verifying the identity of the client making the request.
   - Authorization: Verifying that the client is authorized to perform that particular operation.
   - Certificate management
- **Proxy**
   - Protocol translation: Translate external requests in one protocol to internal requests in another protocol.
- **Throttling**
   - Rate limiting: Limiting how many requests per second from either a specific client and/or from all clients.
   - User quota
- **Resiliency**: The mechanisms to detect failures and recover quickly from failures
- **Caching**: Cache responses to reduce the number of requests made to the services.

### Solution Options
- Use an API gateway or API management product.
   - See [API Management Products]() for more information.
- Develop an API gateway based on an API gateway framework.
   - [Netflix Zuul](https://github.com/Netflix/zuul)
   - [Spring Cloud Gateway](https://spring.io/projects/spring-cloud-gateway)

## Pros & Cons
### Pros
- Encapsulates internal structure of the application.
- Centralize the common functions like authentication and authorization.

### Cons
- Introduce single point of failure
- Must update the API gateway in order to expose a new services’s API.

## Consideration

## When To Use
## References
- Book: [Chris R.(2018). Chapter 8 External API patterns, *Microservices Patterns* (pp. 253-291). Manning Publications](https://www.manning.com/books/microservices-patterns)
