# Validation: [FEATURE_NAME]

> Backend validation rules and error response mapping.

## Endpoint: `POST /api/v1/[resource]`

### Field Validation

| Field         | Rules                                          | Error code          |
| ------------- | ---------------------------------------------- | ------------------- |
| `name`        | required, string, min:1, max:255               | VALIDATION_ERROR    |
| `description` | optional, string, max:1000                     | VALIDATION_ERROR    |

### Validation Response

On validation failure, return `422` with:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed",
    "details": [
      { "field": "name", "message": "Name is required" }
    ]
  }
}
```

### Business Rule Validation

| Rule     | Condition                    | Error code          | HTTP Status |
| -------- | ---------------------------- | ------------------- | ----------- |
| _rule_   | _when this happens_          | _ERROR_CODE_        | _4xx_       |

## Endpoint: `PUT /api/v1/[resource]/{id}`

_Repeat the pattern above for each endpoint._
