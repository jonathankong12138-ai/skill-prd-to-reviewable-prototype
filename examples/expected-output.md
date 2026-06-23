# Expected Output

When used on [brief-prd.md](brief-prd.md), the Skill should produce a local `prototype-review/` project.

Expected characteristics:

- A runnable Vite + React + TypeScript + Tailwind CSS app.
- A responsive clickable prototype for desktop and mobile widths.
- A Flow overview with concrete static screens, not text-only nodes.
- User-flow and functional-line perspectives.
- Page-specific state controls under each Flow screen.
- Review comments under each Flow screen.
- Comments can be added, edited, deleted, resolved, and persisted through refresh.
- A `review-notes.json` export action.
- A production build that creates a browser-openable `dist/index.html`.
- A transfer folder or zip containing the latest inlined `index.html`.

Example inferred screens:

- Workspace dashboard
- Task list
- New task form
- Validation feedback
- Task detail drawer
- Delete confirmation

Example scoped states:

- Dashboard: loading, populated, empty
- Task list: populated, filtered empty, permission denied
- New task form: default, validation error, saving, saved draft, save failed
- Attachment area: empty, uploading, failed, uploaded
- Task detail: view, editing, blocked, done
- Delete confirmation: confirm, permission denied, deleted

The final prototype should use product-facing language in the app screens and keep implementation notes in review panels or annotations.
