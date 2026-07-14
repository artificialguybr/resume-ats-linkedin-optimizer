# The Master Profile (single source of truth)

The Master Profile is a **private, exhaustive record of everything the user has
ever done** — every role, bullet, metric, skill, tool, project, and credential.
Every resume and LinkedIn variant is a **selection and reframing** of this store,
never an invention on top of it.

## Why it exists

- **Truthfulness.** If a fact isn't in the Master Profile, it doesn't go on a
  resume. This is the mechanical enforcement of the zero-fabrication rule.
- **Speed.** Tailoring becomes *choosing which true things to show*, not writing
  from scratch each time.
- **Consistency.** Every variant traces back to the same facts, so dates, titles,
  and metrics never drift between versions.
- **Batching.** N job applications = N selections from one store.

## How to build one

1. Load everything the user has: existing resume(s), LinkedIn export, brag docs,
   performance reviews, old job descriptions.
2. Fill `assets/master-profile-template.md` — capture *more* than any single
   resume would show (extra bullets, secondary skills, side projects).
3. Run **Metric Excavation** (Phase 1): for each role, ask the targeted questions
   to surface real, user-confirmed numbers and store them here. Numbers live in
   the Master Profile once, then flow into every variant.
4. Keep it updated: before any tailoring session, add anything new.

## The visibility system

Tag each role/bullet so selection is fast and intentional:

- `always` — core to the user's identity; appears on essentially every resume.
- `variant-specific` — include only for certain target roles/industries.
- `on-request` — include only if the JD or user calls for it.
- `reference-only` — never shown as-is (context, personal notes, raw metrics to
  draw from).

When you tailor, also record an **"Excluded from this variant, and why"** note —
it makes revisions and multi-job batches coherent and prevents accidentally
dropping something important.

## Relationship to outputs

```
Master Profile (all true facts, exhaustive)
        │  select + reframe (never invent)
        ├── Resume variant A  (tailored to Job A, ATS-safe, 1–2 pages)
        ├── Resume variant B  (tailored to Job B)
        └── LinkedIn profile  (superset, conversational, always current)
```

The Master Profile can hold everything; each output is a curated subset shaped by
the target and the medium's rules (`01`–`04`).
