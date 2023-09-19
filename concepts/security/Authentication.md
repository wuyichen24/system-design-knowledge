# Authentication

## Password Authentication
### Basic Access Authentication
### Session-Cookie Authentication
- **Concepts**
- **Session ID**
   - A session ID is generated to track the user's status during their visit.
   - A session ID is recorded both server-side and in the client’s cookie, serving as an authentication mechanism.
- **How it works**
   - *Get session ID*
      - Client: Sends a request to access a protected resource on the server.
      - Server: Responds with a login prompt to the client.
      - Client: Submits their username and password to the server.
      - Server:
         - Verifies the provided credentials against its user database or authentication service.
         - Generates a unique session ID and creates a corresponding session in the server-side storage.
         - Sends the session ID to the client as a cookie.
      - Client: Stores the session cookie.
   - *Use session ID*
- **Pros**
- **Cons**
### Token-Based Authentication
#### Basic Token Authentication
#### JWT (JSON Web Token) Authentication 
## Passwordless Authentication
