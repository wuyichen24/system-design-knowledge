# HTTP

## Concepts
- A request–response protocol in the client–server model.

## Features
- *Stateless*
   - The server doesn't retain information or status about each user for the duration of multiple requests.
- *Can be stateful*
   - HTTP cookies allow the web server retain information or status (session) about each user for the duration of multiple requests.

## Request and response
### Request
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
