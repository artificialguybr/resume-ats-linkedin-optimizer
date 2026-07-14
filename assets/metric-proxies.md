# Metric Proxy Benchmarks (for guided estimation)

Use these ranges to **prompt the user** for real numbers during Metric Excavation
(Phase 1) — "was it closer to 10K or 1M users?", "roughly how many tickets a
week?". They help someone who never wrote their numbers down recall a plausible
figure.

**Hard rule:** these are conversation aids, never facts. A number goes on the
resume **only after the user confirms it**, and estimates are hedged ("~",
"approximately", "roughly"). Never silently insert a benchmark as if it were the
user's actual result. See the prime directive in `SKILL.md`.

## Excavation questions (ask per role/bullet)

- **Scope:** How many people/clients/users/accounts did this touch? Team size?
  Budget? Volume (transactions, tickets, records) per day/week/month?
- **Change:** What was it before vs after? By how much (%, absolute)?
- **Time/speed:** How much faster? How much time saved (× frequency)?
- **Money:** Revenue influenced, cost saved, budget owned?
- **Quality:** Error rate, satisfaction/NPS, ranking, SLA, adoption?
- **Comparison:** vs the prior year / prior process / the team average / target?

## Benchmark ranges by function (to jog memory, then confirm)

**Software Engineering** — users served 1K–5M; bugs 5–30/sprint; uptime
99.5–99.99%; code review 5–20 PRs/wk; CI/CD or build-time improvement 30–80%;
latency cuts 20–60%; test coverage 50–90%.

**Data / ML** — dataset size MBs–TBs; model accuracy/F1 lift 3–20 pts; pipeline
runtime cut 30–70%; dashboards/reports serving 10–500 stakeholders; queries
optimized 2–100×.

**Sales** — quota $500K–$5M; attainment 80–150%; pipeline 3–5× quota; win rate
15–35%; deal cycle 30–180 days; accounts 20–200.

**Customer Success / Support** — accounts 30–200; NPS 30–70; CSAT 3.5–4.8/5;
tickets 20–100/wk; first-response/resolution time cuts 20–60%; churn reduction
2–15 pts; retention 85–98%.

**Marketing** — traffic/leads lift 20–200%; conversion 1–10%; CAC cut 10–40%;
email open 15–35% / CTR 2–8%; campaign budget $10K–$1M; audience/followers growth
2–10×.

**Operations / Project / Product** — process time cut 20–60%; cost saved
$10K–$1M; on-time delivery 85–99%; team/stakeholders 5–50; features shipped
5–50/yr; adoption 20–80%.

**Finance / Accounting** — budget/portfolio $100K–$100M; close time cut 20–50%;
variance/error reduction 10–40%; audits/reports 10–200; cost savings identified
$50K–$5M.

**HR / Recruiting** — hires 20–500/yr; time-to-fill cut 20–50%; retention +5–20
pts; candidates screened 100–2,000; programs serving 50–5,000 employees.

**Education / Training** — students/trainees 10–500/yr; satisfaction 4.0–4.9/5;
completion 70–98%; curricula/courses 3–30; score improvement 10–40%.

> These ranges are directional industry norms, not the user's data. Their job is
> to make the *right* number easier to recall — nothing more.
