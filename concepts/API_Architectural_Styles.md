# API Architectural Styles

- [**SOAP**](#soap)
- [**REST**](#rest)
- [**RPC**](#rpc)
   - [gRPC](#grpc)
   - [Avro RPC](#avro-rpc)
- [**GraphQL**](#graphql)
- [**WebSocket**](#websocket)
- [**Webhook**](#webhook)

## SOAP

<img width="454" alt="Screenshot 2023-09-10 at 10 19 01 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/ab3e89d6-7239-4f43-8d7f-b582bcf0b632">

- **History**
   - 1998
- **Full name**
   - Simple Object Access Protocol
- **Concepts**
   - An XML-formatted, highly standardized web communication protocol.
   - SOAP is a successor of XML-RPC and also uses XML to encode its HTTP-based calls.
- **Message**
   - *Format*:
      - XML
   - *Structure*:
      - Envelope: Identifies the XML document as a SOAP message.
      - Header: Contains header information.
      - Body: Contains call and response information.
      - Fault: Provides information about errors that occurred while processing the message.
- **Dependent protocols**
   - HTTP
   - SMTP
- **Pros**
   - *Security*
      - SOAP meets an enterprise-grade transaction quality. It provides privacy and integrity inside the transactions while allowing for encryption on the message level.
   - *Error handling*
      - SOAP provides a standardized way to handle errors and exceptions.
   - *Platform-independent*
      - Supported by all mainstream platforms.
   - *Language-independent*
      - Supported by all mainstream programming languages.
- **Cons**
   - *Only support XML*
   - *Message is heavyweight*
   - *Complex*
      - Need specialized knowledge*
   - *Only support request/response style communication*
      - The client sends a request and needs to wait for a response.
      - Doesn't support streaming.
- **Use cases**
   - *Highly secured and reliable data transmission*
      - Financial services and payment gateway.
   - *Legacy system*

## REST

<img width="453" alt="Screenshot 2023-09-10 at 10 19 11 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/6af6ebb2-d327-4066-8fa0-27a7f80b4b07">

- **History**
   - 2000
- **Full name**
   - Representational State Transfer
- **Concepts**
   - An architectural style and set of constraints for designing networked applications and web services.
- **6 constraints**
   - *Client–server architecture*
      - Separate as client and server.
      - Allows either client or server to evolve independently.
   - *Statelessness*
      - The server does not store any information about the client's state between requests.
      - Each request from a client to a server must contain all the information needed to understand and process the request.
   - *Cacheability*
      - Responses from the server can be explicitly marked as cacheable or non-cacheable.
      - Clients and intermediaries can cache responses.
   - *Layered system*
      - Intermediaries can be placed between the client and server, such as load balancers, API gateways, proxy servers.
      - Those intermediaries will enhance scalability, security.
   - *Code on demand (optional)*
      - Servers can temporarily extend or customize the functionality of a client by transferring executable code
   - *Uniform interface*
      - REST encourages the use of a uniform and consistent interface for interacting with resources.
      - This simplifies client implementation and enhances the predictability of the API.
- **Message**
   - *Format*
      - Plain text
      - JSON
      - XML
      - HTML
   - *Structure*
      - URI (Uniform Resource Identifier): Identifies the resource being accessed or manipulated.
      - Method: Indicates the intended action to be performed on a resource.
         - GET
         - POST
         - PUT
         - DELETE
         - PATCH
      - Headers: Provides additional metadata about the request or response.
      - Request body: Contains data that the client sends to the server to create or update a resource.
- **Dependent protocols**
   - HTTP/1.1 (most common)
- **Pros**
   - *Most common API architectural styles*
      - Large ecosystem and community
   - *Simple*
   - *Easy to debug*
      - You can test a API from a web browser.
   - *Scalability*
      - Statelessness: The server doesn't have to retain past client request information.
      - Cacheability: Well-managed caching partially or completely eliminates some client-server interactions.
   - *Platform-independent*
      - Supported by all mainstream platforms.
      - Client and server can use different platform.
   - *Language-independent*
      - Supported by all mainstream programming languages.
      - Client and server can use different programming language.
- **Cons**
   - *Difficult in practice*
      - REST is simple in theory, but difficult in practice*
      - REST has a lot of good practices which is not enforced by the protocols.
   - *Weakly typed interfaces*
      - REST is not required to have a service definition and type definition of the information shared between client and server.
   - *Text-based message*
      - Message is heavyweight.
      - Inefficient for transporting binary data.
   - *Only support request/response style communication*
      - The client sends a request and needs to wait for a response.
      - Doesn't support streaming.
   - *Single resource*
      - Fetching multiple resources is challenging*
- **Use cases**
   - Public APIs
   - Simple resource-drive APIs
   
## RPC
- **History**
- **Full name**
   - Remote Procedure Call
- **Concepts**
   - A protocol and technique for invoking functions or procedures in a remote system.
- **RPC frameworks**

  | Name | Description | Message encoding | Introduced by |
  |---|---|---|---|
  | gRPC | A RPC framework for high performance data transmition. | Protocol Buffers | Google |
  | Avro RPC | A RPC framework for high performance data transmition. | Avro | |
  | Thrift RPC | A RPC framework for high performance data transmition. | Thrift | Facebook |
  | Finagle | A RPC framework for the JVM, used to construct high-concurrency servers. | |
  | Twrip | | Protocol Buffers | Twitch |
  | Cap'n Proto | | | |

- **Pros**
   - *Language-independent*
      - Supported by all mainstream programming languages.
- **Cons**
   - *Tight coupling*
      - Leads to tight coupling between the client and server, making it challenging to evolve and update the system without breaking compatibility.
   - *Hard to change*
   - *Hard to debug*

## gRPC

<img width="455" alt="Screenshot 2023-09-10 at 10 19 41 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/cf16cb99-46a2-4d8a-a22e-d3a4e012ad3b">

- **History**
   - 2016
- **Concepts**
   - A cross-platform open source high performance RPC framework created by Google.
- **Message**
   - *Format*
      - Protocol Buffers
- **Dependent protocols**
   - HTTP/2
- **Pros**
   - *High performance*
      - Protocol buffers is a very efficient binary coding format (much faster than JSON).
      - gRPC is built on top of HTTP/2.
   - *Support bidirectional streaming*
      - gRPC uses HTTP/2 streams.
      - It allows multiple streams of messages over a single long-lived TCP connection.
   - *Strongly typed interfaces*
      - gRPC uses protocol buffers as the interface definition language to define how interface looks like.
   - *Built-in features*
      - Authentication
      - Encryption
      - Resiliency (deadlines and timeouts)
      - Metadata exchange
      - Load balancing
      - Service discovery
   - *Language-independent*
      - Supported by all mainstream programming languages.
      - Client and server can use different programming language.
      - Client and server only need to share the interface definition file for generating stubs respectively.
- **Cons**
   - *Not for external*
      - Limited web browser support. 
   - *Need to regenerate code*
      - When the interface definition changes hugely, we need to regenerate code for both client and server.
   - *Small ecosystem*
   - *Legacy firewall might not support HTTP/2*
- **Use cases**
   - Internal APIs
   - Large data transfer

## Avro RPC
- **Pros**
   - *No need to generate code beforehand*
      - Client and server exchange schemas in the connection handshake and code generation is not required.

## GraphQL

<img width="455" alt="Screenshot 2023-09-10 at 10 19 24 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/02153c46-9c8d-42a6-a812-da07e80bc0dc">

- **History**
   - 2015
- **Concepts**
   - An open-source data query and manipulation language for APIs and a query runtime engine.
   - *Declarative data fetching*
      - A client can specify exactly what data it needs.
      - GraphQL server can fetch from separate data sources and present the data in a unified graph.
   - *Schema*
      - GraphQL APIs are defined by a schema that specifies the types of data that can be queried and the structure of those queries.
   - *Subscriptions*
      - Allows clients to receive updates when data changes on the server.
   - *Batching*
      - GraphQL allows clients to send multiple queries in a single request.
- **Message**
   - *Format*
      - JSON
- **Dependent protocols**
   - HTTP/1.1
- **Pros**
   - *Type schema*
      - GraphQL can provide the data that a client needs (No more over-fetching and underfetching).
      - GraphQL can combine multiple resources from multiple data sources.
   - *Error handling*
      - GraphQL provides detailed error message.
   - *No versioning*
      - No versioning needed for GraphQL
- **Cons**
   - *Performance*
      - Having too many nested fields in one request can lead to system overload.
   - *Caching*
      - As GraphQL isn’t reusing HTTP caching semantics.
   - *Steep learning curve*
      - Cost time to figure out GraphQL niche operations and SDL.
- **Use cases**
   - *Mobile app*
      - Mobile app can load all the needed data by one request.
   - *Complex system*
      - GraphQL server can provide aggregated data and hide the complexity of the system.
   - *Graph-like data*
      - Like social network, recommendation system, knowledge graphs, geospatial data, network topologies.   
        
## WebSocket

<img width="451" alt="Screenshot 2023-09-10 at 10 19 55 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/1efbd56e-db97-4857-a8b6-4577e5460a2b">

- **Concept**
   - Provides full-duplex communication over a single TCP connection.
   - A connection consists of 3 steps
      - Handshake
      - Persistent connection
      - Closure
- **Pros**
   - *Real-time data trasfer*
      - Low latency
   - *Bidirectional*
      -  WebSocket provides full-duplex communication than half-duplex alternatives such as HTTP polling.
   - *Persistent connection*
- **Cons**
- **Use cases**
   - *Low-latency data exchange*
      - Live chat apps, real-time gaming

## Webhook

<img width="452" alt="Screenshot 2023-09-10 at 10 20 07 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/df8f798e-01dc-4c75-a031-7b627e308b7a">

- **Concepts**
   - A method of using HTTP callbacks for asynchronous operations.
- **Use cases**
   - Event-driven applications.

## Resources
- [AltexSoft | Comparing API Architectural Styles: SOAP vs REST vs GraphQL vs RPC](https://www.altexsoft.com/blog/soap-vs-rest-vs-graphql-vs-rpc/)
- [AWS | What Is A RESTful API?](https://aws.amazon.com/what-is/restful-api/)
