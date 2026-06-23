# Expected Output

When used on [brief-prd.md](brief-prd.md), the Skill should produce a local `prototype-review/` project.

Expected characteristics:

- A runnable Vite + React + TypeScript + Tailwind CSS app.
- A mobile-shaped clickable prototype.
- A Flow overview with concrete static screens, not only text nodes.
- Page-specific state controls under each Flow screen.
- Review comments under each Flow screen.
- Comments can be added, edited, deleted, resolved, and persisted through refresh.
- A `review-notes.json` export action.
- A production build that creates a browser-openable `dist/index.html`.
- A transfer folder or zip containing the latest inlined `index.html`.

Example inferred screens:

- Home
- Create note
- Safety check
- Growth result
- Garden
- Detail

Example scoped states:

- Home: default, empty
- Create note: text, image, sticker, empty, privacy reminder, submit failure, cached
- Safety check: pass, privacy reminder, quiet save
- Growth result: seed, sprout, bloom
- Garden: default, search empty
- Detail: normal, deleted item placeholder

The final prototype should use product-facing language in the app screens and keep implementation notes in review panels or annotations.
