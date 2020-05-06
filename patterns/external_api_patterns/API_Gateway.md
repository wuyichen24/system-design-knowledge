# API Gateway

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
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
   - [AWS API Gateway](https://aws.amazon.com/api-gateway/)
   - [Tyk API Gateway](https://github.com/TykTechnologies/tyk)
   - [Kong Gateway](https://konghq.com/kong/)
   - [Traefik](https://docs.traefik.io/)
   - More products
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
