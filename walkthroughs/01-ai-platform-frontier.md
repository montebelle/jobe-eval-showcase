# Walkthrough 01 — AI Platform / LLMOps at a Frontier Lab

**Posting (anonymized):** Member of Technical Staff — Inference Platform
**Tier:** Tier-1 frontier lab
**Archetype detected:** AI Platform / LLMOps
**Overall score:** 82% (Strong Match)
**Ghost score:** 0.08 — High Confidence (fresh posting, posted 4 days, company has no layoff signals, hires-per-posting ratio 0.62)

---

## JD fingerprint (sanitized)

> We're looking for a Member of Technical Staff to own our LLM serving runtime. You'll build the Python-first backend stack behind our consumer assistant — FastAPI services, an OpenAI-compatible gateway, multi-tier model routing, a production caching layer, and the safety + telemetry enforcement that runs on every output. Comfort with non-deterministic system integration, AWS primitives (EC2 GPU, S3, Lambda), Redis, PostgreSQL, and ingestion pipelines expected. Bonus: vLLM / TRT-LLM experience, Rust willingness.

---

## Block A — Role Summary

**Detected archetype:** AI Platform / LLMOps
**Signals:** `LLM`, `platform`, `inference`, `serving runtime`, `gateway`, `model routing`, `caching`, `safety`, `telemetry`, `vLLM`, `TRT-LLM` — 11 archetype-defining keywords in the JD body, weighted density 0.91. Above the 0.7 threshold for unambiguous classification.
**Portfolio emphasis:** A1 (agents + embedding server), A5 (on-device inference), A9 (GCP pipelines — adjacent to AWS).

---

## Block B — Portfolio Match (3 parallel agents)

### Required skills (weight 3×)

| Requirement | Evidence | Adjacency | Score |
|---|---|---|---|
| Python-first backend, FastAPI | A1: production FastAPI embedding server at sub-200ms p95, OpenAI-compatible `/v1/embeddings` | Exact | 1.0 |
| OpenAI-compatible gateway | A1: local gateway routing 28 cron jobs across Sonnet 4.6 + Haiku 4.5 + Opus 4.6 with fallback | Exact | 1.0 |
| Multi-tier model routing | A1: 3-tier (primary/fanout/deepAudit) with concurrency control (max 8 Haiku sub-agents, serial Opus) | Exact | 1.0 |
| Caching — semantic + prefix | A1: two-layer cache (provider prefix + SQLite WAL-mode SHA-256-keyed semantic cache with LRU pruning) | Exact | 1.0 |
| Safety / telemetry enforcement | A1: four-hook safety plugin covering prompt-injection pre-filter, tool-call allowlist, deterministic-regex + LLM two-pass output review over 6 credential patterns, aggregate risk-scored delivery cancellation | Exact | 1.0 |
| Non-deterministic system integration | A1: 28-cron autonomous agent system with idempotency via PID O_EXCL locks + atomic write-rename | Exact | 1.0 |
| AWS EC2 GPU, S3, Lambda | A2/A9: prior ML pipelines on EC2 GPU, S3 feature stores, Lambda scoring | Exact | 1.0 |
| PostgreSQL / Redis | A12: PostgreSQL via Supabase; Redis pattern exposure, not production-scale | Strong | 0.7 |
| Ingestion pipelines | A9: append-only tri-bucket pattern (landing → archive → quarantine) with Cloud Functions triggered via Pub/Sub | Exact | 1.0 |

**Required-skill coverage:** 9/9 with avg weighted score 0.97 → **Gate 1 PASS** (required ≥ 50%).

### Preferred skills (weight 1×)

| Requirement | Evidence | Adjacency | Score |
|---|---|---|---|
| vLLM / TRT-LLM | A5: MLX + Ollama experience; vLLM read, not production | Weak | 0.4 |
| Rust | None | Gap | 0.0 |

**Mitigation:** Neither is gate-blocking. Acknowledge in cover letter with learning posture.

### Experience level (weight 2×)

- 8 years; 3+ years on production non-deterministic systems → **Gate 2 PASS** (required ≥ 0.7).

---

## Block C — Positioning (INTERNAL, not in final output)

**Fragility lens:** Claims backed by deep repos (28-cron autonomous platform, 3k-line embedding-plus-retrieval stack). Antifragile. Lead with.

**Inversion lens:** What would make them NOT hire?
- No vLLM / TRT-LLM production experience → pre-empt with on-device MLX work + learning posture
- No Rust → pre-empt with Go + C read comfort and willingness
- Smaller production scale than FAANG → lead with non-trivial idempotency + safety work that most FAANG candidates haven't done

**Barbell:** 70% safe (exact matches on gateway / routing / caching / safety) + 30% bold (the 4-layer injection defense + persona drift detector is uncommon at this tier).

**Emergence:** Career arc DS → manager → ML engineer → autonomous-agent builder reads as "owns research to deployment to ops."

---

## Block D — Compensation (summary)

Public signals suggest $350K–$450K base + equity at this tier for MTS-level backend work. Internal comp-research agent output not shown.

---

## Block E — Resume + Cover Letter

### Summary (generated)

> Senior ML engineer with 8 years building production backend systems for non-deterministic, LLM-driven workloads. Currently operating 28 scheduled LLM agent jobs with FastAPI services, a multi-tier OpenAI-compatible gateway, SQLite WAL-mode persistence, and a nomic-embed-text FastAPI embedding server powering hybrid vector-plus-BM25 retrieval at sub-200ms p95. Comfortable moving between Python service code, CUDA inference, on-device MLX, and the AWS primitives (EC2 GPU, S3, Lambda) that back them, with an applied math foundation for the statistical workloads the services carry.

### Lead bullets (tailored to this posting)

1. Operated 28 scheduled autonomous LLM agent jobs across 9 production services by building a Python service layer that coordinates multi-model routing through an OpenAI-compatible local gateway, fans out up to 8 concurrent workers to a smaller model, reserves the largest model for weekly deep audits, and falls back to a secondary provider on outage, cutting per-query inference cost 40% while keeping tail latency bounded.
2. Shipped a FastAPI embedding server running nomic-ai/nomic-embed-text-v1.5 behind an OpenAI-compatible `/v1/embeddings` endpoint that accepts float and base64 encoding with L2 normalization applied server-side, powering a hybrid retrieval service blending 65% vector similarity plus 35% BM25 with MMR re-ranking (lambda 0.7) over a 20,000-entry LanceDB store at sub-200ms p95.
3. Eliminated prompt injection, SSRF, and credential leakage across the 28 agent jobs by building a four-hook safety enforcement plugin covering pre-inference pattern matching, tool-call allowlist validation, a two-pass deterministic plus LLM output review over API key, Bearer token, AWS secret, E.164 phone, email, and UUID patterns, and aggregate risk-scored delivery cancellation.

### Cover letter (P1 excerpt)

> The cheapest way to serve an LLM backend reliably is to stop pretending every query deserves the same model. The platform I run today routes a long tail of routine tasks to a smaller model fanning out to 8 concurrent workers, sends complex reasoning to a mid-tier model, and reserves the largest model for weekly deep audits, with automatic fallback to a secondary provider on outage. Uniform routing to the largest model would have been simpler and roughly five times more expensive; a cheap cache alone would have hidden the fact that most queries never needed the big model at all.

ATS normalization pass via `lib/normalize.js`: 14 em-dashes, 8 smart quotes, 2 non-ASCII characters stripped. 527 words (inside 475–600 target).

---

## Block F — Story Mapping

| JD requirement | STAR+R story | Match |
|---|---|---|
| Multi-tier model routing | "Building the multi-model routing plane" | Strong |
| Safety enforcement | "Building the output gate" | Strong |
| Caching at scale | "Two-layer cache under 28 crons" | Strong |
| Ingestion pipeline | "Append-only tri-bucket on GCP" | Strong |
| Rust | "First Rust module for log parsing" | Partial — learning, not shipped |
| vLLM / TRT-LLM | None | None — acknowledge |

---

## Block G — Legitimacy (ghost score 0.08)

| Signal | Value | Contribution |
|---|---|---|
| Age (days) | 4 | 0.00 (below threshold 45d for senior-staff; full credit) |
| Repost cadence | 1 prior in 6 months | 0.00 |
| Hires-per-posting ratio | 0.62 | 0.00 (above 0.5 baseline) |
| Layoff proximity | None in 180d | 0.00 |
| Title-fuzz generic pattern | Specific MTS title | 0.08 |

**Label:** High Confidence. Proceed with application.

---

## Final output

Resume DOCX (527 words, Calibri single-column), cover letter DOCX (312 words, 3 paragraphs), both ATS-normalized, written to `reports/{company-slug}/`. Added to `apply-queue.json` with score 82 and ghost confidence High.
