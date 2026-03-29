# Serialization: Example Feature

> Data transformation and serialization rules for API responses.

## Response Mapping

### Item Object

| Entity field    | API response field | Type      | Notes                        |
| --------------- | ------------------ | --------- | ---------------------------- |
| `id`            | `id`               | string    | UUID format                  |
| `title`         | `title`            | string    |                              |
| `description`   | `description`      | string    | `null` if not set            |
| `status`        | `status`           | string    | `"active"` or `"archived"`   |
| `created_by`    | `created_by`       | string    | User UUID                    |
| `created_at`    | `created_at`       | string    | ISO 8601 with timezone       |
| `updated_at`    | `updated_at`       | string    | ISO 8601 with timezone       |

### Fields to Exclude

- Internal database fields (e.g., `_id`, `__v`)
- Soft delete markers if using soft delete internally

### Null Handling

- `description`: include as `null` when not set (do not omit)
- All other fields: always present, never null

### Date Format

- Format: `2024-01-15T10:30:00Z`
- Timezone: always UTC
- Precision: seconds (no milliseconds unless needed)
