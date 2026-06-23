# Walkthrough 02 — Applied ML at a Quant Fund (Stretch Match)

**Posting (anonymized):** Senior Machine Learning Researcher — Systematic Strategies
**Tier:** Quant hedge fund
**Archetype detected:** Applied ML / Causal
**Overall score:** 61% (Stretch Match)
**Ghost score:** 0.18 — High Confidence

---

## JD fingerprint

> Senior ML Researcher to develop systematic trading strategies. Deep time-series experience, causal inference background, rigorous statistical methodology required. Experience with panel data, cross-fitted estimators, and proper hold-out design expected. PhD preferred but not required for exceptional candidates. Production Python, q/kdb+ exposure a plus.

---

## Block A — Role Summary

**Detected archetype:** Applied ML / Causal (dual)
**Signals:** `time-series` (2), `causal inference` (3), `panel data` (1), `cross-fitted estimators` (1), `hold-out design` (1), `rigorous statistical` (2).
**Portfolio emphasis:** A2 (forecasting), A3 (survival / propensity), A4 (GeoLift / SDID), A8 (change point). PhD signal weak — pre-empt with statistical-sophistication evidence.

---

## Block B — Portfolio Match

### Required skills (weight 3×)

| Requirement | Evidence | Adjacency | Score |
|---|---|---|---|
| Time-series with rigor | A2: 13-model ensemble (SARIMAX, Holt-Winters, Panel RF/XGB/SVM + macro-enriched variants) with TimeSeriesSplit k=3–5, `DEFAULT_CV_GAP` to prevent leakage, Duan smearing bias correction (1983) replacing Jensen's inequality, moving block bootstrap for realistic error autocorrelation | Exact | 1.0 |
| Causal inference with cross-fitting | A3: PropensityScoreAnalysis with cross-fitted propensity scores (5-fold), IPW, PSM (0.1 caliper), AIPW / Doubly Robust, Rosenbaum sensitivity bounds, Crump trimming [0.01, 0.99] | Exact | 1.0 |
| Panel data | A2: 921 panels with lag features [1,3,6,12,24], OOB R² quality assessment, tier-specific Duan smearing from OOB residuals, Winsorized at 5% | Exact | 1.0 |
| Proper hold-out design | A2: TimeSeriesSplit with `DEFAULT_CV_GAP` flagged for lag-6/12 insufficiency, A3: balance check SMD < 0.1 post-matching, minimum matched pairs ≥ 100 | Exact | 1.0 |
| PhD in quantitative field | BS Applied Mathematics | Gap | 0.0 |
| Production Python | A1, A2, all modules are production Python | Exact | 1.0 |

**Required-skill coverage:** 5/6 exact, 1 gap on PhD. Weighted score 0.83.
**Gate 1:** PASS (required ≥ 50%).
**Gate 2 Experience:** Quant-domain experience is weak — consumer packaged goods, not markets. Adjacent. Score 0.6 → **borderline FAIL** (threshold 0.7). Pre-empts needed.

### Preferred skills (weight 1×)

| Requirement | Evidence | Adjacency | Score |
|---|---|---|---|
| q / kdb+ | None | Gap | 0.0 |
| Academic publication | None | Gap | 0.0 |

---

## Block C — Positioning

**Inversion:** What makes them NOT hire?
- No PhD — pre-empt by leading with depth of statistical methodology. The Duan-smearing-vs-Jensen's-inequality decision, the Crump-trimming choice, the 5-gate GeoLift framework — these are PhD-level reasoning in a non-PhD resume.
- No market domain experience — acknowledge directly. Frame CPG forecasting and causal incrementality as transferable: both measure treatment effects in noisy, censored data with selection bias.
- No kdb+ — trivial skill to pick up; mention willingness.

**Asymmetry:** Most applicants lead with credential (PhD from X). An uncredentialed applicant can lead with *methodology depth* — show you've made the non-obvious statistical choices — and win on signal. Example: naming Duan smearing explicitly (not "bias correction") is unusual in non-academic resumes.

**Barbell:** 70% safe (time-series + causal methodology matches). 30% bold (the GeoLift 5-gate framework, the 33.6M-user discrete-time cloglog survival model with C-index 0.97 — uncommon at this scale).

---

## Block D — Compensation

Public signals suggest $300K–$500K base + 2× bonus at senior researcher tier. Lower than frontier labs' total comp but high cash.

---

## Block E — Resume + Cover Letter

### Lead bullets (tailored)

1. Drove measurable incrementality across 33.6M users and 7.3M conversions by building a discrete-time complementary-log-log GLM with L2-regularized period dummies, Kaplan-Meier with Greenwood variance (log-space for scale), Nelson-Aalen cumulative hazard, stratified hazard models, and a PropensityScoreAnalysis class with cross-fitted scores (5-fold), IPW, PSM at 0.1 caliper, AIPW doubly-robust estimation, and Rosenbaum sensitivity bounds — concordance index 0.97.
2. Replaced Jensen's inequality with horizon-specific Duan smearing (Duan 1983) across 700+ forecast paths on log-scale series, computing smearing factors from expanding-window backtest residuals for time-series models and tier-specific OOB residuals for panel ML, Winsorized at 5% and capped at factor 5.0 for heteroscedasticity robustness.
3. Designed a 5-gate synthetic-control framework (effective donors N_eff ≥ 3, top single donor ≤ 25%, donor-to-treatment volume ratio ≥ 1.5×, in-time placebo |abs_lift_in_zero| ≤ 2%, AvgScaledL2Imbalance ≤ 0.25) run over 11 lookback windows with MultiCellMarketSelection and power aggregation, surfacing operational MDE 7.5% at 80% power.

### Cover letter (P1)

> Most incrementality studies fail silently — they produce a number but nobody checks whether the synthetic control is actually valid. The framework I work in makes validity a binary decision before results are even computed: effective donors ≥ 3, top single donor weight ≤ 25%, donor-to-treatment volume ratio ≥ 1.5×, in-time placebo magnitude ≤ 2%, pre-fit L2 imbalance ≤ 0.25. If any gate fails, the study is rejected before it can mislead anyone. Lead with discipline; report second.

### Cover letter (P2 excerpt)

> On the PhD question: I did not pursue one. The statistical apparatus I've shipped in production is my answer — Duan smearing (1983) replacing Jensen's inequality for log-scale bias correction, cross-fitted doubly-robust estimation with Rosenbaum sensitivity analysis, Benjamini-Yekutieli FDR correction for macro-feature selection, Sequential Monte Carlo with PMCMC for Bayesian uncertainty quantification. The methodological choices have been mine; the depth is there. I'd like the chance to take them into a markets context.

---

## Block F — Story Mapping

| JD requirement | STAR+R story | Match |
|---|---|---|
| Time-series rigor | "13-Model Forecasting System" | Strong |
| Causal inference at scale | "33.6M User Survival Analysis" | Strong |
| Panel data methods | "Panel ML with tier-specific Duan smearing" | Strong |
| Quant trading experience | None | None — acknowledge as domain gap |
| PhD | None | None — pre-empt with methodological depth |

---

## Block G — Legitimacy (ghost score 0.18)

| Signal | Value | Contribution |
|---|---|---|
| Age (days) | 22 | 0.00 (below senior-adjusted threshold of 45) |
| Repost cadence | 2 prior in 12 months | 0.15 |
| Hires-per-posting ratio | 0.48 | 0.03 (just below 0.5 baseline) |
| Layoff proximity | None | 0.00 |
| Title-fuzz generic pattern | Specific + senior | 0.00 |

**Label:** High Confidence. Proceed.

---

## Outcome reasoning

Borderline match because of the PhD gap + domain mismatch. jobe flags this to the user with "Stretch Match — recommend applying if time allows, lead with methodological depth, acknowledge domain transition honestly." Cover letter does not hide the gaps; it pre-empts them.
