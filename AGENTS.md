# AGENTS.md

The Matter Handbook is a **public, community-maintained documentation site**
(not a code project) at <https://handbook.buildwithmatter.com>. It helps people
understand the Matter protocol, build products, navigate certification, and
participate in the Connectivity Standards Alliance (Alliance). Content is
Markdown in `src/en/` (and `src/ja/`), rendered into a website by
[Retype](https://retype.com).

## Always-on guardrails

- **Public site.** Never include Alliance-confidential information.
- **Non-normative tone.** Never use "must," "shall," or "required." Use
  "typically," "consider," "common pattern," etc. The handbook guides; it does
  not define requirements.
- **Source of truth.** The Matter specification, SDK docs, and Alliance policies
  are authoritative. This handbook is a companion, not a replacement.
- **Member-only links.** If a page links to any Alliance member-only resource,
  add this disclaimer at the top: `> Some links on this page are only accessible to Alliance members.`
- **Localization is separate.** When editing English content in `src/en/`, do
  not modify the Japanese mirror in `src/ja/` unless explicitly asked.
- **Changes go through PRs** with the correct label; never push to `main`.

## Reference docs (read when relevant)

- **`docs/agents/authoring.md`** — tone/style, Alliance naming, acronyms,
  link/access rules, localization, and how to add or edit a page.
- **`docs/agents/retype.md`** — Retype Markdown: front matter, `index.yml`
  folder config, components (cards, panels, buttons, icons), navigation.
- **`docs/agents/linting.md`** — Vale setup, custom rules, vocabularies, and
  how to fix lint errors.
- **`docs/agents/repository.md`** — repo structure, key config files, build &
  preview commands, CI/CD workflows, and the git/PR workflow.

Other useful files: `README.md` (author guidelines), `CONTRIBUTING.md` (full
contributor workflow). When in doubt about a convention, check existing pages
for patterns.
