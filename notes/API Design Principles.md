# API Design Principles

## RESTful Best Practices

### Resource Naming
- Use nouns, not verbs: `/users` not `/getUsers`
- Use plural for collections: `/products`
- Use hierarchies: `/users/123/orders`
- Keep it consistent

### HTTP Methods
- **GET**: Retrieve data (idempotent)
- **POST**: Create new resources
- **PUT**: Update entire resource
- **PATCH**: Partial update
- **DELETE**: Remove resource

### Status Codes
- **200 OK**: Successful GET, PUT, PATCH
- **201 Created**: Successful POST
- **204 No Content**: Successful DELETE
- **400 Bad Request**: Client error
- **401 Unauthorized**: Authentication required
- **403 Forbidden**: Authenticated but not allowed
- **404 Not Found**: Resource doesn't exist
- **500 Internal Server Error**: Server error

## JSON Response Structure

### Success Response
```json
{
  "data": {
    "id": 123,
    "name": "John Doe"
  },
  "meta": {
    "timestamp": "2026-01-14T12:00:00Z"
  }
}
```

### Error Response
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid email format",
    "details": [
      {
        "field": "email",
        "issue": "Must be valid email"
      }
    ]
  }
}
```

## Versioning Strategies

1. **URL Path**: `/api/v1/users`
2. **Header**: `Accept: application/vnd.api.v1+json`
3. **Query Parameter**: `/api/users?version=1`

Recommendation: URL path for simplicity

## Pagination

```json
{
  "data": [...],
  "pagination": {
    "page": 1,
    "pageSize": 20,
    "totalPages": 5,
    "totalItems": 100,
    "hasNext": true,
    "hasPrevious": false
  }
}
```

## Security

- Always use HTTPS
- Implement rate limiting
- Validate all input
- Use authentication tokens (JWT)
- Never expose sensitive data
- Log security events

## Documentation

- Use OpenAPI/Swagger
- Provide examples
- Document error responses
- Include rate limits
- Keep it up to date

## Performance

- Implement caching headers
- Use ETags for conditional requests
- Support compression (gzip)
- Enable CORS properly
- Monitor response times
