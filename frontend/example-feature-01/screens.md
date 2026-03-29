# Screens: Example Feature

> Screen data needs, UI mapping, and display requirements.

## Screen: Item List

### Route

- Path: `/items`
- Auth required: yes

### Data Needs

| Data            | Source endpoint              | Required |
| --------------- | ---------------------------- | -------- |
| Item list       | `GET /api/v1/items`          | yes      |
| Pagination meta | `GET /api/v1/items` (meta)   | yes      |

### UI Elements

- Item list/table showing: title, status, created date
- Pagination controls (page numbers or load more)
- Status filter dropdown (all, active, archived)
- Sort control (newest first by default)
- "Create Item" button

### Loading States

- Initial load: skeleton/spinner for list area
- Page change: spinner or skeleton rows
- Error: error message with retry button

### Actions

| Action        | Endpoint                 | Triggers           |
| ------------- | ------------------------ | ------------------- |
| Load items    | `GET /api/v1/items`      | Page load, filter   |
| Create item   | Navigate to create form  | Button click        |
| View item     | Navigate to detail page  | Row/card click      |

---

## Screen: Item Detail

### Route

- Path: `/items/:id`
- Auth required: yes

### Data Needs

| Data  | Source endpoint              | Required |
| ----- | ---------------------------- | -------- |
| Item  | `GET /api/v1/items/:id`      | yes      |

### UI Elements

- Item title (heading)
- Item description (body text)
- Status badge (active/archived)
- Created/updated timestamps
- Edit button (if owner)
- Delete button (if owner)

### Loading States

- Initial load: skeleton for content area
- Error: error message (404 -> "Item not found")

### Actions

| Action  | Endpoint                      | Triggers      |
| ------- | ----------------------------- | ------------- |
| Edit    | Navigate to edit form         | Button click  |
| Delete  | `DELETE /api/v1/items/:id`    | Button + confirm |
