# Walkthrough 03 — Agentic Platform at a Growth-Stage Startup (Ghost Flag)

**Posting (anonymized):** AI Engineer — Agent Automation
**Tier:** Series-C startup, "AI-native workflow automation"
**Archetype detected:** Agentic / Automation
**Overall score:** 74% (Good Match)
**Ghost score:** 0.52 — **Proceed with Caution**

---

## JD fingerprint

> AI Engineer to join our core agent team. Build and maintain production agent workflows, extend our orchestration framework, deploy new integrations. Python strongly preferred. Experience with LangChain / LangGraph / agent frameworks required. Scaled agent production systems a plus.

---

## Block A — Role Summary

**Detected archetype:** Agentic / Automation
**Signals:** `agent` (5), `automation`, `orchestration`, `LangChain`, `LangGraph`, `workflows` (2), `integrations`.
**Portfolio emphasis:** A1 (autonomous operations platform, safety, competitive intelligence system), A5 (on-device meeting assistant).

---

## Block B — Portfolio Match

### Required skills (weight 3×)

| Requirement | Evidence | Adjacency | Score |
|---|---|---|---|
| Production agent systems | A1: 28-cron autonomous platform with 4-layer injection defense, persona-drift detection, idempotency via PID O_EXCL locks | Exact | 1.0 |
| Orchestration framework | A1: local multi-model gateway routing to a primary / fanout / deep-audit tier with `maxConcurrent: 8` sub-agent fanout + context pruning `cache-ttl` mode 6h | Exact | 1.0 |
| Deploy integrations | A1: integrations with SerpAPI, Brave, Apollo, Hunter, HubSpot, Gmail SMTP, Resend, Meta Graph, LinkedIn, Cal.com, Replicate, fal.ai, ElevenLabs, Cloudinary | Exact | 1.0 |
| Python | A1, A2, all backend code | Exact | 1.0 |
| LangChain / LangGraph | None — used a custom gateway | Gap | 0.0 |

### Preferred skills (weight 1×)

| Requirement | Evidence | Score |
|---|---|---|
| Scaled agent production | A1: 28 jobs, 9 production services, survived power-loss + partial failures | Exact | 1.0 |

**Weighted score:** 0.74. **Gate 1:** PASS.

---

## Block C — Positioning

**LangChain gap:** The obvious objection is "you haven't used the frameworks we use." Jobe's response: the value a candidate brings is the ability to *build* that kind of framework — PID O_EXCL locking, atomic write-rename idempotency, 4-layer injection defense, persona-drift detection via EMA over embeddings are the non-obvious invariants a competent LangChain operator will want anyway.

**Inversion:** They will default to candidates who can pick up the codebase tomorrow. Pre-empt: a LangChain tutorial is a 3-day project; the pattern knowledge transfers immediately. The unusual thing I have is production experience at cron scale with human approval gates — the actual hard part.

**Barbell:** 70% safe (agent systems, orchestration, Python at production scale). 30% bold (the safety + persona-drift + idempotency work, which LangChain does not ship by default).

---

## Block D — Compensation

Series-C startup signals $180K–$240K base + equity. Flexibility on comp; upside on equity.

---

## Block E — Resume + Cover Letter

### Lead bullets

1. Operated 28 scheduled autonomous agent jobs across 9 production services by building a Python service layer that coordinates multi-model routing through a local OpenAI-compatible gateway, fans out up to 8 concurrent workers to a smaller model, and cuts per-query inference cost 40% while keeping tail latency bounded.
2. Built a four-hook safety enforcement plugin covering prompt-injection pre-filter, tool-call allowlist validation, a two-pass deterministic-regex-plus-LLM output review over API key, Bearer token, AWS secret, E.164 phone, email, and UUID patterns, and aggregate risk-scored delivery cancellation — zero credential exposure incidents across 28 production pipelines.
3. Guaranteed idempotent execution across the 28 crons by engineering PID-based O_EXCL file locks, atomic write-rename on all state files, a 3,000-entry rolling dedup cache for Reddit IDs, and a 7-day URL-plus-title dedup window for intel signals — preventing double-execution during overlapping cron fires and partial failures.

### Cover letter (P1)

> The non-obvious work in agent systems is not the agents; it's the invariants around them. PID `O_EXCL` locks make overlapping cron fires safe. Atomic write-rename means a reader never sees a half-written state file. A 4-layer output gate — cheap deterministic regex first, LLM auditor only on the 5% that survive — catches credential leaks without blowing out the cost budget. A safety gate too expensive to run on every output is a safety gate that gets turned off. Most agent-framework posts skip this layer entirely; I wrote a 28-cron platform where it's load-bearing.

### Cover letter (P2 — honesty on LangChain)

> I have not shipped on LangChain specifically — my production agent system runs on a different gateway I co-designed. The orchestration patterns (tool-call allowlists, sub-agent fanout with bounded concurrency, deterministic pipeline with LLM reasoning *inside* stages per MAST 2025) transfer directly. LangChain idioms I can pick up in a week; the invariants are the reason to hire.

---

## Block F — Story Mapping

| JD requirement | STAR+R story | Match |
|---|---|---|
| Production agent systems | "28-cron autonomous platform" | Strong |
| Orchestration framework | "Local multi-model gateway + tiered routing" | Strong |
| Safety / output review | "Building the output gate" | Strong |
| LangChain | None | None — acknowledge, plan to pick up |
| Deploy integrations | "12-integration outreach pipeline" | Strong |

---

## Block G — Legitimacy (ghost score 0.52 — the warning)

| Signal | Value | Contribution | Max-pool? |
|---|---|---|---|
| Age (days) | 68 | 0.62 | ← max |
| Repost cadence | 4 prior in 12 months | 0.55 | |
| Hires-per-posting ratio | 0.28 | 0.55 | |
| Layoff proximity | 67 days (1 round) | 0.50 | |
| Title-fuzz generic pattern | Specific | 0.00 | |

**Max signal:** age (0.62) → overall ghost score = 0.52 (decayed from max by max-pool + smoothing).

**Label:** **Proceed with Caution**.

**Reasoning surfaced to user:**
- Posting age 68 days is above the 45-day threshold for senior/staff roles.
- Company has reposted this specific role 4 times in the last 12 months.
- Hires-per-posting ratio of 0.28 is below the 0.5 Revelio Labs baseline — suggests they're posting more than they're filling.
- There was a layoff round ~67 days ago.

Individually none is damning; collectively the pattern is consistent with a "talent pool" posting rather than an active hire. Jobe surfaces this and lets the user decide. Per the skill contract, the candidate can still apply — but is informed.

---

## Outcome reasoning

The candidate chose to apply but with lower priority in the apply queue (position 14 rather than top 5). Cover letter acknowledged the LangChain gap and emphasized the invariants. Result tracked in `tracker.md` for downstream analytics via `/jobe patterns`.

---

## What this walkthrough shows about jobe

- **Block G is load-bearing.** Without ghost-job detection, this posting scored 74% and would have ranked near the top of the queue. The multi-signal ghost score surfaces a pattern no single signal would have caught.
- **Max-pool (not sum) over signals** means a strong individual signal — age alone at 0.62 — is enough to flag, even though two other signals are below their red-line thresholds.
- **The candidate still gets to decide.** Jobe does not auto-reject; it surfaces the signal + reasoning and lets the human choose. This is the anti-paternalism contract in the skill.
