# Linting (Vale)

Vale is configured in `.vale.ini` and runs automatically on PRs via GitHub
Actions (`.github/workflows/vale.yml`).

## Running Vale locally

```sh
vale src/
```

## Custom rules

Custom rules live in `.github/vale/Matter/`. Read the specific rule file to
understand what it checks before fixing a flagged issue.

- `BadHexNumberFormat` — hex number formatting
- `BadListFormat` — list formatting
- `BadPlurals` — common plural errors
- `British` — British vs. American English
- `CSA` — Alliance-specific terminology
- `EOLWhitespace` — trailing whitespace
- `LineLength` — line length limits
- `SentenceSpacing` — spacing between sentences
- `Tabs` — tab characters
- `TitleCase` — heading title case

Some rules are currently disabled in `.vale.ini` while issues are being
resolved: `LineLength`, `SentenceSpacing`, `BadPlurals`, `BadReferences`,
`BadListFormat`.

## Vocabularies

Custom word lists live in `.github/vale/config/vocabularies/`. If you introduce
a new proper noun, acronym, or technical term that Vale flags, add it to the
appropriate vocabulary or word list file.

## Fixing Vale errors

1. Read the specific Vale rule file in `.github/vale/Matter/`.
2. Fix the content to comply, or add legitimate terms to the vocabulary.
3. Do **not** disable rules without explicit approval.
