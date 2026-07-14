# Keywords & Tailoring to a Job Description

Tailoring is **selection and mirroring**, not invention. Pull from the Master
Profile (`05-master-profile.md`) and match the target job's language honestly.

## Step 1 — Analyze the job description

Extract and tier the keywords:
- **Required / must-have** — hard skills, tools, technologies, certifications,
  methodologies, and the **exact job title**. These are what parsers and Boolean
  searches catch.
- **Preferred / nice-to-have** — secondary skills and bonus qualifications.
- **Contextual** — domain, industry, scale, team-shape words that show fit.

Note **frequency and placement**: a skill named 5× (and in the title) outranks
one mentioned once — reorder your content to lead with the emphasized ones.
Soft-skill phrases ("excellent communicator") are nearly invisible to parsers —
demonstrate them through achievements, don't list them.

## Step 2 — Gap analysis

Compare the tiered keywords against the Master Profile:
- **Have + shown** — already present in a real bullet. Good.
- **Have, not shown** — genuinely qualified but not surfaced. Add it (skills +
  a real bullet).
- **Don't have** — leave it off. Do **not** fabricate it. If many required items
  are missing, see the apply/skip gate below.

## Step 3 — Mirror the language (exact match)

- Use the JD's **exact wording** for hard skills. Strict-match ATS (Taleo,
  Oracle, iCIMS/Brassring, and largely Greenhouse) don't resolve synonyms or
  word roots — "React.js" ≠ "React" to a dumb matcher, so match the JD's form.
- **Acronyms both ways:** "Search Engine Optimization (SEO)" on first use, then
  the acronym. Exact-match ATS won't connect the two automatically.
- Place each key term in **≥2 places** — the Skills section **and** a real
  experience bullet — so it reads as demonstrated, not listed.

## Step 4 — Do NOT stuff or hide

- **Keyword density is a myth and stuffing backfires.** Repeating "project
  management" 12× ranks *lower* than natural, varied phrasing; recruiters (~76%)
  want natural use. Use each key term ~1–3×.
- **Never use hidden/white text.** 2025/2026 AI layers actively detect it and
  flag the application as manipulative. High risk, negative reward.
- Modern AI/semantic layers understand context ("built ETL pipelines for
  financial data" fits "Data Engineer at a bank"), so **write clearly and
  factually** — that satisfies both the exact-match gate and the AI layer.

## Step 5 — Coverage estimate (label it honestly)

Report a **keyword-coverage estimate**, never a fake "100/100 ATS score." Use:

```
python scripts/resume_tools.py coverage --resume resume.json --jd job.txt
```

It reports the % of JD-required and preferred keywords present in the resume, and
lists misses. Interpretation of the weighted score:

```
Score = 0.40 * required_skills_coverage
      + 0.20 * preferred_coverage
      + 0.20 * achievement_quantification_rate   # % of bullets with a metric
      + 0.10 * section_completeness               # present standard sections / 5
      + 0.10 * keyword_distribution               # sections containing JD terms / sections with content
```

Bands (heuristic, communicate as guidance not gospel): **85%+ strong · 70–84%
moderate · <70% weak.** Always state that this estimates keyword fit, not a
specific ATS's internal score.

## The apply/skip gate ("should I even apply?")

Before spending effort tailoring, score fit and decide:

```
Overall = required_coverage * 0.7 + preferred_coverage * 0.3
```

| Band | Read | Action |
|---|---|---|
| 90–100% | Likely overqualified (flight-risk perception) | Apply; position for the right level |
| 75–89% | Strong fit | Apply immediately, tailored |
| 60–74% | Good fit with gaps | Apply with a strong cover letter addressing gaps |
| 50–59% | Stretch | Apply only if genuinely interested; lead with transferable wins |
| <50% | Poor fit | Skip unless it's a dream role — spend the time elsewhere |

Also scan the JD for **red flags** (unrealistic requirement stacks, vague scope,
churn signals) and surface them so the user decides with eyes open.

## Multi-job batching

With a Master Profile, tailoring N jobs = N selections from one truthful store.
Keep a small per-variant note of which roles/bullets were emphasized or hidden
and why (visibility system in `05-master-profile.md`), so variants stay
consistent and you never re-derive facts.
