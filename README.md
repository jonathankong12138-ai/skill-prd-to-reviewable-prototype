# PRD to Reviewable Prototype Skill

A Codex Skill that turns any early product idea, brief PRD, or incomplete PRD into a runnable, browser-shareable interactive prototype review workbench.

It is built for product managers, designers, frontend engineers, QA, and reviewers who need to align on information architecture, user flows, functional flows, states, interactions, edge cases, comments, and acceptance criteria before full implementation.

It is intended for mobile apps, responsive websites, Web apps, admin/SaaS dashboards, H5/mini-programs, desktop apps, plugins/extensions, productivity tools, content products, e-commerce, communities, games, simulations, and data dashboards.

## What It Does

- Reads early ideas, brief PRDs, or incomplete PRDs.
- Identifies medium, product type, and core task before designing screens.
- Assesses product-definition maturity and asks up to 3 targeted questions when key product or interaction details are missing.
- Infers information architecture, pages, user flows, functional flows, branch paths, page states, edge cases, interaction rules, medium constraints, and acceptance criteria.
- Builds a Vite + React + TypeScript + Tailwind CSS prototype review app.
- Supports clickable prototype screens, user-flow and functional-flow perspectives, scoped states, review comments, localStorage persistence, delete/edit/resolve actions, and `review-notes.json` export.
- Produces a browser-only `dist/index.html` that can be sent to reviewers without requiring Node.js.

## Why This Skill Is Different

Most PRD or product skills stop at writing documents. This Skill pushes the PRD into a usable review artifact:

- Concrete screens instead of text-only flow nodes.
- User flow and functional line views.
- Real interactions for each core function.
- Page-specific states instead of forcing every page into the same state list.
- Review operations that survive refresh.
- A transferable single-file browser build.

## Repository Structure

```text
.
├── README.md
├── examples/
│   ├── brief-prd.md
│   └── expected-output.md
└── prd-to-reviewable-prototype/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── scripts/
    │   └── scaffold-prototype.mjs
    └── assets/
        └── prototype-template/
```

## Install

Copy the Skill folder into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
cp -R prd-to-reviewable-prototype ~/.codex/skills/
```

Restart Codex after copying.

## Usage

Ask Codex:

```text
Use prd-to-reviewable-prototype to create a reviewable interactive prototype from this PRD.
```

Or:

```text
Here is my brief PRD. Use the PRD to Reviewable Prototype skill. First identify the medium, product type, and core task. Ask me up to 3 targeted questions if key details are missing, then build the prototype.
```

For very early ideas, the Skill first asks product-definition questions such as:

- Who is the first target user, and in what moment would they use this?
- What is the single primary outcome the MVP must let them complete?
- What should be included in the first version, and what should be out of scope?

For market, platform, permission, payment, privacy, membership, or "industry common feature" questions, the Skill should research authoritative sources and turn the findings into prototype functions, page states, rules, acceptance criteria, and assumptions.

## Example Input

See [examples/brief-prd.md](examples/brief-prd.md).

## Expected Output

See [examples/expected-output.md](examples/expected-output.md).

## Included Prototype Template

The Skill includes a small Vite + React template and a scaffold script:

```bash
node prd-to-reviewable-prototype/scripts/scaffold-prototype.mjs prototype-review
cd prototype-review
npm install
npm run build
```

Codex uses this as a starting point, then replaces the placeholder screens, states, copy, and data model with the inferred product-specific prototype.

If you use pnpm 10+ and see an `Ignored build scripts: esbuild` warning, run `pnpm approve-builds` once in the generated project, then rerun the build.

## Public-Safe Notes

This repository intentionally does not include private PRDs, generated business prototypes, Figma files, Feishu links, or project-specific documents.

## License

MIT is a good default if you want others to freely use and adapt this Skill.
