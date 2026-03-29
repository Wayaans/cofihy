# Contract-First Hybrid (cofihy)

> Shared source of truth between frontend and backend.

## What Is This?

`cofihy/` is a contract-first system where **API contracts, domain rules, and expectations are defined before code is written**. Both frontend and backend teams (or agents) consume the same contract files to build their respective implementations.

This repo is **not** an application. It is a contract workspace that sits alongside your frontend and backend projects.

## Core Principles

1. **Contract before code** -- define what the API looks like before implementing it
2. **Single source of truth** -- one spec file per feature links to everything
3. **Framework-agnostic** -- uses placeholders until configured for a specific stack
4. **Package-style features** -- each feature version lives in its own suffixed directory
5. **Immutable versions** -- old feature packages are never modified; new revisions get a new suffix

## How It Works

```
                     ┌─────────────┐
                     │   cofihy/   │
                     │  (contracts)│
                     └──────┬──────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
              ▼             ▼             ▼
        BACKEND.md    SPEC.md files   FRONTEND.md
        (stack rules) (per feature)   (stack rules)
              │             │             │
              ▼             │             ▼
     Backend project        │     Frontend project
                            │
                    ┌───────┴───────┐
                    │  api/         │
                    │  domain/      │
                    │  frontend/    │
                    │  backend/     │
                    │  decisions/   │
                    │  examples/    │
                    └───────────────┘
```

1. Fill in `BACKEND.md` and `FRONTEND.md` with your stack rules (see AGENTS.md for how)
2. Configure the repo placeholders to match your stack
3. Create feature packages using templates
4. The `features/<name>-XX/SPEC.md` file is the **single entry point** per feature
5. Hand that SPEC file to a frontend or backend agent to start implementation

## Directory Map

| Directory      | Purpose                                              |
| -------------- | ---------------------------------------------------- |
| `features/`    | Source-of-truth SPEC files (one per feature package)  |
| `api/`         | OpenAPI specs and API contract files                  |
| `domain/`      | Glossary, entities, business rules, permissions       |
| `frontend/`    | Screen data needs, UI mapping, form behavior          |
| `backend/`     | Validation, serialization, backend implementation notes |
| `decisions/`   | ADR-style decision records per feature                |
| `examples/`    | Request/response/error JSON examples                  |
| `generated/`   | Placeholder for generated artifacts (types, SDKs)     |
| `templates/`   | Reusable templates for creating new feature packages  |

## Naming Convention

- Feature directories: `<feature-name>-XX` (e.g., `auth-01`, `task-management-02`)
- Decision files: `NNN-<topic>.md` (e.g., `001-scope.md`, `002-api-shape.md`)
- Suffix numbers are zero-padded: `-01`, `-02`, `-03`

## Stack Placeholders

These placeholders appear throughout the contract files. They are replaced during Step 4 of setup (see AGENTS.md):

| Placeholder             | Meaning                          |
| ----------------------- | -------------------------------- |
| `[FRONTEND]`            | Frontend framework name          |
| `[BACKEND]`             | Backend framework name           |
| `[FRONTEND_LANGUAGE]`   | Frontend programming language    |
| `[BACKEND_LANGUAGE]`    | Backend programming language     |
| `[API_STYLE]`           | API style (REST, GraphQL, tRPC)  |
| `[TYPE_SYSTEM]`         | Type generation system           |
| `[VALIDATION_SYSTEM]`   | Validation library               |
| `[AUTH_STRATEGY]`       | Auth method (JWT, session, etc.) |

## Related Files

- [README.md](./README.md) -- project overview, setup guide, directory explanation
- [AGENTS.md](./AGENTS.md) -- agent instructions (read first if you are an AI agent)
- [FRONTEND.md](./FRONTEND.md) -- frontend stack rules
- [BACKEND.md](./BACKEND.md) -- backend stack rules
