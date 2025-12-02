# Endpoint Template

Use this template to document individual API endpoints. Copy this file and replace the placeholder content with your actual endpoint details.

---

# Endpoint Name

Brief description of what this endpoint does and when a developer would use it.

## Request

```
METHOD /path/to/endpoint
```

### Authentication

Specify the authentication method required (API key, Bearer token, OAuth, etc.).

```
Authorization: Bearer YOUR_API_TOKEN
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `Content-Type` | Yes | Must be `application/json` |
| `Authorization` | Yes | Bearer token for authentication |

### Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `id` | string | Yes | Unique identifier for the resource |

### Query Parameters

| Parameter | Type | Required | Default | Description |
|-----------|------|----------|---------|-------------|
| `limit` | integer | No | 10 | Maximum number of results to return |
| `offset` | integer | No | 0 | Number of results to skip |

### Request Body

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | Yes | Display name for the resource |
| `description` | string | No | Optional description |

#### Example Request

```bash
curl -X POST https://api.example.com/v1/resource \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "My Resource",
    "description": "An example resource"
  }'
```

## Response

### Success Response

**Status Code:** `201 Created`

```json
{
  "id": "abc123",
  "name": "My Resource",
  "description": "An example resource",
  "created_at": "2025-01-15T10:30:00Z"
}
```

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier assigned by the API |
| `name` | string | Display name provided in the request |
| `description` | string | Description if provided, otherwise `null` |
| `created_at` | string | ISO 8601 timestamp of creation |

## Errors

| Status Code | Error Type | Description |
|-------------|------------|-------------|
| `400` | `invalid_request` | Request body is malformed or missing required fields |
| `401` | `unauthorized` | API token is missing or invalid |
| `403` | `forbidden` | API token does not have permission for this action |
| `404` | `not_found` | The requested resource does not exist |
| `429` | `rate_limited` | Too many requests; retry after the time specified in `Retry-After` header |

### Example Error Response

```json
{
  "error": {
    "type": "invalid_request",
    "message": "The 'name' field is required",
    "field": "name"
  }
}
```

## Code Examples

### JavaScript (fetch)

```javascript
const response = await fetch('https://api.example.com/v1/resource', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer YOUR_API_TOKEN',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    name: 'My Resource',
    description: 'An example resource'
  })
});

const data = await response.json();
console.log(data.id);
```

### Python (requests)

```python
import requests

response = requests.post(
    'https://api.example.com/v1/resource',
    headers={
        'Authorization': 'Bearer YOUR_API_TOKEN',
        'Content-Type': 'application/json'
    },
    json={
        'name': 'My Resource',
        'description': 'An example resource'
    }
)

data = response.json()
print(data['id'])
```

## Related Endpoints

- [List Resources](./list-resources.md) — Retrieve all resources
- [Get Resource](./get-resource.md) — Retrieve a single resource by ID
- [Delete Resource](./delete-resource.md) — Remove a resource

---

## Template Notes (delete this section when using)

**Checklist before publishing:**

- [ ] Replace all placeholder values (YOUR_API_TOKEN, example.com, etc.)
- [ ] Verify request/response examples match actual API behavior
- [ ] Test code samples to ensure they work when copied
- [ ] Confirm all error codes are documented
- [ ] Link to related endpoints
