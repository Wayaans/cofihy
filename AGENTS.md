# cofihy -- Contract-First Hybrid Starter

A reusable, framework-agnostic contract system for application development. Define API contracts, domain rules, and frontend/backend expectations **before writing code**.

**IMPORTANT: If you are an AI agent, read this entire file before doing anything else in this repository.**

## Directory Structure

```
cofihy/
├── AGENTS.md                    # This file (read first)
├── CONTRACT.md                  # System overview and principles
├── FRONTEND.md                  # Frontend stack contract rules
├── BACKEND.md                   # Backend stack contract rules
├── features/                    # Source-of-truth SPEC files
│   └── <feature>-XX/SPEC.md
├── api/                         # OpenAPI specs
│   └── <feature>-XX/openapi.yaml
├── domain/                      # Glossary, entities, rules, permissions
│   └── <feature>-XX/
├── frontend/                    # Screen data, UI mapping, forms
│   └── <feature>-XX/
├── backend/                     # Validation, serialization notes
│   └── <feature>-XX/
├── decisions/                   # ADR-style decision records
│   └── <feature>-XX/
├── examples/                    # Request/response JSON examples
│   └── <feature>-XX/
├── generated/                   # Generated artifacts (types, SDKs)
│   └── <feature>-XX/
└── templates/                   # Reusable templates for new features
```

---

## Creating a New Feature Package

1. Pick a feature name and suffix: `my-feature-01`
2. Create directories across all sections:
   ```bash
   FEAT=my-feature-01
   mkdir -p features/$FEAT api/$FEAT domain/$FEAT frontend/$FEAT \
            backend/$FEAT decisions/$FEAT examples/$FEAT generated/$FEAT
   ```
3. Copy templates:
   ```bash
   cp templates/SPEC.template.md features/$FEAT/SPEC.md
   cp templates/openapi.template.yaml api/$FEAT/openapi.yaml
   cp templates/glossary.template.md domain/$FEAT/glossary.md
   cp templates/entities.template.md domain/$FEAT/entities.md
   cp templates/rules.template.md domain/$FEAT/rules.md
   cp templates/permissions.template.md domain/$FEAT/permissions.md
   cp templates/screens.template.md frontend/$FEAT/screens.md
   cp templates/forms.template.md frontend/$FEAT/forms.md
   cp templates/validation.template.md backend/$FEAT/validation.md
   cp templates/serialization.template.md backend/$FEAT/serialization.md
   cp templates/decision.template.md decisions/$FEAT/001-scope.md
   ```
4. Fill in the contract files
5. Update `features/$FEAT/SPEC.md` with correct relative paths
6. Hand SPEC.md to your coding agent

## Creating a Feature Revision

When a feature needs a breaking change or major revision:

1. **Do not modify** the existing package (e.g., `auth-01`)
2. Create a new package with the next suffix: `auth-02`
3. Reference the previous version in the new SPEC.md if needed

---

## Key Files

| File                    | Purpose                                     |
| ----------------------- | ------------------------------------------- |
| `AGENTS.md`             | Agent entry point -- read this first         |
| `CONTRACT.md`           | System design, principles, and directory map |
| `FRONTEND.md`           | Frontend stack rules and conventions         |
| `BACKEND.md`            | Backend stack rules and conventions          |
| `features/*/SPEC.md`    | Single entry point per feature package       |

---

## For Coding Agents

If you are an AI agent working in this repository:

1. **Always read this file (AGENTS.md) first**
2. Read `CONTRACT.md` to understand the system structure
3. Read `FRONTEND.md` and `BACKEND.md` for stack-specific rules
4. When creating a new feature contract, follow "Creating a New Feature Package" above
5. When implementing a feature, read its `features/<name>-XX/SPEC.md` and follow all relative-path references
6. Check `examples/` for expected request/response shapes
7. Check `decisions/` for architectural context
8. **Never modify existing feature packages** -- create new suffixed versions instead

If you are an AI agent receiving a `SPEC.md` file for implementation (in a frontend or backend project):

1. Read the SPEC.md to understand the feature scope
2. Follow all relative-path references to read related contract files
3. Read `FRONTEND.md` or `BACKEND.md` for stack-specific rules
4. Implement according to the contract -- do not deviate without discussion
5. Check `examples/` for expected request/response shapes
6. Check `decisions/` for architectural context
