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
- **Concepts**
- **Pros**
- **Cons**

## RPC
- **History**
- **Concepts**
- **Pros**
- **Cons**
