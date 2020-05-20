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
- The configuration properties need to be refreshed when the application is running.
   - The only way to do that is to restart or redeploy the application.
- The multiple applications or application instances may use the same configuration properties.

## Solution
### Concepts
- Externalize all application configuration properties to a centralized location.

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
- Centralizes all the configuration properties to one place.
   - Easier management.
- The configuration properties can be shared across applications and application instances.
- Hot reload: The configuration properties can be refreshed without restarting the application.

### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|
| Security | Protect the configuration data | <li>Authorize users’ or applications' access to the configuration data.<li>Encrypts some or all of the configuration data. |
| Feasibility | Be flexible enough to store multiple versions of the configuration data (development, staging and production, etc.). | |

## When To Use
## References
- Book: [Chris R.(2018). Chapter 11 Developing production-ready services, *Microservices Patterns* (pp. 348-382). Manning Publications](https://www.manning.com/books/microservices-patterns)
- Web Article: [Pattern: Externalized configuration | https://microservices.io/patterns/externalized-configuration.html](https://microservices.io/patterns/externalized-configuration.html)
- Web Article: [External Configuration Store pattern | https://docs.microsoft.com/en-us/azure/architecture/patterns/external-configuration-store](https://docs.microsoft.com/en-us/azure/architecture/patterns/external-configuration-store)
