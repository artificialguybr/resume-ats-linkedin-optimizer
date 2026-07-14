# Resume + ATS + LinkedIn Optimizer — an AI Agent Skill

> Build, rewrite, tailor, and audit a **job-winning resume/CV and LinkedIn
> profile** — optimized at the same time for **ATS parsing** (Workday,
> Greenhouse, Lever, Taleo, iCIMS, Ashby), the **7-second recruiter skim**, and
> **LinkedIn recruiter search**. Zero fabrication. Fully sourced. Battle-tested.

This is an **[Agent Skill](https://docs.claude.com/en/docs/claude-code/skills)**
for Claude Code (and any agent that reads `SKILL.md`). Point your AI agent at it
and it turns a person's real experience into the strongest possible resume and
LinkedIn profile — the way top university career centers, ex-FAANG recruiters,
and the actual behavior of production ATS say to do it, minus the myths.

If you've ever wondered *"why do I never hear back?"* — this is the fix, and it
does it honestly.

## Why this skill is different

Most resume prompts and "ATS checkers" repeat fear-based myths, invent metrics,
and hand you a two-column template that ATS can't even read. This one is built on
what's actually true:

- **🔒 Zero fabrication.** Never invents employers, titles, dates, degrees, or
  numbers. Instead it *excavates* the real metrics you already have and hedges
  honest estimates. A resume that lies fails the reference check — and your
  career deserves better.
- **📄 Optimizes for all three at once.** ATS parseability **and** human
  skim-readability **and** LinkedIn recruiter-search ranking — not one at the
  expense of the others.
- **🧠 Sourced, not vibes.** Harvard/MIT career services, Google's XYZ formula,
  Ladders eye-tracking research, ex-Amazon/Google recruiters, and the documented
  parsing behavior of real ATS. Myths (the "75% auto-reject" hoax, hidden-text
  keyword stuffing, "PDFs don't parse") are debunked, not repeated.
- **⚙️ Deterministic tooling.** The agent writes the *words*; bundled Python
  tools own *layout and checks* — render an ATS-safe `.docx`, run truthfulness
  invariants, estimate keyword coverage, and strip AI-slop language.
- **🗂️ A Master Profile as source of truth.** Tailoring becomes *selection* from
  everything you've truthfully done — fast, consistent, and honest across every
  job you apply to.

## What it can do

| You want to… | Ask your agent |
|---|---|
| Build a resume from scratch / raw notes | *"Build my resume from this experience."* |
| Make an existing resume much stronger | *"Improve my resume."* |
| Tailor to a specific job | *"Tailor my resume to this job description: …"* |
| Check if it's ATS-friendly | *"Audit my resume for ATS."* |
| Write/quantify achievement bullets | *"Turn these duties into quantified bullets."* |
| Optimize your LinkedIn profile | *"Optimize my LinkedIn headline / About / skills."* |
| Decide whether a job is worth applying to | *"Should I apply to this role?"* |

## Install

### Claude Code
Clone into your skills directory (user-level shown; use `.claude/skills/` inside
a project for project-level):

```bash
git clone https://github.com/artificialguybr/resume-ats-linkedin-optimizer.git \
  ~/.claude/skills/resume-ats-linkedin-optimizer
```

The skill auto-activates when you ask anything resume/CV/ATS/LinkedIn-related.
You can also invoke it explicitly.

### Any other agent (Cursor, Cline, custom, etc.)
The skill is plain Markdown. Add `SKILL.md` (and the `references/`, `assets/`,
`scripts/` folders) to your agent's context, or paste `SKILL.md` as a system
instruction. It's framework-agnostic.

### Optional: the render tool
Rendering a JSON resume to an ATS-safe `.docx` needs one dependency:

```bash
pip install -r scripts/requirements.txt   # python-docx
```

The other tools (`validate`, `coverage`, `deslop`) are pure standard library.

## How it works

The agent follows a gated workflow (only the phases your task needs):

```
Intake → Master Profile → Metric Excavation → Content Engineering
       → ATS Formatting → Keyword Tailoring → Render → Evaluate → (LinkedIn)
```

The **Master Profile** (`assets/master-profile-template.md`) is your private,
exhaustive record of everything you've done. Every resume and LinkedIn variant is
a *selection* from it — never an invention on top of it. That's what makes
tailoring both fast and truthful.

## Bundled tools (`scripts/resume_tools.py`)

```bash
# Render structured JSON → single-column, ATS-safe .docx
python scripts/resume_tools.py render   --resume resume.json --out resume.docx

# Truthfulness invariants: no fabricated employer/date, identity untouched, nothing dropped
python scripts/resume_tools.py validate --resume resume.json --source master-profile.json

# Labeled keyword-coverage ESTIMATE vs a job description (never a fake "ATS score")
python scripts/resume_tools.py coverage --resume resume.json --jd job.txt

# Flag AI-slop: buzzwords, inflated verbs, filler, em-dash tics
python scripts/resume_tools.py deslop   --resume resume.json
```

See `assets/example-resume.json` for the input shape and
`assets/resume.schema.json` for the full schema.

## What's inside

```
SKILL.md                     ← the orchestrator (start here)
references/
  01-ats-and-formatting.md   ← how each ATS parses; format rules; PDF vs DOCX
  02-content-and-bullets.md  ← XYZ/CAR bullets; quantification; recruiter skim
  03-keywords-and-tailoring.md ← JD analysis; keyword tiering; apply/skip gate
  04-linkedin.md             ← algorithm; per-field limits + formulas; checklist
  05-master-profile.md       ← the single source of truth + visibility system
  06-scoring-and-evaluation.md ← rubric; truthfulness invariants; skim test
  07-myths-and-truth.md      ← ATS myths debunked
assets/                      ← templates, JSON schema, verb bank, metric proxies, slop blacklist
scripts/                     ← resume_tools.py (render / validate / coverage / deslop)
```

## A few myths this skill refuses to repeat

- ❌ *"ATS auto-reject 75% of resumes."* — A myth from a defunct 2012 vendor. ~92%
  of recruiters say their ATS doesn't auto-reject. What kills you is human
  overload + knockout questions.
- ❌ *"Hidden white-text keywords beat the bot."* — Modern AI layers detect it and
  flag you as manipulative.
- ❌ *"ATS can't read PDFs."* — Outdated since ~2019. The killer is a *two-column*
  or *image* layout, not the PDF container.
- ❌ *"Cram the keyword 12 times."* — Stuffing ranks you *lower* and reads as spam.

Full list with the truth: `references/07-myths-and-truth.md`.

## Contributing

Issues and PRs welcome — especially newer ATS behavior, LinkedIn field changes,
and additional metric-proxy benchmarks. Keep the **zero-fabrication** principle
intact.

## License

MIT — see [LICENSE](LICENSE). Go get the job.
