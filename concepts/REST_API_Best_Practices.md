# REST API Best Practices

## Best practices
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
