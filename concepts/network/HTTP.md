# HTTP

## Full name
- HyperText Transfer Protocol

## Concepts
- A request–response protocol in the client–server model.

## Features
- *Stateless*
   - The server doesn't retain information or status about each user for the duration of multiple requests.
- *Can be stateful*
   - HTTP cookies allow the web server retain information or status (session) about each user for the duration of multiple requests.

## Versions
### HTTP/1.0
- **Transport protocol**
   - TCP
- **Limitations**
   - Each request to the same server required a separate TCP connection.

### HTTP/1.1
- **Transport protocol**
   - TCP
- **Features**
   - *Persistent connection*
      - A TCP connection could be left open for reuse.
- **Limitations**
   - *'Head-of-Line' (HOL) blocking*
      - When all parallel request slots in a browser are filled, forcing subsequent requests to wait until previous ones are complete.

### HTTP/2.0
- **Transport protocol**
   - TCP
- **Features**
   - *Multiplexing*
      - Allows multiple requests and responses to be interleaved over a single connection.
      - Eliminates HOL blocking at the application layer
   - *HTTP streaming*
      - Allows the multiplexing of different HTTP exchanges onto the same TCP connection, freeing us from the need to send each stream in order.
- **Limitations**
   - *HOL blocking at transport layer*
      - HTTP/2.0 eliminates HOL blocking at the application layer, but HOL blocking could still occur at the transport layer (TCP).

### HTTP/3.0
- **Transport protocol**
   - QUIC (based on UDP)
- **Features**
   - *Use QUIC*
      - HTTP/3.0 is based UDP rather than TCP.
      - Eliminates HOL blocking at both the application layer and transport layer.
   - *QUIC streams*
      - QUIC streams share the same QUIC connection, requiring no additional handshakes or slow starts to create new ones.
      - QUIC streams are delivered independently. It means that in most cases packet loss in one stream doesn't impact others.

## Request and response
### Request
- **Structure**
   - Method
   - URL/Path
   - Protocol version
   - Header(s)
   - Body
- **Methods**
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
        
### Response
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

## Techniques
### HTTP polling
### HTTP long polling
- Concepts
   - The server doesn't respond the client immediately when it receives a request from the client.
   - The server holds the connection and responds only if any new message is available or if a timeout threshold is reached.
- Pros
   - The client doesn't need to send requests frequently to check any new message is available or not.
- Cons
   - The server need to maintain lots of open connections.

### HTTP streaming

## References
- https://stackoverflow.com/questions/12555043/my-understanding-of-http-polling-long-polling-http-streaming-and-websockets
