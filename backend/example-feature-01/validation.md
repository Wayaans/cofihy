# Validation: Example Feature

> Backend validation rules and error response mapping.

## Endpoint: `POST /api/v1/items`

### Field Validation

| Field         | Rules                                    | Error message              |
| ------------- | ---------------------------------------- | -------------------------- |
| `title`       | required, string, min:1, max:255         | "Title is required"        |
| `description` | optional, string, max:2000               | "Description is too long"  |
| `status`      | optional, in:[active, archived]          | "Invalid status"           |

### Business Rule Validation

| Rule             | Condition                          | Error code         | HTTP Status |
| ---------------- | ---------------------------------- | ------------------ | ----------- |
| Unique title     | Another item with same title exists| DUPLICATE_TITLE    | 409         |

### Validation Response

On validation failure, return `422`:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [
      { "field": "title", "message": "Title is required" }
    ]
  }
}
```

---

## Endpoint: `PUT /api/v1/items/:id`

### Field Validation

| Field         | Rules                                    | Error message              |
| ------------- | ---------------------------------------- | -------------------------- |
| `title`       | optional, string, min:1, max:255         | "Title cannot be empty"    |
| `description` | optional, string, max:2000               | "Description is too long"  |
| `status`      | optional, in:[active, archived]          | "Invalid status"           |

### Business Rule Validation

| Rule             | Condition                          | Error code         | HTTP Status |
| ---------------- | ---------------------------------- | ------------------ | ----------- |
| Owner only       | Current user != item.created_by    | FORBIDDEN          | 403         |
| Not archived     | Item status is `archived`          | ITEM_ARCHIVED      | 422         |
| Unique title     | Another item with same title exists| DUPLICATE_TITLE    | 409         |

---

## Endpoint: `DELETE /api/v1/items/:id`

### Pre-conditions

| Rule             | Condition                          | Error code         | HTTP Status |
| ---------------- | ---------------------------------- | ------------------ | ----------- |
| Exists           | Item does not exist                | NOT_FOUND          | 404         |
| Owner only       | Current user != item.created_by    | FORBIDDEN          | 403         |
