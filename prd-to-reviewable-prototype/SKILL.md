---
name: prd-to-reviewable-prototype
description: Turn any early product idea, brief PRD, or incomplete PRD into a runnable, shareable, reviewable low-fidelity interactive prototype workbench. Use when Codex must identify medium, product type, core task, product-definition gaps, information architecture, user flows, functional flows, page states, edge cases, medium constraints, interaction rules, acceptance criteria, and build or refine a Vite + React + TypeScript + Tailwind CSS + React Flow prototype for mobile apps, responsive websites, Web apps, admin/SaaS dashboards, H5/mini-programs, desktop apps, plugins/extensions, tools, content products, e-commerce, communities, games, simulations, and data dashboards, with real interactions, comments, localStorage, JSON export, browser-only index.html, and zip packaging.
---

# PRD To Reviewable Prototype

Use this skill to convert any incomplete PRD or early product idea into a runnable prototype review workbench. The output is not a static page gallery. It must expose information architecture, user flows, functional flows, state feedback, exception paths, medium constraints, review comments, and acceptance criteria.

Do not ask the user to write a complete PRD. Ask up to 3 focused questions only when missing information would materially change the prototype. Infer low-risk gaps and write them in `assumptions`.

## Core Workflow

1. Read the PRD and any referenced style, product, market, or platform docs. Preserve source text in `prototype-review/src/data/prdInput.md`.
2. Classify product-definition maturity:
   - `idea`: feature name or goal only.
   - `definition`: user/problem/value partly clear, but pages, rules, states, or flow incomplete.
   - `interaction-ready`: medium, product type, core task, pages, actions, rules, and states are clear enough to prototype.
3. Identify three foundations before designing screens:
   - **Medium**: `mobile-app`, `responsive-web`, `desktop-web-app`, `admin-dashboard / SaaS`, `H5 / mini-program`, `desktop-app`, `plugin / extension`, `game / interactive-tool`, or `unknown`.
   - **Product type**: `landing / marketing`, `content / media`, `e-commerce`, `community / social`, `productivity / tool`, `SaaS / admin / CRM / ops`, `diary / personal-record`, `data-dashboard`, `onboarding / form / application`, `game / simulation`, or `other`.
   - **Core task**: why the user comes, where they enter, what success means, where failure/cancel goes, which actions are irreversible or risky, and what data must save, recover, or sync.
4. Ask clarification questions if medium, product type, or core task is missing and would significantly affect the prototype. Ask no more than 3 questions at a time.
5. Infer the structured spec:
   - product goal and MVP promise
   - first target user segment
   - core scenario and use trigger
   - medium and product type
   - information architecture
   - page/screen inventory
   - user flow and functional flow
   - primary, branch, cancel, error, retry, and recovery paths
   - page-specific states
   - permissions, login, identity, data saving, sync, and recovery
   - high-risk actions and confirmation/undo/recovery strategy
   - acceptance criteria
   - assumptions
6. Build or update `prototype-review/` using Vite, React, TypeScript, Tailwind CSS, and React Flow.
7. Package a browser-only deliverable: inlined `dist/index.html` plus a zip folder.

## Clarification Questions

Ask product-definition questions before UI work when the PRD is early:

1. Who is the first target user, and in what moment would they use this?
2. What is the single primary outcome the MVP must let them complete?
3. What should be included in v1, and what is explicitly out of scope?

Ask interaction questions when needed:

- What is the target medium or device class?
- What is the main entry point and exit path?
- What data must be saved, restored, synced, or exported?
- Which actions are destructive, irreversible, costly, public, paid, or high risk?
- Which platform capabilities are required, such as camera, microphone, location, notification, sound, haptics, file system, payment, login, or sharing?

If the user cannot answer, make conservative assumptions and show them in the rules panel, review notes, and generated spec.

## Required Project Structure

Create or maintain:

```text
prototype-review/
  package.json
  README.md
  index.html
  vite.config.ts
  scripts/inline-dist.mjs
  src/
    App.tsx
    main.tsx
    index.css
    data/
      prdInput.md
      prototypeSpec.ts
    components/
      PrototypeView.tsx
      FlowView.tsx
      StateView.tsx
      ReviewView.tsx
      AnnotationLayer.tsx
      SpecPanel.tsx
    utils/
      parsePrd.ts
      storage.ts
      exportReview.ts
```

When creating a fresh project, prefer the bundled template:

```bash
node path/to/prd-to-reviewable-prototype/scripts/scaffold-prototype.mjs prototype-review
```

Use `base: './'` in Vite and inline CSS/JS into `dist/index.html` for browser-only sharing.

## Medium Rules

Apply medium-specific interaction obligations automatically.

### Mobile App

- Render inside a phone frame.
- Secondary and deeper screens must have back navigation.
- Task pages must have close, cancel, or save-draft exits.
- Long content must scroll inside the phone frame; do not crop content.
- Camera, album, microphone, location, notification, sound, haptic, and similar system capabilities must include permission, denied, off, unavailable, or degraded paths.
- Bottom actions must avoid safe areas.
- Foreground/background switching, weak network, failure, restore, and retry must be represented.

### Responsive Website / Web App

- Verify desktop, tablet, and mobile layouts.
- Navigation, forms, buttons, modals, filters, pagination, empty states, and errors must work responsively.
- Do not create uncontrolled horizontal scrolling.
- Include keyboard focus, semantic structure, form labels, inline errors, and accessible names.
- Login, submit, save, payment, upload, and export tasks need loading, success, error, and retry.

### Admin / SaaS / Data Dashboard

- Favor density, scanning, tables/lists, search, filters, bulk actions, detail drawers, permissions, empty states, and errors.
- Do not make a marketing hero page.
- Show data loading, no data, filtered empty results, permission denied, save failure, and delete confirmation.
- High-risk operations require confirmation plus undo, recovery, or audit strategy when appropriate.

### H5 / Mini-Program

- Consider short-link entry, share entry, auth dialogs, WeChat/system capabilities, return path, loading failure, and re-entry.
- Keep pages lightweight and task paths short.

### Desktop App / Tool

- Consider menu, toolbar, shortcuts, panels, canvas/work area, file save, undo/redo, import/export.
- For canvas/editors, support zoom, drag, select, status feedback, and empty-canvas browsing.

### Plugin / Extension

- Consider host-app context, permission request, install/onboarding, compact popup, options page, unavailable host state, and safe fallback.

### Game / Interactive Tool

- Implement the core mechanic or interaction. Do not build only an explanation page.
- Include start, in-progress, pause, fail, success, restart, and exit.
- For established rules, physics, parsing, or AI engines, use a mature library unless the user explicitly asks for a from-scratch implementation.

## Product Type Baselines

All products must check:

- main entry
- primary flow
- success loop
- cancel/back path
- empty state
- error state
- loading state
- permission/login/identity state
- data save and recovery
- high-risk confirmation
- help, feedback, or next step

Add product-specific baselines:

- **Diary / personal record**: My/settings, subscription or premium plan, privacy lock, sync/backup, import/export, reminders, theme/appearance, sound/haptics switch. Recycle bin/trash belongs to content management unless the PRD says otherwise.
- **E-commerce**: product list, detail, variant selection, cart, coupon, address, payment, order, after-sales; include out of stock, payment failure, price change, and invalid coupon.
- **SaaS / admin / CRM / ops**: side navigation, list, detail, create/edit form, filters, bulk actions, permissions, audit/logs; make delete, disable, publish, and similar high-risk actions reviewable.
- **Content / media / community / social**: feed, detail, comments, publish, report, collect/save, share, follow, notifications; include empty feed, load failure, content violation, and login gate.
- **Onboarding / form / application**: step-by-step form, validation, save draft, attachment upload, submit confirmation, review status, returned-for-edit path.
- **Data dashboard**: overview, chart/table states, time range, filters, drilldown, export, no data, delayed data, permission, and data freshness.
- **Landing / marketing**: only create a landing page when the PRD is truly marketing-focused; still include responsive CTA flow, form/submission state, success/failure, and analytics assumptions.
- **Game / simulation**: playable core loop, rules, start, pause, fail, success, retry, exit, settings, and score/progress when relevant.

## Flow Views

Flow must include two perspectives when the product has enough scope:

### User Flow View

- Start from the user entry.
- Show the path the user actually traverses.
- Every node must be a concrete screen UI, not a text-only node.
- Every path must include entry, main action, feedback, exception, success, and return/reflow.
- The main journey must form a closed loop or clear terminal state.

### Functional Line View

- Organize screens by module or functional area.
- Show internal states and page relationships.
- Every screen card must have state controls.
- Comments must bind to the corresponding screen.
- Comments must support add, edit, delete, resolved/unresolved, and localStorage persistence.

If the user asks to merge or restructure flows, update both perspectives.

## Real Interaction Requirement

Each core function must implement at least one real interaction, such as:

- input
- search
- filter
- state switch
- toggle
- upload count
- play/pause
- timer
- drag/zoom
- save draft
- submit validation
- failed retry
- delete/restore
- subscription expand/open
- permission denied/degraded path

If a core page only navigates, continue implementing until it has meaningful interaction.

## Information Architecture Sync

When the user changes structure or ownership, such as “move trash to content management,” “merge these features,” or “where should recording live,” update all related artifacts:

- actual entry button
- user flow
- functional flow
- static Flow screen
- interactive Prototype screen
- rules panel
- review notes or page explanation
- acceptance criteria
- assumptions

Do not only update one button or one screen.

## Review Workbench Requirements

- Keep Prototype, Flow, rules, comments, and export in one clear review environment.
- Flow overview and interactive prototype must be easy to locate.
- Avoid overlap in large canvases.
- Canvas drag/zoom must not hijack phone scrolling, form typing, or button clicks.
- Avoid uncontrolled horizontal scrolling.
- Long content needs explicit scroll containers.
- Phone screens, web viewports, dashboard panels, cards, and modals must be fully viewable.
- Product UI should use product language; review metadata belongs in rules, annotations, or panels.

## State Generation Rules

Do not force every page to show `default`, `loading`, `empty`, `error`, `success`, and `completed`.

Generate only meaningful states for each page:

- data fetch/export/save: loading, error, success
- entry/editor: default, empty, validation, draft, permission, failed save
- timer/game: ready, running, paused, failed, success, retry
- dashboard/list: loading, populated, no data, filtered empty, permission denied, error
- settlement/payment/order: pending, success, failure, retry, cancel, refund/after-sales when relevant

## Interaction Annotation Rules

Generate annotations for meaningful actions:

- trigger and source element
- destination page or state transition
- visible feedback
- loading/error/success behavior
- permission, login, identity, sync, save, or recovery impact
- sound/haptic/animation behavior only if relevant to the medium or PRD
- branch and exception behavior

Do not invent fake product controls. For example, do not add “simulate finish” to a timer; implement the timer or expose completed state in Flow.

## Review Data Contract

Store review comments with:

- `id`
- `pageId` or `screenId`
- `elementName` when available
- `x` and `y` when coordinate-based
- `body`
- `createdAt`
- `updatedAt`
- `resolved`

Use localStorage first. Export `review-notes.json` with comments, spec context, assumptions, and unresolved risks.

## Research And Networking

When the user asks for market analysis, competitor references, latest standards, common industry functions, or help completing settings, membership, privacy, payment, permissions, platform capabilities, or design patterns, browse the web. Prefer official docs, authoritative design guidelines, platform docs, and mainstream product documentation. Convert findings into:

- prototype functions
- page states
- rules panel content
- acceptance criteria
- assumptions

Include source links in the final answer when web research informed the prototype.

## Transferable Output

When sharing with reviewers:

1. Build with relative asset paths.
2. Inline CSS and JS into `dist/index.html`.
3. Copy `dist/index.html` and a short instruction file into a transfer folder.
4. Zip the folder.
5. Provide exact local paths to `dist/index.html` and the zip.

Opening `dist/index.html` directly in a browser must not show a blank page.

## Visual QA

After each build, verify at least:

- build passes
- page is not blank
- primary flow is clickable
- core interactions really work
- Flow and Prototype areas do not overlap
- mobile/web/dashboard layouts are not cropped
- long pages scroll
- text does not overflow buttons or cards
- comments can add, edit, delete, resolve/unresolve, and persist
- export file can be generated
- packaged `index.html` opens directly in a browser

Use browser automation/screenshots when available. If unavailable, report the limitation and still run build/package checks.

## Final Response

Final delivery must include:

- runnable prototype path or local URL
- browser-openable single-file `dist/index.html`
- zip path
- key change summary
- verification result
- source links if market/platform/design research was used
