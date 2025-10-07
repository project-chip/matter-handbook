## Contributing to the Matter Handbook

Welcome - thanks for taking the time to improve the Matter Handbook.

> [!NOTE]
> For questions, clarifications, or early ideas, start a Discussion instead of opening an Issue;
> Issues are reserved for concrete, actionable work items.

---

### Summary

The contribution process is intentionally lightweight and entirely pull‑request (PR) based:
every change - large or small, including typo fixes - comes in as a PR so it can be reviewed, validated by automation,
and merged transparently.

Classify the change with the most specific label (`editorial`, `tooling`, or one or more domain labels;
add `do not merge` only when you deliberately want to block). Every PR requires at least one maintainer approval.
When a domain label is present, the external `sme-aproval` check must also succeed, confirming that the appropriate
subject‑matter experts have signed off. All mandatory automated checks (including Vale) must be green,
there must be zero unresolved review threads and no active “changes requested” reviews,
the PR cannot be in draft state or have merge conflicts, and the blocking `do not merge` label must be absent.
Once these conditions are satisfied, the merge is performed automatically—no further manual action is needed.
If you are new to GitHub: a PR is simply a proposed set of changes that others can comment on before it is merged.

---

All changes flow through this PR pipeline (there is no direct push to main, even for small editorial tweaks);
this ensures consistency, traceability, and required approvals without extra ceremony for contributors
who are less familiar with GitHub.

### Labels

| If your change… | Use this label | Extra gate |
|-----------------|---------------|------------|
| Pure wording / typos / formatting (no meaning change) | `editorial` | Maintainer approval |
| CI, workflows, devcontainer, build infra | `tooling` | Maintainer approval |
| Semantic/content change in a domain (e.g. certification) | Domain label (e.g. `certification`) | Maintainer approval + `sme-aproval` |
| Needs a temporary hold | `do not merge` | Blocks merge |

Rules:
- Any semantic impact then use a domain label (not `editorial`).
- Multiple domain labels allowed; external check enforces SME coverage.
- Don’t remove a domain label to bypass review.

---

### Merge Conditions

All must be true for auto‑merge:
- Maintainer approval present.
- If domain label: `sme-aproval` succeeded.
- Vale success.
- No unresolved review threads (`#review-threads-unresolved=0`).
- No “changes requested” reviews.
- Not draft; no merge conflicts.
- No `do not merge` label.

---

### Roles

| Role | Responsibility |
|------|----------------|
| Author | Correct labels, clear scope, address feedback |
| Maintainer | Process, risk, coherence |
| SME (external) | Domain accuracy (per domain label) |

---

### Review Discipline

- Resolve threads only after action or explicit agreement.
- Keep scope tight; split unrelated chunks.
- Avoid large force-pushes mid-review (cleanup near the end is fine).
- Don’t game the process by dropping needed labels.

---

### Escalation

If blocked >5 business days:
- Comment and mention `@project-chip/handbook-maintainers`.
- Open a Discussion for structural or multi-domain proposals.
