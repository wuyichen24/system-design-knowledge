# REST API Best Practices

## Best practices
### Use nouns instead of verbs in URL
- **Concept**
   - Shouldn't use verbs in the URL. Instead, we should use the nouns which represent the entity that the endpoint that we're retrieving or manipulating.
- **Examples**
   - Good
     ```
     GET http://mysite.com/users
     GET http://mysite.com/user/:id
     ```
   - Bad
     ```
     GET http://mysite.com/getUsers
     GET http://mysite.com/getUser/:id
     ```
