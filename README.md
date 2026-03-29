# cofihy

Contract-First Hybrid -- a shared contract system that sits between your frontend and backend projects. Define what your API looks like, what the domain rules are, and what each side expects, **before writing any code**.

Framework-agnostic. Works with any stack. Designed for humans and AI coding agents.

---

## Why?

When frontend and backend are built separately, things drift. Response shapes don't match. Validation rules diverge. Edge cases get discovered late.

cofihy fixes this by making one shared place where both sides agree on everything first.

---

## How It Works

```
 ┌──────────────┐         ┌──────────────┐
 │   Backend    │         │   Frontend   │
 │   project    │         │   project    │
 └──────┬───────┘         └──────┬───────┘
        │                        │
        │    ┌──────────────┐    │
        └───►│    cofihy    │◄───┘
             │  (contracts) │
             └──────────────┘
```

1. You define a feature as a contract package
2. The contract describes: API shape, domain rules, frontend screens, backend validation, examples
3. One file (`SPEC.md`) ties the whole feature together
4. You hand that file to a coding agent (or a teammate) and they build it

---

## Setup

### 1. Clone

```bash
git clone https://github.com/<your-username>/cofihy.git
```

### 2. Generate backend rules

Open your **backend project** in a coding agent. Copy the prompt from the bottom of [`BACKEND.md`](./BACKEND.md), replace `[BACKEND]` and `[BACKEND_LANGUAGE]` with your actual stack, and paste it into the agent. The agent will analyze your backend codebase and produce markdown output. Copy that output back into `BACKEND.md`, replacing the placeholder sections.

### 3. Generate frontend rules

Same process with your **frontend project**. Copy the prompt from [`FRONTEND.md`](./FRONTEND.md), replace `[FRONTEND]` and `[FRONTEND_LANGUAGE]`, paste into the agent working on your frontend project. Copy the output back into `FRONTEND.md`.

### 4. Configure the repo

Once both files are filled in, open **this repo** in a coding agent and paste this prompt:

```
Read AGENTS.md first, then read BACKEND.md and FRONTEND.md in this repository.

These files have been filled in with the actual stack rules for our project:
- Backend: [BACKEND] with [BACKEND_LANGUAGE]
- Frontend: [FRONTEND] with [FRONTEND_LANGUAGE]

Now do the following:
1. Read CONTRACT.md to understand the system structure
2. Go through every file in templates/ and replace all generic placeholders with values that match our actual stack
3. Update the example feature package (example-feature-01) across all directories to reflect our actual conventions (response format, error format, field casing, auth strategy, etc.)
4. Replace these placeholders everywhere they appear:
   - [FRONTEND] -> actual frontend framework
   - [BACKEND] -> actual backend framework
   - [FRONTEND_LANGUAGE] -> actual frontend language
   - [BACKEND_LANGUAGE] -> actual backend language
   - [API_STYLE] -> actual API style (e.g., REST)
   - [TYPE_SYSTEM] -> actual type system (e.g., TypeScript)
   - [VALIDATION_SYSTEM] -> actual validation library
   - [AUTH_STRATEGY] -> actual auth strategy (e.g., JWT)
5. Make sure all example JSON files in examples/ match the actual response envelope and error format from BACKEND.md
6. Do not delete any files or change the directory structure

List every file you changed when done.
```

### 5. Start making contracts

You're ready. See [Creating a new feature](#creating-a-new-feature) below.

---

## Creating a New Feature

```bash
FEAT=my-feature-01
mkdir -p features/$FEAT api/$FEAT domain/$FEAT frontend/$FEAT \
         backend/$FEAT decisions/$FEAT examples/$FEAT generated/$FEAT
```

Copy templates:

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

Fill in the contract files, then hand `features/$FEAT/SPEC.md` to your coding agent.

### Revisions

Never edit an existing feature package. Create a new one with the next suffix:

- `auth-01` (original)
- `auth-02` (revision)

---

## What's in Each Directory

### Root Files

| File | What it does |
| --- | --- |
| `AGENTS.md` | Instructions for AI agents. Read first before working in this repo. |
| `CONTRACT.md` | System overview, principles, naming rules, placeholder reference. |
| `FRONTEND.md` | Frontend stack conventions. Placeholder-based until configured. Contains a prompt to auto-generate rules from your frontend project. |
| `BACKEND.md` | Backend stack conventions. Same idea -- placeholder-based with a generation prompt. |

### `features/`

The main entry point for each feature. Contains one `SPEC.md` per feature package. This is the **single file you hand to an agent** -- it links to everything else.

```
features/
└── example-feature-01/
    └── SPEC.md          # Links to all contract files for this feature
```

### `api/`

OpenAPI specs. One folder per feature package.

```
api/
└── example-feature-01/
    └── openapi.yaml     # Endpoints, request/response schemas, auth
```

### `domain/`

Business domain definitions. The "what" of the feature.

```
domain/
└── example-feature-01/
    ├── glossary.md      # Domain terms and definitions
    ├── entities.md      # Entity fields, types, relationships, lifecycle
    ├── rules.md         # Business rules and invariants
    └── permissions.md   # Roles and access control matrix
```

### `frontend/`

What the frontend needs to know. Screens, data requirements, form behavior.

```
frontend/
└── example-feature-01/
    ├── screens.md       # Screen data needs, UI elements, loading states
    └── forms.md         # Form fields, validation timing, error mapping
```

### `backend/`

What the backend needs to know. Validation rules, serialization details.

```
backend/
└── example-feature-01/
    ├── validation.md    # Per-endpoint validation rules, error codes
    └── serialization.md # Response field mapping, null handling, date format
```

### `decisions/`

ADR-style decision records. Why things are the way they are.

```
decisions/
└── example-feature-01/
    ├── 001-scope.md     # Why this scope was chosen
    └── 002-api-shape.md # Why this API shape was chosen
```

### `examples/`

Concrete JSON examples of requests, responses, and errors.

```
examples/
└── example-feature-01/
    ├── create-request.json   # POST body example
    ├── create-response.json  # Success response example
    ├── list-response.json    # Paginated list example
    └── error-response.json   # Validation error example
```

### `generated/`

Placeholder for artifacts generated from contracts (types, SDK clients, validation schemas). Empty until you set up code generation.

```
generated/
└── example-feature-01/
    └── .gitkeep
```

### `templates/`

Reusable templates for creating new feature packages. Copy these when starting a new feature.

| Template | Creates |
| --- | --- |
| `SPEC.template.md` | `features/<feat>/SPEC.md` |
| `openapi.template.yaml` | `api/<feat>/openapi.yaml` |
| `glossary.template.md` | `domain/<feat>/glossary.md` |
| `entities.template.md` | `domain/<feat>/entities.md` |
| `rules.template.md` | `domain/<feat>/rules.md` |
| `permissions.template.md` | `domain/<feat>/permissions.md` |
| `screens.template.md` | `frontend/<feat>/screens.md` |
| `forms.template.md` | `frontend/<feat>/forms.md` |
| `validation.template.md` | `backend/<feat>/validation.md` |
| `serialization.template.md` | `backend/<feat>/serialization.md` |
| `decision.template.md` | `decisions/<feat>/001-scope.md` |

---

## License

MIT
