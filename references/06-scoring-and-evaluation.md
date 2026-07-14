# Scoring & Evaluation

Most resume tools *assert* they produce great resumes; almost none *measure* it.
This skill evaluates every output three ways: truthfulness invariants (hard
gates), a labeled coverage/quality score, and the human skim test.

## 1. Truthfulness invariants (hard gates — must all pass)

These are cheap, deterministic checks. Run `python scripts/resume_tools.py
validate --resume resume.json --source master-profile.json`. Any failure blocks
the output:

- **No section silently dropped.** Every populated section in the source is
  represented (or its removal was explicit).
- **No fabricated employer.** Every company in the output appears in the source.
- **No fabricated dates/titles.** Every role's title and dates trace to the source.
- **Identity untouched.** Name, contact, and personal info match the source
  exactly.
- **Schema-valid.** Output validates against `assets/resume.schema.json`.
- **Metrics accounted for.** Numbers present in the output either exist in the
  source or are flagged as user-confirmed estimates (hedged with "~/approx").

If a check trips, stop and reconcile with the user — never "fix" it by inventing.

## 2. Coverage & quality score (labeled estimate, not a fake ATS score)

Never present a precise "100/100 ATS score" — no tool actually replicates a
specific ATS. Report this as an explicit *estimate* of keyword fit + quality:

```
Score = 0.40 * required_skills_coverage        # JD required terms present
      + 0.20 * preferred_coverage               # JD preferred terms present
      + 0.20 * achievement_quantification_rate  # % of bullets with a metric
      + 0.10 * section_completeness              # standard sections present / 5
      + 0.10 * keyword_distribution              # sections with JD terms / content sections
```

`python scripts/resume_tools.py coverage --resume resume.json --jd job.txt`
computes it. Bands (guidance): **85%+ strong · 70–84% moderate · <70% weak.**
Always say what it measures (keyword fit + quantification) and what it does not
(a real ATS's internal verdict).

## 3. The de-slop pass

Run `python scripts/resume_tools.py deslop --resume resume.json` to flag AI-tells
and filler (buzzwords, inflated verbs, em-dash tics, "responsible for"). See
`assets/ai-slop-blacklist.md`. Every draft gets this pass — it's the difference
between a resume that reads human and one that reads generated.

## 4. The human skim test (7 seconds)

Simulate the recruiter scan:
- In ~7 seconds, can you find **name, current title + company, and the single
  best achievement**?
- Is the strongest, most-quantified, keyword-rich material in the **top third**?
- Does every bullet lead with impact, start with a strong plain verb, and read
  cleanly on one line?
- Any red flags (gaps, hopping) framed, not hidden?

If the skim fails, the parse-perfect resume still loses. Fix ordering and the
top-third content, then re-run.

## Evaluation summary to give the user

Report, briefly and honestly:
1. Truthfulness invariants: pass/fail (must be all pass).
2. Coverage estimate: X% with the top 3–5 missing keywords they genuinely
   qualify for.
3. De-slop findings applied.
4. Skim-test result and any ordering fixes made.
