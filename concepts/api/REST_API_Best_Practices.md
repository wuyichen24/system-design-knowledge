# REST API Best Practices

- [**Best practices**](#best-practices)
   - [Use JSON as payload](#use-json-as-payload)
   - [Use nouns instead of verbs in URL](#use-nouns-instead-of-verbs-in-url)
   - [Name collections with plural nouns](#name-collections-with-plural-nouns)
   - [Use proper status code for error handling](#use-proper-status-code-for-error-handling)
   - [Use proper method for operation](#use-proper-method-for-operation)
   - [Use nesting in URL for nesting resources](#use-nesting-in-url-for-nesting-resources)
   - [Allow versioning](#allow-versioning)
   - [Allow filtering, sorting, and pagination](#allow-filtering-sorting-and-pagination)
   - [Use SSL for security](#use-ssl-for-security)
   - [Get smaller chunks for large binary resources](#get-smaller-chunks-for-large-binary-resources)
- [**References**](#references)

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
     GET http://api.example.com/users
     GET http://api.example.com/user/:id
     ```
   - *Bad*
     ```
     GET http://api.example.com/getUsers
     GET http://api.example.com/getUser/:id
     ```

### Name collections with plural nouns
- **Concept**
   - If your API returns a colleciton of entities, the resource name should use plural nouns
- **Example**
   - *Good* (return a list of users)
     ```
     GET http://api.example.com/users
     ```
   - *Bad* (return a list of users)
     ```
     GET http://api.example.com/user
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
   - GET: Retrieve data.
   - POST: Create data.
   - PUT: Create or replace data.
   - PATCH: Update data partially
   - DELETE: Remove data.

### Use nesting in URL for nesting resources
- **Concept**
   - If one resource is nested in another resource, it would better to reflect the resting relationship in URL
- **Example**
  ```
  https://api.example.com/posts/123/comments
  https://api.example.com/posts/123/comments/456
  ```

### Allow versioning
- **Concept**
   - We should have different versions of API if we're making any changes to them that may break clients.
- **Strategies and examples**
   - *URL versioning*
      - Add version number in URL.
        ```
        GET http://api.example.com/v1/users
        GET http://api.example.com/v2/users
        ```
   - *Query parameter versioning*
      - Add version number as a query parameter.
        ```
        GET http://api.example.com/users?version=1
        GET http://api.example.com/users?version=2
        ```
   - *Header versioning*
      - Add version number in header.
        ```
        GET http://api.example.com/users
        Custom-Header: api-version=1
        ```
   - *Media type versioning*
      - Add version number in media type.
        ```
        GET http://api.example.com/users
        Accept: application/example.v1+json
        ```

### Allow filtering, sorting, and pagination
- **Concept**
   - We should use filtering and pagination to reduce the size of the response.
   - We should use sorting to provide the result in more meaningful order.
- **Example**
   - *Filtering*
     ```
     GET http://api.example.com/user?lastName=Smith&age=30
     ```
   - *Sorting*
     ```
     GET https://api.example.com/products?sort=price&order=desc
     ```
   - Pagination
     ```
     https://api.example.com/articles?page=3&per_page=15
     https://api.example.com/orders?limit=25&offset=50
     ```

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

### Get smaller chunks for large binary resources
- **Concept**
   - Get smaller chunks of large binary resources (files or images) by `Range` header.
- **How to do**
   - *Step 1*: Use `HEAD` method to get the total size of the file
      - Description
         - A HEAD request is similar to a GET request, except that it only returns the HTTP headers that describe the resource, with an empty message body.
      - Request
        ```
        HEAD http://api.example.com/v1/image
        ```
      - Response
        ```
        HTTP/1.1 200 OK

        Accept-Ranges: bytes        // indicates that the corresponding GET operation supports partial results.
        Content-Type: image/jpeg
        Content-Length: 4580        // total image size
        ```
   - *Step 2*: Use `GET` method with `Range` header to get smaller chunks.
      - Description
         - Use `Range` header to specify which range of the file you want to get.
      - Request 1 (get first 2500 bytes)
        ```
        GET http://api.example.com/v1/image
        Range: bytes=0-2499
        ```
      - Request 2 (get rest bytes)
        ```
        GET http://api.example.com/v1/image
        Range: bytes=2500-4579
        ```

## References
- [Microsoft | RESTful web API design](https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design)
- [The Web API Checklist - 43 Things To Think About When Designing, Testing, and Releasing your API](https://mathieu.fenniak.net/the-api-checklist/)
- [Microsoft Azure REST API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/azure/Guidelines.md)
- [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
