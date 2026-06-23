# Repository, Build & CI Reference

## Repository structure

```text
.
├── .devcontainer/          # Dev Container configuration
├── .gemini/                # Gemini AI agent configuration
├── .github/
│   ├── ISSUE_TEMPLATE/     # Issue templates (YAML)
│   ├── vale/               # Vale linting rules and config
│   │   ├── Matter/         # Custom Matter style rules
│   │   └── config/         # Dictionaries and vocabularies
│   └── workflows/          # GitHub Actions CI/CD
├── docs/agents/            # Agent reference docs (this directory)
├── src/
│   ├── en/                 # English content (primary)
│   │   ├── _includes/      # Shared HTML partials (e.g. head.html)
│   │   ├── alliance/       # Alliance membership and working groups
│   │   ├── certification/  # Certification process and guides
│   │   ├── development/    # SDK and development resources
│   │   ├── glossary/       # Glossary of terms
│   │   ├── guides/         # Practical how-to guides (e.g. DCL)
│   │   ├── how-it-works/   # Core Matter concepts and protocol
│   │   ├── specification/  # How to read and navigate the spec
│   │   └── static/         # Images, logos, and other static assets
│   └── ja/                 # Japanese localization
├── retype.yml              # Primary Retype configuration (English)
└── .vale.ini               # Vale linter configuration
```

## Key configuration files

- **`retype.yml`** — Main Retype configuration. Sets input to `src/en`, output
  to `.retype`, defines theming, navigation links, footer, and metadata. The
  Japanese build uses `src/ja/retype.yml`.
- **`.vale.ini`** — Vale linter configuration. Styles live in
  `.github/vale/Matter/`. Custom vocabularies and dictionaries are in
  `.github/vale/config/`.
- **`.devcontainer/devcontainer.json`** — Dev Container using the official
  Retype Docker image.

## Build and preview

The recommended workflow is the VS Code Dev Container (`retypeapp/retype:4.4.0`).
Reopen the project in the container, then run a build command in the terminal.

```sh
retype build             # Build the English site to .retype/
retype build src/ja      # Build the Japanese site
retype watch             # Live-reload dev server
```

The `.retype/` output directory is git-ignored. See `CONTRIBUTING.md` for the
full contributor walkthrough.

## CI/CD workflows

| Workflow                    | Trigger                   | Purpose                          |
| :-------------------------- | :------------------------ | :------------------------------- |
| `vale.yml`                  | Pull requests             | Lint Markdown with Vale          |
| `retype-build.yml`          | Called by other workflows | Reusable build (EN + JA)         |
| `publish.yml`               | Push to `main`            | Build and deploy to GitHub Pages |
| `pr-preview-publish.yml`    | Pull requests             | Deploy PR preview                |
| `pr-preview-remove.yml`     | PR close                  | Clean up PR preview              |
| `retype-version-update.yml` | (Dependabot / manual)     | Update Retype version            |

The site is deployed to GitHub Pages from the `gh-pages` branch via the
`retypeapp/action-github-pages` action.

## Git and PR workflow

The authoritative guide is `CONTRIBUTING.md`. In short:

- All changes go through Pull Requests; never push directly to `main`.
- PRs are label-driven: `editorial` (wording/typos/formatting), a domain label
  (e.g. `certification`, `transport`) for content/meaning changes, `tooling`
  (CI/infra/build), and `do not merge` to block auto-merge.
- Auto-merge occurs when all approvals and checks pass; branches are
  auto-deleted after merge.
