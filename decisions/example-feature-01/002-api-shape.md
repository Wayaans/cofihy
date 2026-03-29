# Decision: API Shape

> ADR-002 | Feature: example-feature-01 | Date: 2024-01-15 | Status: Accepted

## Context

Need to decide on the API shape for the Item resource endpoints, including URL structure, HTTP methods, and response format.

## Decision

- Use standard RESTful URL patterns: `/api/v1/items` and `/api/v1/items/:id`
- Use response envelope: `{ "data": {...}, "meta": {...} }`
- Use standard HTTP methods: GET, POST, PUT, DELETE
- Use standard HTTP status codes: 200, 201, 204, 401, 403, 404, 409, 422
- Pagination via query params: `page` and `per_page`
- Sorting via `sort` param with `-` prefix for descending

## Alternatives Considered

1. **GraphQL**: Adds complexity for a simple CRUD feature
2. **Flat response (no envelope)**: Harder to extend with metadata later

## Consequences

- Consistent with most REST API conventions
- Easy to consume from any frontend framework
- Envelope format allows adding metadata without breaking changes
