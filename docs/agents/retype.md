# Retype Markdown Conventions

Retype extends standard Markdown. Full syntax: <https://retype.com/components/>.
Key features used in this project:

## Front matter

Every content page starts with YAML front matter:

```yaml
---
icon: home
label: Home
toc:
  depth: 2
---
```

Common front-matter keys: `icon`, `label`, `layout`, `order`, `toc`,
`visibility`, `tags`, `description`.

## Folder configuration

Folders can have an `index.yml` file (separate from `index.md`) that configures
the navigation label, icon, order, and expanded state for that section.

## Components

- **Panels / Alerts:** `!!!` blocks with variants like `!!!success`, `!!!warning`
- **Cards:** `[!card title="..." text="..." icon="..." layout="compact"](url)`
- **Buttons:** `[!button variant="..." icon="..." text="..."](url)`
- **References:** `[!ref text="..." icon="..." target="blank"](url)`
- **Icons:** `:icon-name:` syntax (uses Octicons), e.g. `:icon-home:`
- **Badges and Tabs:** See Retype docs for syntax.

## Navigation

- `index.md` files serve as the landing page for a section.
- `index.yml` files in the same directory configure section-level settings
  (label, icon, ordering, expanded state).
- Page ordering can be controlled via `order` in front matter or `index.yml`.
