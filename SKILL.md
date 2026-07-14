---
name: resume-ats-linkedin-optimizer
description: >-
  Build, rewrite, tailor, and audit a world-class resume/CV and LinkedIn profile
  that wins interviews — optimized at the same time for ATS parsing (Workday,
  Greenhouse, Lever, Taleo, iCIMS, Ashby), fast recruiter skim-reading, and
  LinkedIn recruiter search. Use when the user wants to create, improve, fix, or
  review a resume or CV; tailor a resume to a specific job description; run an ATS
  check or audit; write or strengthen achievement bullet points; quantify
  accomplishments; optimize a LinkedIn headline, About, skills, or experience;
  or generally maximize their chances of getting hired. Governing rule:
  zero fabrication — never invent facts, employers, dates, titles, or numbers.
license: MIT
---

# Resume + ATS + LinkedIn Optimizer

Turn a person's real experience into the strongest possible resume, CV, and
LinkedIn profile — one that survives every major ATS parser, wins the 7-second
recruiter skim, and ranks in LinkedIn recruiter search. This skill encodes what
university career centers (Harvard, MIT), ex-FAANG recruiters, eye-tracking
research, and the actual behavior of production ATS agree on, and resolves the
places where popular advice is wrong or outdated.

## The prime directive: zero fabrication

**Never invent, inflate, or guess a fact.** No fabricated employers, titles,
dates, degrees, or metrics. This is non-negotiable and overrides every other
goal — a resume that lies fails the moment a recruiter or reference check
catches it, and it puts the user's career at risk.

What this means in practice:
- Every number, employer, title, and date must come from the user or a document
  they gave you. If you don't have it, ask — don't fill it in.
- Metrics the user *has but didn't write down* are fair game to **excavate**
  (Phase 2). Estimates are allowed **only** when the user confirms them and they
  are hedged ("~", "approximately", "roughly"). See `assets/metric-proxies.md`.
- You may sharpen *language* freely (weak verb → strong verb, task → outcome,
  vague → specific). You may not sharpen *facts*.
- When you reword something, preserve its truth. "Helped build" does not become
  "single-handedly architected."

If the user pushes you to fabricate, refuse and explain the risk, then offer the
honest alternative (excavate a real number, reframe, or omit).

## Mental model (get this right, everything else follows)

A modern hiring pipeline is **two stages, and parsing is the gate before
everything**:

1. **Parse + store.** The file is flattened to plain text and mapped into fields
   (name, contact, roles, dates, skills). If the parser can't read something, it
   is invisible to *every* downstream step, including any AI layer.
2. **Search + rank + (increasingly) AI-summarize.** Recruiters run keyword
   searches over the parsed database; an LLM layer may summarize and score on
   top. Humans still make the decision.

The load-bearing truth: **ATS almost never auto-reject** (≈92% of recruiters say
theirs don't). The "ATS rejects 75% of resumes" stat is a myth from a defunct
2012 vendor. What feels like bot-rejection is human overload (hundreds to
thousands of applicants) plus knockout questions. So optimize for **(a) clean
parsing and (b) a fast, convincing human skim** — not for gaming a rejection
algorithm that mostly doesn't exist. Details + myths: `references/07-myths-and-truth.md`.

## The single source of truth: the Master Profile

Do not tailor by rewriting from scratch each time. Maintain a **Master Profile**
— an exhaustive, private store of everything the user has ever done (every role,
bullet, metric, skill, project). Every resume and LinkedIn variant is then a
**selection and reframing** of that store, never an invention on top of it. This
is what makes tailoring fast, consistent, and truthful.

- If the user has no Master Profile yet, build one first (`assets/master-profile-template.md`).
- If they do, load it and update it with anything new before tailoring.
- Full workflow and the role "visibility" system: `references/05-master-profile.md`.

## Modes

Detect which the user wants (ask if unclear) and follow the phases below.

| Mode | Trigger | Phases |
|---|---|---|
| **Build** | "make/write my resume", from scratch or from raw material | 0 → 6 |
| **Improve** | "fix / make my resume better", no specific job | 0,1,2,3,5,6 |
| **Tailor** | "tailor my resume to this job" + a job description | 0,1,4,2,3,5,6 |
| **Audit** | "check / score my resume", "is this ATS-friendly" | 0,3,4,6 (report only) |
| **LinkedIn** | "optimize my LinkedIn" | 0,1,7 |
| **Apply/skip** | "should I apply to this?" | 0,4 → `references/03-keywords-and-tailoring.md` gate |

## Workflow

Work through phases in order for the chosen mode. **Gate each phase**: do not
move on until its exit condition is met. Load the linked reference *when you
reach that phase* — don't front-load everything.

### Phase 0 — Intake & Master Profile
- Establish the goal: target role/industry, seniority, and whether there's a
  specific job description. Determine career stage (new grad / mid / senior /
  career-changer) — it drives section order and emphasis.
- Gather raw material: existing resume, LinkedIn export, job history, or a
  conversation. Load into / create the **Master Profile**.
- **Exit when:** you have a Master Profile (even a rough one) and a clear target.

### Phase 1 — Metric Excavation & fact-gathering
- The highest-leverage step. Most people undersell themselves. For each
  significant role/bullet, ask targeted questions to surface real numbers:
  scope (team size, budget, users, volume), change (before → after, %),
  time/speed, money, and quality. Use `assets/metric-proxies.md` to *prompt*
  plausible ranges — but every number must be **confirmed by the user**.
- Also collect: domain/context (the "secret weapon" — "web apps" →
  "fintech card-issuance platform"), tools/tech, and outcomes.
- **Exit when:** each headline achievement has real, user-confirmed substance.

### Phase 2 — Content engineering (bullets, verbs, summary)
- Rewrite every bullet to **Action verb + what you did + quantified impact +
  (how/context)** — the XYZ / Google formula ("Accomplished X, measured by Y, by
  doing Z"). Lead with impact, not task.
- Use strong, *plain* verbs (led, built, designed, cut, shipped, grew); kill
  "responsible for / helped / worked on" and buzzword-inflated verbs. Full
  guidance, verb bank, and before/after examples: `references/02-content-and-bullets.md`
  and `assets/action-verbs.md`.
- Run the **de-slop pass**: remove AI-tells and filler (`assets/ai-slop-blacklist.md`).
- Write the professional summary (if ≥1–2 yrs experience) or objective (new
  grad / career-changer).
- **Exit when:** bullets are outcome-led, quantified where honest, and slop-free.

### Phase 3 — Structure & ATS-safe formatting
- Enforce the non-negotiable ATS format: **single column; no tables, text boxes,
  columns, headers/footers, graphics, or icons; standard section headings;
  standard bullets; web-safe font 10–12pt; contact info in the body.**
- Order sections by career stage; reverse-chronological; dates as
  `Month Year – Month Year` + "Present". Full rules: `references/01-ats-and-formatting.md`.
- **Exit when:** structure passes the ATS-safe checklist in that reference.

### Phase 4 — Keywords & tailoring (Tailor/Audit/Apply modes)
- Analyze the job description: extract and tier keywords (required vs preferred),
  find the most-emphasized terms, run a gap analysis vs the Master Profile.
- Mirror the JD's **exact** hard-skill wording (ATS often don't resolve
  synonyms); include acronym + spelled-out pairs ("SEO (Search Engine
  Optimization)"). Place each key term in ≥2 places (skills + a real bullet).
  **No stuffing, no hidden text** — both backfire. Use `scripts/resume_tools.py
  coverage` for a labeled keyword-coverage estimate. Details + apply/skip gate:
  `references/03-keywords-and-tailoring.md`.
- **Exit when:** required keywords the user genuinely qualifies for are present
  and natural.

### Phase 5 — Render
- Prefer the **LLM-writes-JSON, code-renders-doc** pattern: put content in
  `assets/resume.schema.json` shape, then `python scripts/resume_tools.py render
  --resume resume.json --out resume.pdf` (or `.docx`) produces a clean,
  single-column, ATS-safe file with selectable text. This keeps layout
  deterministic and parseable. Text-based PDF is the safe default for
  submission; keep `.docx` for portals that request Word.
- File name: `Firstname-Lastname-Resume.pdf`.
- **Exit when:** a rendered file exists and its text is selectable/copyable.

### Phase 6 — Evaluate
- Run the scoring rubric and the **truthfulness invariants** (no section
  dropped, no employer/date/title that wasn't in the source, identity
  untouched): `python scripts/resume_tools.py validate` and see
  `references/06-scoring-and-evaluation.md`.
- Do the **skim test**: in 7 seconds can you find name, current title+company,
  and the top achievement? Is the strongest material in the top third?
- Report a **keyword-coverage estimate** (explicitly labeled an estimate, never
  a fake "100/100 ATS score").
- **Exit when:** invariants pass and the skim test succeeds.

### Phase 7 — LinkedIn (LinkedIn mode)
- Port the same keyword spine into LinkedIn, adapting for its algorithm and
  human, in-feed reading: headline (220 chars, front-loaded, keyword-rich),
  About (hook in the first ~300 chars, first-person story, CTA), experience
  (conversational + media), pinned top-3 skills, All-Star completeness.
  Per-field limits, formulas, and checklist: `references/04-linkedin.md`.
- **Exit when:** every field has a concrete recommendation and the profile hits
  All-Star.

## Reference & asset map

Load references on demand as you reach the phase that needs them.

- `references/01-ats-and-formatting.md` — how each ATS parses, what breaks it,
  format rules, headings, dates, PDF vs DOCX, file naming, length.
- `references/02-content-and-bullets.md` — XYZ/CAR formulas, quantification,
  summary vs objective, recruiter skim behavior, red-flag handling, tense/voice.
- `references/03-keywords-and-tailoring.md` — JD analysis, keyword tiering,
  coverage scoring, apply/skip gate.
- `references/04-linkedin.md` — algorithm, per-field limits + formulas, skills,
  featured/recommendations/URL/banner/photo, resume↔LinkedIn diffs.
- `references/05-master-profile.md` — the source-of-truth doc + visibility system.
- `references/06-scoring-and-evaluation.md` — rubric, truthfulness invariants,
  skim test.
- `references/07-myths-and-truth.md` — myths to stop repeating; what's actually true.
- `assets/master-profile-template.md`, `assets/resume.schema.json`,
  `assets/example-resume.json`, `assets/action-verbs.md`,
  `assets/metric-proxies.md`, `assets/ai-slop-blacklist.md`.
- `scripts/resume_tools.py` — `render` (JSON→ATS-safe .docx), `validate`
  (truthfulness invariants), `coverage` (JD keyword-coverage estimate),
  `deslop` (flag AI-tells/filler). `python scripts/resume_tools.py --help`.

## Hard rules (never violate)

1. **Zero fabrication.** See prime directive.
2. **Single column, no tables/graphics/headers-footers.** Parsing gate.
3. **Standard section headings and reverse-chronological order.**
4. **Exact-match JD keywords, placed naturally — never stuffed or hidden.**
5. **Quantify honestly.** Estimates only when user-confirmed and hedged.
6. **No fake "ATS score."** Report a labeled keyword-coverage *estimate* only.
7. **Plain strong verbs over buzzwords.** Run the de-slop pass on every draft.
