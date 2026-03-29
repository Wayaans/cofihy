# Backend Stack Contract

> Project-level reference defining how the backend stack works and what the contract must follow.

## Purpose

This file documents the backend framework conventions, patterns, and constraints that all feature contracts must respect. Fill this in once per project after choosing your backend stack.

---

## Stack Profile

| Field                | Value                  |
| -------------------- | ---------------------- |
| Framework            | `[BACKEND]`            |
| Language             | `[BACKEND_LANGUAGE]`   |
| API style            | `[API_STYLE]`          |
| ORM / data layer     | `[ORM]`                |
| Validation library   | `[VALIDATION_SYSTEM]`  |
| Auth strategy        | `[AUTH_STRATEGY]`      |
| Testing framework    | `[TEST_FRAMEWORK]`     |
| Type system          | `[TYPE_SYSTEM]`        |

---

## API Style

- Style: `[API_STYLE]` (REST / GraphQL / tRPC / gRPC)
- URL convention: _`/api/v1/resource` or describe_
- HTTP methods: _standard REST verbs or describe_
- Versioning strategy: _URL path / header / none_

---

## Response Envelope Conventions

```json
{
  "data": {},
  "meta": {},
  "message": "string"
}
```

- All successful responses must use this envelope: _yes / no_
- Pagination metadata location: _`meta` object / headers / Link header_
- Empty responses: _`204 No Content` / empty `data`_

---

## Error Format Conventions

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Human-readable message",
    "details": []
  }
}
```

- Error codes: _uppercase snake_case_
- HTTP status mapping: _describe which codes map to which status_
- Stack traces in errors: _never in production_

---

## Validation Response Conventions

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [
      { "field": "email", "message": "Must be a valid email" }
    ]
  }
}
```

- Field-level errors: _always include `field` and `message`_
- Nested field paths: _dot notation (`address.city`) or describe_
- Validation library: `[VALIDATION_SYSTEM]`

---

## Auth Strategy

- Method: `[AUTH_STRATEGY]` (JWT / session / API key / OAuth)
- Token location: _Authorization header / cookie_
- Token format: _`Bearer <token>` or describe_
- Refresh mechanism: _describe_
- Permission model: _RBAC / ABAC / custom_

---

## Serialization Rules

- Date format: _ISO 8601 (`2024-01-15T10:30:00Z`)_
- Null handling: _omit null fields / include as `null`_
- Case convention: _camelCase / snake_case_
- ID format: _UUID / integer / ULID_
- Enum serialization: _string / integer_

---

## Naming Conventions

- Route paths: _kebab-case (`/user-profiles`)_
- Query params: _camelCase / snake_case_
- Request body fields: _camelCase / snake_case_
- Response body fields: _camelCase / snake_case_
- Database columns: _snake_case_

---

## Type Safety / Data Casting Rules

- Request parsing: _strict typing / loose coercion_
- Query param types: _always strings, cast manually / auto-cast_
- Boolean params: _`true`/`false` strings / `1`/`0`_
- Number params: _string-to-number casting rules_

---

## Pagination Conventions

- Strategy: _offset-based / cursor-based_
- Default page size: _number_
- Max page size: _number_
- Parameters: _`page` + `per_page` / `cursor` + `limit`_
- Response: _total count included / not included_

---

## Filtering / Sorting Conventions

- Filter parameter format: _`?status=active` / `?filter[status]=active`_
- Multiple values: _comma-separated / repeated params_
- Sort parameter: _`?sort=created_at` / `?sort=-created_at` for desc_
- Default sort: _describe_

---

## Date / Time Conventions

- Storage format: _UTC always_
- API input format: _ISO 8601_
- API output format: _ISO 8601 with timezone_
- Timezone handling: _server converts / client converts_

---

## File / Folder Conventions

- Controller/handler location: _describe path pattern_
- Service/business logic location: _describe path pattern_
- Route registration: _describe pattern_
- Middleware location: _describe path pattern_
- Naming convention: _describe file naming_

---

## Testing Expectations

- Unit tests: _required / optional_
- Integration tests: _required / optional_
- API/E2E tests: _required / optional_
- Testing framework: `[TEST_FRAMEWORK]`
- Test database strategy: _in-memory / separate DB / transactions_
- Coverage target: _percentage_

---

## Constraints the Contract Must Follow

- [ ] All endpoints must match the OpenAPI spec exactly
- [ ] Response shapes must match the envelope format above
- [ ] Error responses must use the error format above
- [ ] Validation errors must include field-level details
- [ ] Auth endpoints must follow the auth strategy defined above
- [ ] All dates must use ISO 8601 format
- [ ] Pagination must follow the conventions defined above
- [ ] Naming must follow the conventions defined above

---

## Documentation Checklist

Before considering this file complete, ensure you have documented:

- [ ] Framework name and version
- [ ] API style and URL conventions
- [ ] Response envelope format
- [ ] Error response format
- [ ] Validation error format
- [ ] Auth strategy and token handling
- [ ] Serialization rules (dates, nulls, casing, IDs)
- [ ] Naming conventions (routes, params, fields)
- [ ] Type safety / data casting rules
- [ ] Pagination conventions
- [ ] Filtering / sorting conventions
- [ ] Date / time conventions
- [ ] File / folder conventions
- [ ] Testing expectations

---

## Agent Prompt: Generate Backend Rules

**How to use this prompt:**

1. Replace `[BACKEND]` and `[BACKEND_LANGUAGE]` with your actual stack
2. Open your **backend project** in your coding agent
3. Paste the prompt below into that agent
4. The agent will analyze your backend codebase and produce markdown output
5. Copy the output back into this file, replacing the placeholder sections above

```
You are a backend architecture expert. I am using [BACKEND] with [BACKEND_LANGUAGE] for my project.

Analyze this codebase and generate concise, practical project rules and conventions for a BACKEND.md contract file. This file will be used as a reference by other agents when implementing features from API contracts.

For each of the following sections, provide:
- How this project specifically handles it (based on what you see in the code)
- A short code example or format example where helpful
- Any constraints or gotchas specific to this project

Sections to cover:
1. Stack profile (framework, language, ORM, key libraries used in this project)
2. API style and URL conventions (REST/GraphQL, URL patterns, versioning)
3. Response envelope format (success response shape, collection response shape)
4. Error format conventions (error codes, HTTP status mapping, stack traces)
5. Validation response format (field-level errors, nested field paths)
6. Auth strategy (token handling, middleware pattern, permission model)
7. Serialization rules (dates, nulls, field casing, ID format, enums)
8. Naming conventions (routes, query params, request/response fields, DB columns)
9. Type safety / data casting rules (query params, booleans, numbers)
10. Pagination conventions (strategy, params, response format)
11. Filtering / sorting conventions (parameter format, defaults)
12. Date / time conventions (storage, input, output, timezone handling)
13. File / folder conventions (controllers, services, routes, middleware, naming)
14. Testing expectations (unit, integration, e2e, test DB strategy, coverage)

Keep each section under 5 lines. Be specific to this project, not generic.
Output as markdown sections I can copy-paste directly into BACKEND.md.
```
