# Quickstart Template

Use this template to create getting-started guides that help developers make their first successful API call within minutes.

---

# Quickstart: [Product/API Name]

This guide walks you through making your first API call to [Product Name]. By the end, you'll have [specific outcome, e.g., "retrieved your account information" or "created your first resource"].

**Time to complete:** ~5 minutes

## Prerequisites

Before you begin, make sure you have:

- [ ] A [Product Name] account ([sign up here](https://example.com/signup) if you don't have one)
- [ ] Your API key (find it in your [dashboard](https://example.com/dashboard))
- [ ] [Any other requirements, e.g., "Node.js 16+ installed" or "curl available in your terminal"]

## Step 1: Get Your API Key

1. Log in to your [Product Name] dashboard
2. Navigate to **Settings → API Keys**
3. Click **Create New Key**
4. Copy your key and store it securely—you won't be able to see it again

> ⚠️ **Keep your API key secret.** Don't commit it to version control or share it publicly.

## Step 2: Make Your First Request

Let's verify everything is working by calling the `/me` endpoint, which returns information about your account.

### Using curl

```bash
curl https://api.example.com/v1/me \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Using JavaScript

```javascript
const response = await fetch('https://api.example.com/v1/me', {
  headers: {
    'Authorization': 'Bearer YOUR_API_KEY'
  }
});

const data = await response.json();
console.log(data);
```

### Using Python

```python
import requests

response = requests.get(
    'https://api.example.com/v1/me',
    headers={'Authorization': 'Bearer YOUR_API_KEY'}
)

print(response.json())
```

## Step 3: Check the Response

If everything is set up correctly, you'll see a response like this:

```json
{
  "id": "user_abc123",
  "email": "you@example.com",
  "plan": "developer",
  "created_at": "2025-01-01T00:00:00Z"
}
```

🎉 **Congratulations!** You've made your first API call.

## Common Issues

### "401 Unauthorized"

Your API key is missing or incorrect. Double-check that:
- You included the `Authorization` header
- The key is prefixed with `Bearer ` (note the space)
- You're using the correct key (not a revoked one)

### "403 Forbidden"

Your API key doesn't have permission for this endpoint. Check your key's permissions in the dashboard.

### Connection errors

Make sure you're using `https://` (not `http://`) and that your network allows outbound HTTPS connections.

## Next Steps

Now that you're set up, here are some things to try:

- [Create your first resource](./create-resource.md)
- [Explore the full API reference](./api-reference.md)
- [Set up webhooks](./webhooks.md) to receive real-time updates

## Get Help

- 📖 [Full documentation](https://docs.example.com)
- 💬 [Community Discord](https://discord.example.com)
- 🐛 [Report an issue](https://github.com/example/api/issues)

---

## Template Notes (delete this section when using)

**Tips for effective quickstarts:**

- Keep it under 5 minutes of actual work
- Use the simplest possible endpoint for the first call (often a "get current user" or "list" endpoint)
- Provide code samples in multiple languages
- Anticipate common errors and explain how to fix them
- End with clear next steps so developers know where to go

**Checklist before publishing:**

- [ ] Tested all code samples
- [ ] Verified prerequisites are complete and accurate
- [ ] Checked all links work
- [ ] Removed placeholder URLs and values
