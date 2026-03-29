# Forms: Example Feature

> Form behavior, field definitions, and validation mapping.

## Form: Create Item

### Fields

| Field         | Type     | Required | Validation              | API field      |
| ------------- | -------- | -------- | ----------------------- | -------------- |
| `title`       | text     | yes      | min 1, max 255 chars    | `title`        |
| `description` | textarea | no       | max 2000 chars          | `description`  |

### Submit

- Endpoint: `POST /api/v1/items`
- Success: redirect to item detail page (`/items/:id`)
- Error: show inline field errors + toast for non-field errors

### Server Error Mapping

| API error field | Form field     | Display            |
| --------------- | -------------- | ------------------ |
| `title`         | `title`        | Inline below field |
| `description`   | `description`  | Inline below field |

### Validation Timing

- Client-side: on submit (validate before sending)
- Server-side: always on submit

---

## Form: Edit Item

### Fields

| Field         | Type     | Required | Validation              | API field      |
| ------------- | -------- | -------- | ----------------------- | -------------- |
| `title`       | text     | yes      | min 1, max 255 chars    | `title`        |
| `description` | textarea | no       | max 2000 chars          | `description`  |
| `status`      | select   | yes      | `active` or `archived`  | `status`       |

### Pre-fill

- Load current item data from `GET /api/v1/items/:id`
- Pre-fill all form fields with existing values

### Submit

- Endpoint: `PUT /api/v1/items/:id`
- Success: redirect to item detail page + success toast
- Error: show inline field errors + toast for non-field errors

### Server Error Mapping

| API error field | Form field     | Display            |
| --------------- | -------------- | ------------------ |
| `title`         | `title`        | Inline below field |
| `description`   | `description`  | Inline below field |
| `status`        | `status`       | Inline below field |

### Special Cases

- If item is archived, show warning before allowing edits
- If `ITEM_ARCHIVED` error, show message: "Archived items cannot be edited"
