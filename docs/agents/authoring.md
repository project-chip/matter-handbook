# Content Authoring Reference

Detailed authoring conventions. The always-on guardrails are in `AGENTS.md`;
the canonical author guidelines are in `README.md` — keep the three consistent.

## Tone and style

- **Non-normative language only.** Never use "must," "shall," or "required."
  Use "typically," "consider," "common pattern," etc. This handbook explains
  and guides; it does not define requirements.
- Keep content **informative and version-agnostic** where possible.
- Use durable terminology. Add synonyms to aid discoverability.
- The official Matter specification, SDK documentation, and Alliance policies
  are always the **source of truth**. This handbook is a companion, not a
  replacement.

## Alliance naming

- First reference: "Connectivity Standards Alliance (Alliance)".
- Subsequent references: "Alliance".

## Acronyms

- Write out acronyms on first use with the abbreviation in parentheses.
  Example: "Three Letter Acronym (TLA)".
- Add new acronyms to `acronyms.dic` in `.github/vale/config/dictionaries/`
  (hunspell-based, used by Vale).
- Add new acronyms to the Glossary if appropriate.

## Confidentiality

This is a **public** website. Never include Alliance-confidential information.

## Links and access levels

- Prefer links to **public** resources (Alliance public website, `project-chip`
  GitHub repositories).
- If a page links to any Alliance member-only resource, add this disclaimer at
  the top of the page:
  `> Some links on this page are only accessible to Alliance members.`
- For resources intended for Adopter members, link to the "All Members" section
  in Causeway when possible. If a needed resource is not in that folder,
  consider moving it.
- Pages with resources aimed specifically at Participant and Promoter members
  (private GitHub repos, Matter working group documents in Causeway) should
  carry the member-only disclaimer at the top.

## Localization

- English content is the primary source in `src/en/`.
- Japanese content mirrors the English structure in `src/ja/`.
- Each locale has its own Retype configuration (`retype.yml` at the root for
  English, `src/ja/retype.yml` for Japanese).
- When editing English content, do **not** automatically modify Japanese files
  unless explicitly asked. Localization is handled separately.

## Common tasks

### Adding a new page

1. Create a `.md` file in the appropriate section under `src/en/`.
2. Add YAML front matter with at least `label` and optionally `icon`, `order`.
3. If it is a new section, create both `index.md` (landing content) and
   `index.yml` (navigation config).
4. Ensure Vale passes on the new content.

### Editing existing content

1. Read the existing file fully before making changes.
2. Preserve Retype-specific syntax (front matter, components, icons).
3. Follow the non-normative tone and style guidelines above.
4. Preserve existing link disclaimers about member-only resources.
