# Permissions: Example Feature

> Access control and authorization rules.

## Roles

| Role           | Description                              |
| -------------- | ---------------------------------------- |
| authenticated  | Logged-in user                           |
| owner          | The user who created the specific item   |
| unauthenticated| Not logged in                            |

## Permission Matrix

| Action              | Unauthenticated | Authenticated | Owner |
| ------------------- | --------------- | ------------- | ----- |
| List items          | no              | yes           | yes   |
| View item           | no              | yes           | yes   |
| Create item         | no              | yes           | --    |
| Update own item     | no              | no            | yes   |
| Delete own item     | no              | no            | yes   |
| Archive own item    | no              | no            | yes   |

## Rules

- Authentication is required for all endpoints
- Users can only modify/delete items they own (`created_by` matches current user)
- List endpoint returns only items the current user has access to
