# PRD to Reviewable Prototype Skill

A Codex Skill that turns early product ideas, brief PRDs, or incomplete PRDs into runnable, browser-shareable interaction prototype review tools.

It is built for product managers, designers, frontend engineers, QA, and reviewers who need to align on flows, states, interactions, and review comments before full implementation.

## What It Does

- Reads brief or incomplete PRDs.
- Assesses product-definition maturity before designing screens.
- Asks targeted clarification questions when key product or interaction details are missing.
- Infers product goals, pages, primary flows, branch flows, page states, edge cases, interaction rules, and acceptance criteria.
- Builds a Vite + React + TypeScript + Tailwind CSS prototype review app.
- Supports clickable prototype screens, Flow overview, scoped states, review comments, localStorage persistence, delete/edit/resolve actions, and `review-notes.json` export.
- Produces a browser-only `dist/index.html` that can be sent to reviewers without requiring Node.js.

## Why This Skill Is Different

Most PRD or product skills stop at writing documents. This Skill pushes the PRD into a usable review artifact:

- Concrete screens instead of only text.
- Flow screens with states and comments embedded.
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
Here is my brief PRD. Use the PRD to Reviewable Prototype skill. Ask me targeted questions first if key details are missing, then build the prototype.
```

For very early ideas, the Skill first asks product-definition questions such as:

- Who is the first target user, and in what moment would they use this?
- What is the single primary outcome the MVP must let them complete?
- What should be included in the first version, and what should be out of scope?

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
