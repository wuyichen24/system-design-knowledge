# REST API Best Practices

- [**Best practices**](#best-practices)
   - [Use JSON as payload](#use-json-as-payload)
   - [Use nouns instead of verbs in URL](#use-nouns-instead-of-verbs-in-url)
   - [Name collections with plural nouns](#name-collections-with-plural-nouns)
   - [Use proper status code for error handling](#use-proper-status-code-for-error-handling)
   - [Allow versioning](#allow-versioning)
   - [Allow filtering, sorting, and pagination](#allow-filtering-sorting-and-pagination)
   - [Use SSL for security](#use-ssl-for-security)

## Best practices
### Use JSON as payload
- **Concept**
   - Use JSON as the format for request payload and response payload.
   - If use JSON as the request payload and response payload, add the header `Content-Type` as `application/json`.

### Use nouns instead of verbs in URL
- **Concept**
   - Shouldn't use verbs in the URL. Instead, we should use the nouns which represent the entity that the endpoint that we're retrieving or manipulating.
- **Examples**
   - *Good*
     ```
     GET http://mysite.com/users
     GET http://mysite.com/user/:id
     ```
   - *Bad*
     ```
     GET http://mysite.com/getUsers
     GET http://mysite.com/getUser/:id
     ```

### Name collections with plural nouns
- **Concept**
   - If your API returns a colleciton of entities, the resource name should use plural nouns
- **Example**
   - *Good* (return a list of users)
     ```
     GET http://mysite.com/users
     ```
   - *Bad* (return a list of users)
     ```
     GET http://mysite.com/user
     ```

### Use proper status code for error handling
- **Concept**
   - Return HTTP response codes that indicate what kind of error occurred.
- **Categories of status code**
  | Code | Type | Description |
  |----|----|----|
  | 1XX | Informational | The request was received, continuing process. |
  | 2XX | Successful | The request was successfully received, understood, and accepted. |
  | 3XX | Redirection | Further action needs to be taken in order to complete the request. |
  | 4XX | Client error | The request contains bad syntax or cannot be fulfilled. |
  | 5XX | Server error | The server failed to fulfill an apparently valid request. |
- **Common status codes**
   - *Success (2XX)*
      - 200 - OK: The request was successful, and the server has returned the requested data.
      - 201 - Created: The request resulted in the creation of a new resource.
      - 204 - No Content: The request was successful, but there is no response body (commonly used in DELETE requests).
   - *Client-error (4XX)*
      - 400 - Bad Request: The server couldn't understand the client's request due to syntax errors or invalid parameters.
      - 401 - Unauthorized: The client must provide authentication credentials to access the resource.
      - 403 - Forbidden: The client is authenticated but not permitted to access the requested resource.
      - 404 - Not Found: The requested resource does not exist on the server.
   - *Server-error (5XX)*
      - 500 - Internal Server Error: An unexpected server error occurred while processing the request.
      - 502 - Bad Gateway: The server, while acting as a gateway, received an invalid response from the upstream server.
      - 503 - Service Unavailable: The server is currently unable to handle the request due to temporary overloading or maintenance.
      - 504 - Gateway Timeout: The server, while acting as a gateway, did not receive a timely response from the upstream server.

### Use proper method for operation
- **Concept**
   - Use proper HTTP method for different operations
- **Common methods**
   - GET: Retrieve data
   - POST: Create data
   - PUT: Update data
   - DELETE: Remove data

### Allow versioning
- **Concept**
   - We should have different versions of API if we're making any changes to them that may break clients.
- **Example**
  ```
  GET http://mysite.com/v1/users
  GET http://mysite.com/v2/users
  ```

### Allow filtering, sorting, and pagination
- **Concept**
   - We should use filtering and pagination to reduce the size of the response.
   - We should use sorting to provide the result in more meaningful order.

### Use SSL for security
- **Concepts**
   - Use `https` rather than `http` in the URL.
- **Example**
   - *Good*
     ```
     GET https://mysite.com/v1/users
     ```
   - *Bad*
     ```
     GET http://mysite.com/v1/users
     ```
