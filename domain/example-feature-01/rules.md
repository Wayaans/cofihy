# Business Rules: Example Feature

> Invariants, constraints, and domain logic.

## Rules

1. **RULE-001**: Item title must be unique per user
   - Enforced by: backend
   - Error if violated: `DUPLICATE_TITLE` (409 Conflict)

2. **RULE-002**: Only the item owner can update or delete their item
   - Enforced by: backend
   - Error if violated: `FORBIDDEN` (403 Forbidden)

3. **RULE-003**: Archived items cannot be updated (only restored)
   - Enforced by: backend
   - Error if violated: `ITEM_ARCHIVED` (422 Unprocessable Entity)

4. **RULE-004**: Title cannot be empty or whitespace-only
   - Enforced by: both frontend and backend
   - Error if violated: `VALIDATION_ERROR` (422)

## Invariants

- An item always has exactly one owner
- An item always has a status of either `active` or `archived`
- `created_at` is immutable after creation
- `updated_at` is updated on every modification
