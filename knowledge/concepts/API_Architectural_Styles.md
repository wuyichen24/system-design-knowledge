# API Architectural Styles

## Overview
- SOAP
- REST
- RPC
   - gRPC
- GraphQL
- Web socket
- Webhook

## SOAP
- **History**
   - 1998
- **Full name**
   - Simple Object Access Protocol
- **Concepts**
   - An XML-formatted, highly standardized web communication protocol.
- **Message**
   - *Format*:
      - XML
   - *Structure*:
      - Envelope: Identifies the XML document as a SOAP message.
      - Header: Contains header information.
      - Body: Contains call and response information.
      - Fault: Provides information about errors that occurred while processing the message.
- **Dependent protocols**
   - Application layer protocol
      - HTTP
      - SMTP
- **Pros**
   - *Platform-independent*
      - Supported by all mainstream platforms.
   - *Language-independent*
      - Supported by all mainstream programming languages.
   - *Error handling*
      - SOAP provides a standardized way to handle errors and exceptions.
   - *Security*
      - SOAP meets an enterprise-grade transaction quality. It provides privacy and integrity inside the transactions while allowing for encryption on the message level.
- **Cons**
   - *Outdated*
   - *Only support XML*
   - *Message is heavyweight*
   - *Need specialized knowledge*
- **Use cases**
   - *Highly secured data transmission*
      - Financial industry
   - *Legacy system*

## REST
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
   - *Layered system*
   - *Code on demand (optional)*
   - *Uniform interface*
- **Message**
- **Dependent protocols**
- **Pros**
- **Cons**

## RPC
- **History**
- **Concepts**
- **Pros**
- **Cons**
