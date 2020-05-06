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
- Functions
   - **Request routing**: Routes some requests to the corresponding service.
   - **API composition/aggregation**: Aggregate multiple individual requests into a single request.
   - **Authentication**: Verifying the identity of the client making the request.
   - **Authorization**: Verifying that the client is authorized to perform that particular operation.
   - **Rate limiting**: Limiting how many requests per second from either a specific client and/or from all clients.
   - **Caching**: Cache responses to reduce the number of requests made to the services.
   - **Metrics collection**: Collect metrics on API usage for billing analytics purposes.
   - **Request logging**: Log requests.

### Solution Options
- Use API gateway product
- Develop an API gateway based on API gateway framework


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
