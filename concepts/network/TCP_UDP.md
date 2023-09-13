# TCP and UDP

## TCP
- **Full name**
   - Transmission Control Protocol
- **Characteristics**
   - *Connection-oriented*
      - TCP establishes a connection between the sender and receiver before data transfer begins.
   - *Reliable*
      - TCP is highly reliable. It uses acknowledgment and retransmissions to ensure that data is delivered without errors.
   - *Delivery in order*
      - TCP ensures that data is delivered in the same order it was sent.
   - *Point-to-point/Unicast*
      - TCP establishes a connection between two specific servers.
   - *Larger header*
      - TCP has a larger header (20 bytes).
   - *Flow control and congestion control*
      - TCP provides flow control and congestion control mechanisms to prevent network congestion and ensure fair bandwidth usage.
   - *Error detection*
      - TCP includes error-checking mechanisms like checksums to detect and discard corrupted data.
   - *Bitstream-oriented*
      - 
## UDP
- **Full name**
   - User Datagram Protocol
- **Characteristics**
   - *Connectionless*
      - UDP does not establish a connection before sending data.
   - *Less reliable*
      - UDP does not guarantee reliability. It does not use acknowledgments or retransmissions to ensure that data is delivered without errors.
   - *Orderless*
      - UDP does not guarantee that data is delivered in the same order it was sent.
   - *Multicast*
      - UDP allows one servers to send data to one or multiple servers.
   - *Smaller header*
      - TCP has a smaller header (20 bytes).

## Comparison
| | TCP | UPD |
|----|----|----|
| Connection | Connection-oriented | Connectionless |
| Reliability | More reliable | Less reliable |
| Delivery order | In order | Orderless |
| Header size | Large (20 bytes) | Small (8 bytes) |
| Number of receivers | 1 (P2P) | 1 or multiple (Multicast) | 
| Congestion control | Yes | No |
| Flow control | Yes | No |
| Error detection | Robust | Not robustl | 
