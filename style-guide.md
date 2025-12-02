# Documentation Style Guide

This style guide establishes conventions for writing consistent, clear API documentation. Use it as a reference when creating new docs or reviewing existing content.

---

# Style Guide

## Voice and Tone

### Be direct and concise

Get to the point. Developers are usually looking for specific information, not reading for pleasure.

| ❌ Don't | ✅ Do |
|----------|-------|
| "In order to be able to make a request..." | "To make a request..." |
| "It should be noted that the API requires..." | "The API requires..." |
| "You will need to make sure that you have..." | "You need..." |

### Use second person ("you")

Write as if you're talking directly to the developer.

| ❌ Don't | ✅ Do |
|----------|-------|
| "The user must provide an API key" | "You must provide an API key" |
| "Developers can access the dashboard" | "You can access the dashboard" |

### Use active voice

Active voice is clearer and more direct than passive voice.

| ❌ Don't (passive) | ✅ Do (active) |
|---------------------|----------------|
| "The request is authenticated by the server" | "The server authenticates the request" |
| "An error will be returned if..." | "The API returns an error if..." |

### Be confident, not apologetic

State facts directly. Avoid hedging language.

| ❌ Don't | ✅ Do |
|----------|-------|
| "You might want to try using..." | "Use..." |
| "Perhaps consider checking..." | "Check..." |

## Formatting Conventions

### Headings

- Use sentence case for headings ("Get started with authentication" not "Get Started With Authentication")
- Keep headings short and descriptive
- Use heading levels hierarchically (don't skip from H2 to H4)

### Code formatting

Use backticks for:
- API endpoints: `GET /v1/users`
- Parameter names: `user_id`
- Field names: `created_at`
- Values: `null`, `true`, `"pending"`
- HTTP status codes: `200 OK`, `404 Not Found`
- File names: `config.json`
- Command-line input: `npm install`

### Code blocks

Always specify the language for syntax highlighting:

~~~
```bash
curl https://api.example.com/v1/users
```
~~~

~~~
```json
{
  "id": "user_123",
  "name": "Example User"
}
~~~

### Lists

Use bullet points for unordered items:

- First item
- Second item
- Third item

Use numbered lists only for sequential steps:

1. Create an account
2. Generate an API key
3. Make your first request

### Tables

Use tables for structured reference information like parameters, fields, and error codes. Always include a header row.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | The user's display name |
| `email` | string | Yes | The user's email address |

## Terminology

### Consistent naming

Pick one term and use it everywhere. Don't alternate between synonyms.

| Concept | Use | Don't use |
|---------|-----|-----------|
| Authentication credential | API key | token, secret, key, auth token |
| Unique identifier | ID | identifier, UID, key |
| Request data | request body | payload, data, body |
| API call | request | call, query, hit |

### Technical terms

- **Endpoint** — A specific URL path that accepts requests (e.g., `/v1/users`)
- **Resource** — An object or entity in the API (e.g., a user, an order)
- **Parameter** — A value passed in the URL, query string, or request body
- **Response** — The data returned by the API
- **Scope** — A permission that limits what an API key or token can do

### Placeholder values

Use consistent, obvious placeholders that developers will recognize need replacing:

| Type | Placeholder format | Example |
|------|-------------------|---------|
| API keys | `YOUR_API_KEY` | `Authorization: Bearer YOUR_API_KEY` |
| IDs | Descriptive with prefix | `user_abc123`, `order_xyz789` |
| URLs | `example.com` domain | `https://api.example.com` |
| Emails | `@example.com` domain | `user@example.com` |

## Code Samples

### Make them copy-paste ready

- Use realistic (but fake) values
- Include all required headers
- Show complete, working examples

### Placeholder visibility

Make it obvious what needs to be replaced:

```bash
# Good: Clear placeholder
curl -H "Authorization: Bearer YOUR_API_KEY"

# Bad: Looks like a real value
curl -H "Authorization: Bearer sk_live_abc123def456"
```

### Multiple languages

When providing code samples in multiple languages, maintain consistency:
- Same operation in each language
- Same variable names where possible
- Same order of operations

### Comments

Use comments sparingly to explain non-obvious behavior, not to narrate what the code does:

```javascript
// Good: Explains why
const maxRetries = 3; // API rate limits reset after 60 seconds

// Bad: Just narrates what
const maxRetries = 3; // Set max retries to 3
```

## Error Documentation

### Always include

- HTTP status code
- Error type/code
- Human-readable message
- Common causes
- How to fix it

### Example error format

```
### 404 Not Found

The requested resource doesn't exist.

**Common causes:**
- The resource ID is incorrect
- The resource was deleted
- You don't have permission to view this resource (some APIs return 404 instead of 403 for security)

**How to fix:**
Verify the resource ID and check that the resource hasn't been deleted.
```

## Writing Checklist

Before publishing documentation, verify:

- [ ] All code samples are tested and work
- [ ] Placeholder values are obvious and consistent
- [ ] All links work
- [ ] Language is concise and direct
- [ ] Technical terms are used consistently
- [ ] Examples cover both success and error cases
- [ ] Prerequisites are clearly stated

---

## Template Notes (delete this section when using)

**Adapting this style guide:**

This guide covers general best practices. You should add sections specific to your project:

- Product-specific terminology
- Brand voice guidelines
- Versioning conventions
- Localization requirements
- Accessibility standards
