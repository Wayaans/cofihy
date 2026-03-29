# Permissions: [FEATURE_NAME]

> Access control and authorization rules.

## Roles

| Role    | Description              |
| ------- | ------------------------ |
| _role_  | _what this role can do_  |

## Permission Matrix

| Action         | Role A | Role B | Role C |
| -------------- | ------ | ------ | ------ |
| Create         | yes    | no     | no     |
| Read (own)     | yes    | yes    | no     |
| Read (all)     | yes    | no     | no     |
| Update (own)   | yes    | yes    | no     |
| Delete         | yes    | no     | no     |

## Rules

- _Describe any special permission logic_
