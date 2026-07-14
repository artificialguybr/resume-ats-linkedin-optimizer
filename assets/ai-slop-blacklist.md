# AI-Slop Blacklist & De-Slop Pass

Recruiters increasingly recognize (and discount) AI-generated resume language.
Run every draft through this pass. `scripts/resume_tools.py deslop` flags these.

## Inflated verbs → plain replacement

| Slop | Use instead |
|---|---|
| spearheaded | led |
| orchestrated | coordinated |
| architected | designed |
| leveraged | used |
| utilized | used |
| facilitated | ran / helped |
| championed | advocated for |
| pioneered | introduced |
| harnessed | used |
| helmed | led |
| navigated | managed |

## Empty buzzwords → cut or make concrete

`synergy, synergize, paradigm, robust, scalable, actionable, impactful,
best-in-class, cutting-edge, world-class, next-level, move the needle,
low-hanging fruit, think outside the box, results-driven, detail-oriented,
team player, hard worker, go-getter, self-starter, dynamic, passionate, holistic,
seamless, game-changer, value-add, mission-critical, deep dive.`

Rule: if a word describes you but proves nothing, delete it and show the proof
instead. "Results-driven marketer" → "Grew qualified leads 40% in two quarters."

## Filler phrases → tighten

| Filler | Use instead |
|---|---|
| in order to | to |
| on a daily basis | daily |
| due to the fact that | because |
| a wide variety of | many / (name them) |
| responsible for | (lead with the action verb) |
| tasked with | (lead with the action verb) |
| successfully | (delete — show the success) |
| various | (name them or delete) |

## Punctuation / style tells

- Em-dash "—" and double-hyphen "--" tics: replace with a comma, period, or "to".
- Over-uniform bullet lengths and rhythm — vary them; real bullets aren't
  identical widgets.
- Delete trailing periods inconsistency; pick one convention.
- Kill exclamation points and ALL-CAPS emphasis.

## De-slop checklist

- [ ] No inflated verbs (used plain equivalents)
- [ ] No empty buzzwords (replaced with concrete proof)
- [ ] No filler phrases
- [ ] No em-dash/double-hyphen tics
- [ ] Varied bullet rhythm; each leads with impact
- [ ] Reads like a specific person wrote it about specific work
