# Feature: Example Feature

> Version: example-feature-01 | Status: Complete (Reference Example) | Created: 2024-01-15

## Overview

A generic CRUD feature for managing "Items". This is a reference implementation demonstrating the cofihy contract system. It covers creation, listing, updating, archiving, and deleting items with ownership-based access control.

## Previous Version

- Previous: none (initial version)

---

## Contract Files

### API Contract

| File | Description |
| ---- | ----------- |
| [openapi.yaml](../../api/example-feature-01/openapi.yaml) | OpenAPI 3.0 spec -- CRUD endpoints for items |

### Domain Rules

| File | Description |
| ---- | ----------- |
| [glossary.md](../../domain/example-feature-01/glossary.md) | Domain terms: Item, Owner, Status, Archive, Restore |
| [entities.md](../../domain/example-feature-01/entities.md) | Item entity fields, relationships, lifecycle states |
| [rules.md](../../domain/example-feature-01/rules.md) | Business rules: unique titles, owner-only access, archive constraints |
| [permissions.md](../../domain/example-feature-01/permissions.md) | Role-based access: authenticated, owner, unauthenticated |

### Frontend Expectations

| File | Description |
| ---- | ----------- |
| [screens.md](../../frontend/example-feature-01/screens.md) | Item List and Item Detail screens: data needs, UI elements, actions |
| [forms.md](../../frontend/example-feature-01/forms.md) | Create and Edit forms: fields, validation timing, error mapping |

### Backend Expectations

| File | Description |
| ---- | ----------- |
| [validation.md](../../backend/example-feature-01/validation.md) | Field validation rules per endpoint, business rule validation |
| [serialization.md](../../backend/example-feature-01/serialization.md) | Response field mapping, null handling, date format |

### Decision Records

| File | Description |
| ---- | ----------- |
| [001-scope.md](../../decisions/example-feature-01/001-scope.md) | Why a generic "Item" CRUD was chosen as the example |
| [002-api-shape.md](../../decisions/example-feature-01/002-api-shape.md) | REST URL patterns, envelope format, pagination design |

### Examples

| File | Description |
| ---- | ----------- |
| [create-request.json](../../examples/example-feature-01/create-request.json) | Example POST body for creating an item |
| [create-response.json](../../examples/example-feature-01/create-response.json) | Example 201 response after creation |
| [list-response.json](../../examples/example-feature-01/list-response.json) | Example paginated list response |
| [error-response.json](../../examples/example-feature-01/error-response.json) | Example 422 validation error response |

### Generated Artifacts

| Directory | Description |
| --------- | ----------- |
| [generated/](../../generated/example-feature-01/) | Placeholder for generated types, SDK clients, validation schemas |

---

## Stack References

- Frontend rules: [FRONTEND.md](../../FRONTEND.md)
- Backend rules: [BACKEND.md](../../BACKEND.md)
- System overview: [CONTRACT.md](../../CONTRACT.md)

---

## Feature Summary

### Endpoints

| Method | Path               | Description       | Auth |
| ------ | ------------------ | ----------------- | ---- |
| GET    | `/api/v1/items`    | List items        | yes  |
| POST   | `/api/v1/items`    | Create item       | yes  |
| GET    | `/api/v1/items/:id`| Get item          | yes  |
| PUT    | `/api/v1/items/:id`| Update item       | yes  |
| DELETE | `/api/v1/items/:id`| Delete item       | yes  |

### Key Business Rules

1. Item titles must be unique per user
2. Only the owner can update/delete their items
3. Archived items cannot be updated
4. Title cannot be empty or whitespace-only

### Entity States

- `active` (default on creation)
- `archived` (soft removal, reversible)

---

## Pre-Implementation Checklist

Before starting implementation, verify:

- [x] OpenAPI spec is complete and reviewed
- [x] Domain entities and rules are defined
- [x] Permissions are documented
- [x] Frontend screen data needs are listed
- [x] Form fields and validation rules are specified
- [x] Backend validation rules match frontend expectations
- [x] Request/response examples are provided
- [x] Decision records capture key architectural choices
- [ ] FRONTEND.md is filled in for the current stack
- [ ] BACKEND.md is filled in for the current stack

---

## Expected Generated Artifacts

After implementation, the following should exist in `generated/example-feature-01/`:

- [ ] `[TYPE_SYSTEM]` types for Item, CreateItemRequest, UpdateItemRequest
- [ ] API client functions for all 5 endpoints
- [ ] `[VALIDATION_SYSTEM]` schemas for create and update forms

---

## Notes

This is a reference example. When creating a real feature:

1. Copy the templates from `templates/` instead of duplicating this example
2. Replace `[FEATURE_NAME]` and `[Resource]` placeholders
3. Fill in FRONTEND.md and BACKEND.md for your chosen stack
4. Mark the pre-implementation checklist items as you complete them
