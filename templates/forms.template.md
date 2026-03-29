# Forms: [FEATURE_NAME]

> Form behavior, field definitions, and validation mapping.

## Form: [Form Name]

### Fields

| Field         | Type     | Required | Validation              | API field     |
| ------------- | -------- | -------- | ----------------------- | ------------- |
| `name`        | text     | yes      | min 1, max 255 chars    | `name`        |
| `description` | textarea | no       | max 1000 chars          | `description` |

### Submit

- Endpoint: `POST /api/v1/resource`
- Method: _POST / PUT_
- Success: _redirect to / show toast / describe_
- Error: _show inline errors / show toast / describe_

### Server Error Mapping

| API error field | Form field    | Display           |
| --------------- | ------------- | ----------------- |
| `name`          | `name`        | Inline below field |
| `email`         | `email`       | Inline below field |

### Validation Timing

- Client-side: _on blur / on submit_
- Server-side: _always on submit_
