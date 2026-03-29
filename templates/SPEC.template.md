# Feature: [FEATURE_NAME]

> Version: [FEATURE_NAME]-XX | Status: Draft | Created: YYYY-MM-DD

## Overview

_One-paragraph description of what this feature does and why it exists._

## Previous Version

- Previous: _none / `[FEATURE_NAME]-XX` (link if applicable)_
- Reason for revision: _describe what changed_

---

## Contract Files

### API Contract

| File | Description |
| ---- | ----------- |
| [`../../api/[FEATURE_NAME]-XX/openapi.yaml`](../../api/[FEATURE_NAME]-XX/openapi.yaml) | OpenAPI spec for this feature |

### Domain Rules

| File | Description |
| ---- | ----------- |
| [`../../domain/[FEATURE_NAME]-XX/glossary.md`](../../domain/[FEATURE_NAME]-XX/glossary.md) | Domain terms and definitions |
| [`../../domain/[FEATURE_NAME]-XX/entities.md`](../../domain/[FEATURE_NAME]-XX/entities.md) | Entity definitions and relationships |
| [`../../domain/[FEATURE_NAME]-XX/rules.md`](../../domain/[FEATURE_NAME]-XX/rules.md) | Business rules and invariants |
| [`../../domain/[FEATURE_NAME]-XX/permissions.md`](../../domain/[FEATURE_NAME]-XX/permissions.md) | Permission and access control rules |

### Frontend Expectations

| File | Description |
| ---- | ----------- |
| [`../../frontend/[FEATURE_NAME]-XX/screens.md`](../../frontend/[FEATURE_NAME]-XX/screens.md) | Screen data needs and UI mapping |
| [`../../frontend/[FEATURE_NAME]-XX/forms.md`](../../frontend/[FEATURE_NAME]-XX/forms.md) | Form behavior and field expectations |

### Backend Expectations

| File | Description |
| ---- | ----------- |
| [`../../backend/[FEATURE_NAME]-XX/validation.md`](../../backend/[FEATURE_NAME]-XX/validation.md) | Validation rules and error responses |
| [`../../backend/[FEATURE_NAME]-XX/serialization.md`](../../backend/[FEATURE_NAME]-XX/serialization.md) | Serialization and data transformation |

### Decision Records

| File | Description |
| ---- | ----------- |
| [`../../decisions/[FEATURE_NAME]-XX/001-scope.md`](../../decisions/[FEATURE_NAME]-XX/001-scope.md) | Feature scope decision |

### Examples

| File | Description |
| ---- | ----------- |
| [`../../examples/[FEATURE_NAME]-XX/create-request.json`](../../examples/[FEATURE_NAME]-XX/create-request.json) | Example create request |
| [`../../examples/[FEATURE_NAME]-XX/create-response.json`](../../examples/[FEATURE_NAME]-XX/create-response.json) | Example success response |
| [`../../examples/[FEATURE_NAME]-XX/error-response.json`](../../examples/[FEATURE_NAME]-XX/error-response.json) | Example error response |

### Generated Artifacts

| Directory | Description |
| --------- | ----------- |
| [`../../generated/[FEATURE_NAME]-XX/`](../../generated/[FEATURE_NAME]-XX/) | Generated types, SDKs, or client code |

---

## Stack References

- Frontend rules: [`../../FRONTEND.md`](../../FRONTEND.md)
- Backend rules: [`../../BACKEND.md`](../../BACKEND.md)
- System overview: [`../../CONTRACT.md`](../../CONTRACT.md)

---

## Pre-Implementation Checklist

Before starting implementation, verify:

- [ ] OpenAPI spec is complete and reviewed
- [ ] Domain entities and rules are defined
- [ ] Permissions are documented
- [ ] Frontend screen data needs are listed
- [ ] Form fields and validation rules are specified
- [ ] Backend validation rules match frontend expectations
- [ ] Request/response examples are provided
- [ ] Decision records capture key architectural choices
- [ ] FRONTEND.md and BACKEND.md are filled in for the current stack

---

## Expected Generated Artifacts

After implementation, the following should exist in `generated/[FEATURE_NAME]-XX/`:

- [ ] `[TYPE_SYSTEM]` types for request/response shapes
- [ ] API client functions (if using code generation)
- [ ] Validation schemas (if shared between frontend and backend)

---

## Notes

_Any additional context, constraints, or references._
