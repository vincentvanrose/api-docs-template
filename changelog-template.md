# Changelog Template

Use this template to document API changes, new features, and bug fixes. Consistent release notes help developers understand what changed and whether they need to take action.

---

# Changelog

All notable changes to the [Product Name] API are documented here.

This changelog follows [Semantic Versioning](https://semver.org/) and the format is based on [Keep a Changelog](https://keepachangelog.com/).

## [Unreleased]

Changes that are merged but not yet released.

---

## [1.2.0] - 2025-02-15

### Added

- New `GET /v1/users/{id}/activity` endpoint to retrieve user activity history
- Support for filtering resources by `created_after` and `created_before` query parameters
- Webhook event `resource.archived` fires when a resource is archived

### Changed

- The `GET /v1/resources` endpoint now returns a maximum of 100 items per page (previously 50)
- Error responses now include a `request_id` field for easier debugging

### Deprecated

- The `v1/legacy/users` endpoints are deprecated and will be removed in v2.0.0. Use `v1/users` instead.

### Fixed

- Fixed an issue where `null` values in optional fields caused `400 Bad Request` errors
- Corrected rate limit headers to accurately reflect remaining requests

---

## [1.1.0] - 2025-01-20

### Added

- OAuth 2.0 PKCE support for mobile and single-page applications
- New `status` field on all resources (`active`, `pending`, `archived`)
- Bulk operations: `POST /v1/resources/bulk` to create multiple resources in one request

### Changed

- Improved error messages to include more specific details about validation failures
- The `updated_at` field now uses millisecond precision

### Security

- API keys are now hashed using SHA-256 before storage
- Added rate limiting per API key (1000 requests/minute)

---

## [1.0.1] - 2025-01-10

### Fixed

- Fixed pagination returning duplicate items when resources were modified during iteration
- Resolved timeout issues on `GET /v1/resources` with large datasets

---

## [1.0.0] - 2025-01-01

Initial public release.

### Added

- Core API endpoints for resources, users, and teams
- API key authentication
- Webhook support for `resource.created`, `resource.updated`, `resource.deleted` events
- Rate limiting (500 requests/minute)
- SDKs for JavaScript, Python, and Ruby

---

## Change Type Definitions

Use these categories consistently:

| Category | When to use |
|----------|-------------|
| **Added** | New features, endpoints, fields, or capabilities |
| **Changed** | Changes to existing functionality (non-breaking) |
| **Deprecated** | Features that will be removed in a future version |
| **Removed** | Features that have been removed |
| **Fixed** | Bug fixes |
| **Security** | Security improvements or vulnerability fixes |

## Writing Good Changelog Entries

### Be specific

| ❌ Vague | ✅ Specific |
|----------|-------------|
| "Performance improvements" | "Reduced response time for `GET /v1/resources` by 40%" |
| "Bug fixes" | "Fixed pagination returning duplicate items" |
| "New features" | "Added `GET /v1/users/{id}/activity` endpoint" |

### Focus on impact

Tell developers what changed and why they should care.

| ❌ Implementation-focused | ✅ Impact-focused |
|---------------------------|-------------------|
| "Refactored authentication middleware" | "Improved authentication error messages to include specific reasons for failure" |
| "Updated database schema" | "The `status` field now supports `archived` as a value" |

### Call out breaking changes

If a change requires developers to update their code, make it unmissable:

```markdown
### ⚠️ Breaking Changes

- The `user_id` field has been renamed to `user` across all endpoints
- Removed support for API version 2023-01
```

### Include migration guidance

For significant changes, tell developers what to do:

```markdown
### Changed

- The `data` field in webhook payloads is now nested under `payload.data`

  **Migration:** Update your webhook handlers to access `event.payload.data` instead of `event.data`. The old structure will be removed in v2.0.0.
```

---

## Template Notes (delete this section when using)

**Changelog best practices:**

- Update the changelog with every PR, not just at release time
- Keep an `[Unreleased]` section for changes not yet deployed
- Link version numbers to git tags or release pages
- Date format should be ISO 8601 (YYYY-MM-DD)

**Checklist before release:**

- [ ] All changes since last release are documented
- [ ] Breaking changes are clearly marked
- [ ] Migration guidance provided where needed
- [ ] Version number follows semver correctly
- [ ] Release date is accurate
