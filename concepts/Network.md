# Network

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
   - Rely on TCP/IP connection.
- **Features**
   - Stateless: The web server doesn't retain information or status about each user for the duration of multiple requests.
   - Can be stateful: HTTP cookies allow the web server retain information or status (session) about each user for the duration of multiple requests.
- **Request and response**
   - Request
      - Methods
   - Response
      - Status code
        | Code | Type | Description |
        |----|----|----|
        | 1XX | Informational | The request was received, continuing process. |
        | 2XX | Successful | The request was successfully received, understood, and accepted. |
        | 3XX | Redirection | Further action needs to be taken in order to complete the request. |
        | 4XX | Client error | The request contains bad syntax or cannot be fulfilled. |
        | 5XX | Server error | The server failed to fulfill an apparently valid request. |
- Techniques
   - HTTP polling
   - HTTP long polling
   - HTTP streaming

#### RPC
- Concepts
   - Allows a computer program to cause a procedure to execute in another address space (commonly on another computer on a shared network).
- Pros
   - Efficient for exchanging large data.
   - Bidirectional streaming.
- Cons
   - Hard to debug.
   - Not flexible.
   - Old firewalls don’t support HTTP/2-based RPCs (Cannot be used for public APIs).

#### WebSocket
- Pros
   - Full duplex: Client and server can send data at the same time.
   - Connections can keep open for the duration of the session.

## References
- https://en.wikipedia.org/wiki/WebSocket
- https://en.wikipedia.org/wiki/Application_layer
- https://stackoverflow.com/questions/12555043/my-understanding-of-http-polling-long-polling-http-streaming-and-websockets
