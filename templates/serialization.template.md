# Serialization: [FEATURE_NAME]

> Data transformation and serialization rules for API responses.

## Response Mapping

### [Resource] Object

| Entity field    | API response field | Type      | Notes                        |
| --------------- | ------------------ | --------- | ---------------------------- |
| `id`            | `id`               | string    | UUID format                  |
| `name`          | `name`             | string    |                              |
| `created_at`    | `created_at`       | string    | ISO 8601                     |
| `updated_at`    | `updated_at`       | string    | ISO 8601                     |

### Fields to Exclude

- _List fields that must never appear in API responses (e.g., password_hash)_

### Computed Fields

| Field         | Source                         | Notes              |
| ------------- | ------------------------------ | ------------------- |
| _field_       | _how it's computed_            | _include when_      |

### Nested Relationships

- _Describe when and how related entities are included or excluded_
- _Describe eager vs lazy loading decisions_
