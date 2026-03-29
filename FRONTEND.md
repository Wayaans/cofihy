# Frontend Stack Contract

> Project-level reference defining how the frontend stack works and what the contract must follow.

## Purpose

This file documents the frontend framework conventions, patterns, and constraints that all feature contracts must respect. Fill this in once per project after choosing your frontend stack.

---

## Stack Profile

| Field                | Value                  |
| -------------------- | ---------------------- |
| Framework            | `[FRONTEND]`           |
| Language             | `[FRONTEND_LANGUAGE]`  |
| Type system          | `[TYPE_SYSTEM]`        |
| API client           | `[API_CLIENT]`         |
| State management     | `[STATE_MANAGEMENT]`   |
| Form library         | `[FORM_LIBRARY]`       |
| Validation library   | `[VALIDATION_SYSTEM]`  |
| Auth handling        | `[AUTH_STRATEGY]`      |
| Testing framework    | `[TEST_FRAMEWORK]`     |
| CSS/styling approach | `[STYLING_APPROACH]`   |

---

## Rendering Model

<!-- How does the framework render pages? SSR, CSR, SSG, ISR, hybrid? -->

- Rendering strategy: `[RENDERING_STRATEGY]`
- Hydration model: `[HYDRATION_MODEL]`

---

## Routing Model

<!-- File-based? Config-based? Nested layouts? -->

- Router type: `[ROUTER_TYPE]`
- Route conventions: _describe naming and nesting rules_

---

## Data Fetching Conventions

<!-- How does data get to the UI? Hooks? Server functions? Loaders? -->

- Primary method: `[DATA_FETCHING_METHOD]`
- Caching strategy: `[CACHING_STRATEGY]`
- Error boundary pattern: _describe how fetch errors are handled_

---

## Type Safety Rules

- API response types must be: _generated / hand-written / inferred_
- Type source: `[TYPE_SYSTEM]`
- Shared types location: _path convention_

---

## API Client Conventions

- HTTP client: `[API_CLIENT]`
- Base URL config: _describe how API base URL is configured_
- Auth header injection: _describe how auth tokens are attached_
- Response unwrapping: _describe how response envelopes are handled_

---

## Form Handling Expectations

- Form library: `[FORM_LIBRARY]`
- Validation timing: _on blur / on submit / real-time_
- Server error mapping: _how API validation errors map to form fields_

---

## Validation Handling

- Client-side validation: `[VALIDATION_SYSTEM]`
- Schema sharing with backend: _yes / no / partial_
- Validation error display: _inline / toast / summary_

---

## Auth / Session Handling

- Strategy: `[AUTH_STRATEGY]`
- Token storage: _cookie / localStorage / memory_
- Session refresh: _describe refresh flow_
- Protected route pattern: _describe guard mechanism_

---

## Error Handling

- Global error boundary: _yes / no_
- Toast/notification system: _describe_
- API error format expected: _refer to BACKEND.md error conventions_

---

## State Management Expectations

- Global state: `[STATE_MANAGEMENT]`
- Server state: `[DATA_FETCHING_METHOD]`
- Form state: `[FORM_LIBRARY]`
- What goes where: _describe boundaries_

---

## File / Folder Conventions

- Feature folder pattern: _describe_
- Component naming: _PascalCase / kebab-case_
- File extensions: _`.tsx` / `.vue` / `.svelte`_
- Index files: _barrel exports or direct imports_

---

## Testing Expectations

- Unit tests: _required / optional_
- Integration tests: _required / optional_
- E2E tests: _required / optional_
- Testing framework: `[TEST_FRAMEWORK]`
- Coverage target: _percentage_

---

## Constraints the Contract Must Follow

- [ ] All API endpoints used by frontend must exist in the OpenAPI spec
- [ ] Response shapes must match the contract exactly
- [ ] Error responses must follow the format defined in `BACKEND.md`
- [ ] Auth flows must follow the strategy defined above
- [ ] Form validation must cover all fields marked required in the API spec
- [ ] Loading and error states must be handled for every async operation

---

## Documentation Checklist

Before considering this file complete, ensure you have documented:

- [ ] Framework name and version
- [ ] Rendering model (SSR/CSR/SSG/hybrid)
- [ ] Routing model and conventions
- [ ] Data fetching approach
- [ ] Type safety approach
- [ ] API client setup
- [ ] Form handling approach
- [ ] Validation approach
- [ ] Auth/session handling
- [ ] Error handling patterns
- [ ] State management boundaries
- [ ] File/folder conventions
- [ ] Testing expectations

---

## Agent Prompt: Generate Frontend Rules

**How to use this prompt:**

1. Replace `[FRONTEND]` and `[FRONTEND_LANGUAGE]` with your actual stack
2. Open your **frontend project** in your coding agent
3. Paste the prompt below into that agent
4. The agent will analyze your frontend codebase and produce markdown output
5. Copy the output back into this file, replacing the placeholder sections above

```
You are a frontend architecture expert. I am using [FRONTEND] with [FRONTEND_LANGUAGE] for my project.

Analyze this codebase and generate concise, practical project rules and conventions for a FRONTEND.md contract file. This file will be used as a reference by other agents when implementing features from API contracts.

For each of the following sections, provide:
- How this project specifically handles it (based on what you see in the code)
- The convention or pattern to follow
- Any constraints or gotchas

Sections to cover:
1. Stack profile (framework, language, key libraries used in this project)
2. Rendering model (SSR, CSR, SSG, ISR, hybrid -- what does this project use?)
3. Routing model (file-based, config-based, nested layouts)
4. Data fetching conventions (hooks, loaders, server functions)
5. Type safety rules (how types flow from API to UI)
6. API client conventions (HTTP client used, base URL config, auth header injection, response unwrapping)
7. Form handling expectations (form library, validation timing, server error mapping)
8. Validation handling (client-side validation library, schema sharing with backend)
9. Auth/session handling (token storage, session refresh, route guards)
10. Error handling (error boundaries, toast patterns, API error format expected)
11. State management expectations (global vs server vs form state boundaries)
12. File/folder conventions (feature folders, component naming, file extensions, import style)
13. Testing expectations (unit, integration, e2e, tools, coverage targets)

Keep each section under 5 lines. Be specific to this project, not generic.
Output as markdown sections I can copy-paste directly into FRONTEND.md.
```
