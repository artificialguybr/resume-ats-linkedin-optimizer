# ATS Parsing & ATS-Safe Formatting

How real Applicant Tracking Systems read a resume, what breaks them, and the
exact formatting rules that survive all of them. Optimize for **clean parsing +
fast human skim**, not for a mythical auto-reject bot (see `07-myths-and-truth.md`).

## How parsing actually works

A resume goes through two stages; **parsing is the gate before everything**:

1. **Ingestion + parsing** — the file is converted to plain text, layout is
   stripped, and a parser maps text into fields: name, contact, work history
   (with dates), education, skills. Anything the parser mis-reads or drops is
   invisible to every later step, including AI screening.
2. **Search / rank / AI** — recruiters run Boolean keyword searches over the
   parsed database (results stack-ranked by how often search terms appear); an
   LLM layer increasingly summarizes and scores on top of the extracted text.

Design implication: if it doesn't survive step 1 as clean text, nothing else
matters.

## What breaks parsing (in rough order of severity)

1. **Multiple columns / two-column layouts** — the #1 failure (~34% of parse
   errors). Parsers read left-to-right, top-to-bottom, so two columns interleave
   into gibberish. Single-column resumes parse ~96% complete vs ~78% for
   two-column/designer exports. **Use one column.**
2. **Headers & footers** — many parsers (Workday especially) strip them. Contact
   info placed there can vanish. **Put nothing critical in the header/footer.**
3. **Tables** (including invisible "layout" tables) — scramble chronology and
   field mapping; the top Taleo failure. A neat skills table becomes a garbled
   string. **No tables.**
4. **Text boxes, graphics, icons, logos, charts, photos, skill bars** — not
   extractable as text; anything inside them disappears. **None of these.**
5. **Non-standard bullet characters** (→ ✓ ➤ ✦) — tokenize as junk and fragment
   bullets. **Use standard round/square bullets.**
6. **Decorative/unusual fonts** — character-mapping errors. **Web-safe fonts only.**
7. **Image-based / scanned PDFs** — the real format killer. Text must be
   selectable.

## Platform-specific behavior

| Platform | Style | Notes |
|---|---|---|
| **Workday** | Strictest; exact section labels | Strips headers/footers; wants contact in first ~10–15 lines; prefers `MM/YYYY`; can drop multi-word skills |
| **Taleo** | Oldest, strict; needs `MM/YYYY` | A misread heading shifts everything after it; **silently deletes** content; tables are its #1 failure |
| **Greenhouse** | Sovren parser, more tolerant/semantic | Cleanest with conventional single-column headings; still rewards standard labels |
| **Lever** | Most forgiving | Aggressive sidebar stripping (lost ~60% of multi-column content in tests); stores "Present" literally |
| **iCIMS** | Post-parse validation, flags uncertain fields | Reads columns straight across → gibberish; recognizes "Present" but not "Ongoing/Now/Current" |
| **Ashby / SmartRecruiters** | Modern, tolerant | Clean single-column parses well everywhere |
| **LinkedIn** | Profile-first | Recruiters Boolean-search the DB; your *profile* usually drives visibility more than the uploaded file — mirror keywords there too |

**Rule of thumb:** a single-column, no-table, no-header/footer, standard-heading,
standard-bullet, text-based file survives all of them. Design for the strictest
(Workday/Taleo) and you're safe everywhere.

## File format: PDF vs DOCX (sources disagree — here's the defensible call)

- **The container is rarely the failure — the layout is.** Both PDF and DOCX
  parse well when the file is clean/single-column/text-based; both fail on
  columns/tables/graphics.
- **Default: text-based PDF** exported from a word processor (not a scan, not
  "print to image"). Reliable parsing across modern ATS + pixel-stable for the
  human reader.
- **Use DOCX when:** the posting requests it; a legacy strict parser (older
  Taleo/Workday) is involved (DOCX has more deterministic extraction order); or
  the portal does field autofill from the file.
- **Always obey an explicit format instruction** in the posting.
- The test that settles it: open the file, select-all, copy into a plain-text
  editor. If the text comes out clean and in order, the ATS can read it. Keep
  both PDF and DOCX on hand.

## Canonical section headings (use these — don't get creative)

Recognized reliably by all major parsers:
- **Summary** (or "Professional Summary")
- **Work Experience** (or "Experience" / "Professional Experience" — all fine)
- **Education**
- **Skills** (or "Technical Skills")
- **Certifications**
- Optional: **Projects**, **Publications**, **Awards**

Avoid cute headings ("Where I've Made an Impact"). Do **not** over-police the
standard synonyms — "Professional Experience" and "Technical Skills" are
standard and safe; some guides wrongly claim otherwise.

## Section order (reverse-chronological, US standard)

1. Contact (in the body, top of page)
2. Summary (optional but recommended if experienced)
3. Work Experience (reverse-chronological)
4. Education
5. Skills
6. Certifications / extras

Reorder by career stage:
- **New grad:** Contact → Summary/Objective → Education → Projects/Internships →
  Experience → Skills (education first — it's the strongest asset).
- **Mid/Senior:** Contact → Summary → Experience → Skills → Education →
  Certifications (experience dominates; education drops to the bottom).
- **Career-changer:** Contact → bridging Summary → Skills/Relevant Projects →
  reframed Experience → Education (emphasize transferable skills).

## Dates

- Format `Month Year – Month Year` (e.g., "January 2018 – April 2022"); parsers
  recognize this range. Workday/Taleo prefer `MM/YYYY` precision.
- Use the literal word **"Present"** for current roles (avoid Current/Now/Ongoing).
- Right-aligned dates are fine in a single-column layout.

## Contact info

- In the **document body**, top of page — never in a header/footer.
- Name on its own top line; then phone, professional email, city/state, LinkedIn
  URL — each on its own line or plainly delimited (pipe/comma). Plain-text URLs,
  not icons. No photo, age, full street address, or personal data.

## Formatting specifics

- **Layout:** single column. No tables/text boxes/columns/graphics.
- **Fonts:** Calibri, Cambria, Georgia, Arial, Helvetica, Times New Roman,
  Garamond, Tahoma, Verdana. Body 10–12pt; headings 14–16pt; name largest.
- **Margins:** 1 inch standard; 0.5 inch absolute minimum.
- **Bullets:** standard solid/open circles or squares; no custom symbols.
- **Punctuation:** consistent; digits not words (8, not eight); no trailing
  periods on bullets (be consistent either way).

## Length (the one-page rule is outdated)

- **1 page** for under ~10 years of experience / students / new grads.
- **2 pages** beyond ~10 years — 2025/2026 recruiter surveys show a majority now
  accept or prefer 1–2 pages.
- **3 pages** only for executive / academic / federal / medical CVs.
- ATS do **not** penalize length. Because humans skim, the strongest,
  keyword-rich, quantified material must sit in the **top third** regardless.

## File naming

`Firstname-Lastname-Resume.pdf` (hyphens or underscores travel more predictably
than spaces across systems). Include the full name. Obey any posting-specified
naming convention.

## The ATS-safe checklist (Phase 3 exit gate)

- [ ] Single column, no tables/text boxes/columns
- [ ] No content in headers or footers (contact info in body top)
- [ ] No graphics, icons, logos, charts, photos, skill bars
- [ ] Standard section headings, reverse-chronological
- [ ] Standard bullet characters
- [ ] Web-safe font, 10–12pt body / 14–16pt headings, ≥0.5" margins
- [ ] Dates as `Month Year – Month Year` + "Present"
- [ ] Text is selectable/copyable (not an image)
- [ ] Acronyms spelled out once with the acronym in parentheses
- [ ] File named `Firstname-Lastname-Resume.pdf`, correct format for the portal
