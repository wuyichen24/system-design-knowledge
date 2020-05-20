# External Configuration Store

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
      - [Approaches](#approaches)
      - [Push Model External Configuration](#push-model-external-configuration)
      - [Pull Model External Configuration](#pull-model-external-configuration)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation

## Solution
### Concepts
- Externalize all application configuration property values to a centralized location.

### Implementation
#### Approaches
- **Push model**: The deployment infrastructure passes the configuration properties to the service instance using.
- **Pull model**: The service instance reads its configuration properties from a configuration server.

#### Push Model External Configuration
- Solution options for passing configuration properties
   - Command-line arguments.
   - Operating system environment variables.
   - A configuration file in the current directory.

#### Pull Model External Configuration
- Solution options for storing configuration properties
   - Version control system such as Git
   - Databases
   - Specialized configuration servers
      - Spring Cloud Config Server
      - Hashicorp Vault
      - AWS Parameter Store

## Pros & Cons
### Pros
- Centralize all the configuration properties to one place.
   - Easier management.
- Hot reload: The configuration properties can be refreshed without restarting the application.

### Cons

## Consideration
## When To Use
## References
- Book: [Chris R.(2018). Chapter 11 Developing production-ready services, *Microservices Patterns* (pp. 348-382). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Externalized configuration | https://microservices.io/patterns/externalized-configuration.html](https://microservices.io/patterns/externalized-configuration.html)
