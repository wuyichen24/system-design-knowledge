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
      - With TCP, application layer data is segmented. The transport layer still ignores message boundaries.
- **Connection**
   - *Establish (The 3-way handshake)*
      - Step 1
         - Client:
            - The client initiates a connection by sending a SYN segment, enters into the SYN-SENT state.
            - It assigns a random number to the sequence number, known as the Initial Sequence Number (ISN).
      - Step 2:
         - Server:
            - After receiving the SYN segment, the server assigns a random number to the sequence number and sets the acknowledgment number to `client_isn+1`
            - The server sets both the SYN and ACK control bits to 1 and sends this segment back to the client, enters the SYN-RECEIVED state.
      - Step 3:
         - Client:
            - After receiving the SYN+ACK segment, the client sends back an ACK segment and enter to the ESTABLISHED state.
         - Server
            - After receiving the ACK segment, the server enters the ESTABLISHED state too.
   - *Close (The 4-way handshake)*
      - Step 1
         - Client: Initiates by sending a FIN segment to the server, transitioning into the FIN_WAIT_1 state.
      - Step 2:
         - Server: After receiving the FIN segment, the server responds with an ACK segment and enters the CLOSE_WAIT state.
         - Client: After receiving the ACK segment, the client enters the FIN_WAIT_2 state.
      - Step 3:
         - Server: After the server finishes processing, the server sends a FIN segment and enters the LAST_ACK state.
      - Step 4:
         - Client:
            - After receiving the FIN segment, the client sends an ACK segment and enters the TIME_WAIT state.
            - After waiting for a 2MSL (Maximum Segment Lifetime) duration, the client enters to the CLOSED state too.
         - Server: After receiving the ACK segment, the server enters to the CLOSED state.

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
![tcp_udp](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/c9357a6c-6255-4c6f-b986-c1b479152d4b)
