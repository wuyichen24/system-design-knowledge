# Network

- [**OSI model**](#osi-model)
- [**Common protocols**](#common-protocols)
   - [Common transport layer (L4) protocols](#common-transport-layer-l4-protocols)
      - [UDP](#udp)
      - [TCP](#tcp)
   - [Common application layer (L7) protocols](#common-application-layer-l7-protocols)
      - [HTTP](#http)
      - [RPC](#rpc)
      - [WebSocket](#websocket)

## OSI model
| Number | Name | Protocol Data Unit | Decription | Common Protocols |
|----|----|----|----|----|
| 7 | Application | Data | High-level APIs. | HTTP (HTTP/1, HTTP/2), HTTPS, RPC, SOAP, WebSocket, FTP, SFTP, SMTP, LDAP, SSH, DHCP, DNS  |
| 6 | Presentation | Data | Translation of data between a networking service and an application. | |
| 5 | Session | Data | Managing communication sessions. | |
| 4 | Transport | Segment, Datagram | Reliable transmission of data segments between points on a network. | TCP, UDP, TLS/SSL |
| 3 | Network | Packet | Structuring and managing a multi-node network. | IP (IPv4, IPv6) |
| 2 | Data Link | Frame | Reliable transmission of data frames between two nodes connected by a physical layer. | |
| 1 | Physical | Bit, Symbol | Transmission and reception of raw bit streams over a physical medium. | |

## Common protocols
### Common transport layer (L4) protocols
#### UDP
- **Features**
   - Connectionless
   - Unreliable
#### TCP
- **Features**
   - Connection-based
   - Reliable
 
### Common application layer (L7) protocols
#### HTTP
- **Concepts**
   - A request–response protocol in the client–server model:
   - Rely on TCP/IP standard.
- **Features**
   - Stateless: The web server doesn't retain information or status about each user for the duration of multiple requests.
   - Can be stateful: HTTP cookies allow the web server retain information or status (session) about each user for the duration of multiple requests.
- **Request and response**
   - Request
      - Structure
         - Method
         - URL/Path
         - Protocol version
         - Header(s)
         - Body
      - Methods
        | Method | Description |
        |----|----|
        | GET | Retrieves data without making changes. |
        | HEAD | Retrieves the metadata of data in the response headers without the response body. |
        | POST | Submits data and ask the server to process. |
        | PUT | Creates or updates data. |
        | DELETE | Deletes data. |
        | CONNECT | Asks proxy server to establish a TCP/IP tunnel to the origin server. |
        | OPTIONS | Returns all the supported HTTP methods. |
        | PATCH | Updates data partially. |
        
   - Response
      - Structure
         - Protocol version
         - Status code
         - Status message
         - Header(s)
         - Body
      - Status code
        | Code | Type | Description |
        |----|----|----|
        | 1XX | Informational | The request was received, continuing process. |
        | 2XX | Successful | The request was successfully received, understood, and accepted. |
        | 3XX | Redirection | Further action needs to be taken in order to complete the request. |
        | 4XX | Client error | The request contains bad syntax or cannot be fulfilled. |
        | 5XX | Server error | The server failed to fulfill an apparently valid request. |
- **Techniques**
   - HTTP polling
   - HTTP long polling
      - Concepts
         - The server doesn't respond the client immediately when it receives a request from the client.
         - The server holds the connection and responds only if any new message is available or if a timeout threshold is reached.
      - Pros
         - The client doesn't need to send requests frequently to check any new message is available or not.
      - Cons
         - The server need to maintain lots of open connections.
   - HTTP streaming

## References
- https://en.wikipedia.org/wiki/Application_layer
- https://stackoverflow.com/questions/12555043/my-understanding-of-http-polling-long-polling-http-streaming-and-websockets
