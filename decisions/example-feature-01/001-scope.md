# Decision: Feature Scope

> ADR-001 | Feature: example-feature-01 | Date: 2024-01-15 | Status: Accepted

## Context

We need a reference example feature to demonstrate the cofihy contract system. The feature should be simple enough to understand quickly but complete enough to show all contract components.

## Decision

Use a generic "Item" CRUD resource with the following scope:

- Basic CRUD operations (create, read, update, delete)
- List with pagination, filtering by status, and sorting
- Ownership model (items belong to users)
- Two-state lifecycle (active/archived)
- Standard validation and error handling

## Alternatives Considered

1. **Auth feature**: Too complex for an example; involves multiple flows
2. **Simple notes feature**: Too minimal; wouldn't demonstrate permissions or lifecycle
3. **E-commerce product**: Too domain-specific; wouldn't feel generic

## Consequences

- The example is generic enough to serve as a template for real features
- All contract components have meaningful content to demonstrate
- The "Item" name makes it clear this is a placeholder, not a real domain
