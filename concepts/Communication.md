# Communication

## Mechanisms
### REST
- **Concepts**
- **Pros**
   - Simple
   - Easy to debug (You can debug by web browsers, Postman and curl command)
   - Firewall-friendly (Can be used for public APIs).
   - Stateless.
- **Cons**
   - Only supports request-response style.

### RPC
- **Concepts**
   - Allows a computer program to cause a procedure to execute in another address space (commonly on another computer on a shared network).
- **Pros**
   - Efficient for exchanging large data.
   - Bidirectional streaming.
- **Cons**
   - Hard to debug.
   - Not flexible.
   - Old firewalls don’t support HTTP/2-based RPCs (Cannot be used for public APIs).
  
### WebSocket
- **Concepts**
- **Pros**
- **Cons**
