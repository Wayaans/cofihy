# Entities: Example Feature

> Entity definitions, fields, and relationships.

## Item

| Field         | Type     | Required | Description                    |
| ------------- | -------- | -------- | ------------------------------ |
| `id`          | string   | yes      | Unique identifier (UUID)       |
| `title`       | string   | yes      | Item title, 1-255 chars        |
| `description` | string   | no       | Optional description, max 2000 |
| `status`      | enum     | yes      | `active` or `archived`         |
| `created_by`  | string   | yes      | User ID of the creator         |
| `created_at`  | datetime | yes      | ISO 8601 creation timestamp    |
| `updated_at`  | datetime | yes      | ISO 8601 last update           |

### Relationships

- **Owner**: Each item belongs to one user (`created_by` -> User.id)
- An item has no child entities in this version

### Lifecycle / States

```
[created] --> active --> archived
                ^           |
                |           |
                +-----------+
                 (restore)
```

- Items are created in `active` status by default
- Items can be archived (soft delete)
- Archived items can be restored to `active`
- Hard delete removes the item permanently
