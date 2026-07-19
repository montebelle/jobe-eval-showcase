# Jobe — Evaluation Showcase

**Real end-to-end output from [Jobe](https://github.com/montebelle/jobe-skill), a career-intelligence skill for Claude Code.** Jobe runs a discover → evaluate → apply → track pipeline over ML / AI / DS postings. This repo shows what it actually produces, so you can judge the tool from its output rather than its description.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Source](https://img.shields.io/badge/source-jobe--skill-orange)](https://github.com/montebelle/jobe-skill)

This repo is a **showcase**, not source code. Each walkthrough shows what jobe produces when run against a single job posting: the A–G block decomposition, the ghost-score breakdown, and a before/after tailoring pass. If you're evaluating jobe and want to see real output, read one of these. If you want the code, see [jobe](https://github.com/montebelle/jobe-skill).

---

## What you're looking at

Each walkthrough is one markdown file under `walkthroughs/`. Every one goes through the same seven blocks:

| Block | What's shown |
|---|---|
| **A: Role Summary** | Detected archetype + JD fingerprint |
| **B: Portfolio Match** | 3 parallel agents score every requirement against `reference.md` evidence |
| **C: Positioning** | Gate-pass check + differentiation strategy (internal reasoning, not shown in final output) |
| **D: Compensation** | Market research, not shown here |
| **E: Resume + Cover Letter** | ATS-normalized DOCX with XYZ-formula bullets |
| **F: Story Mapping** | STAR+R stories mapped to JD requirements |
| **G: Legitimacy** | Multi-signal ghost-job detection |

---

## Walkthroughs

| File | Archetype | Tier | What it demonstrates |
|---|---|---|---|
| [`01-ai-platform-frontier.md`](walkthroughs/01-ai-platform-frontier.md) | AI Platform / LLMOps | Tier-1 frontier lab | Strong match path. Block E shows how portfolio agent-systems experience re-frames as inference-platform contribution. |
| [`02-applied-ml-quant.md`](walkthroughs/02-applied-ml-quant.md) | Applied ML | Quant / finance | Stretch-match path. Gate-pass borderline; shows how jobe surfaces adjacent evidence and where the cover letter acknowledges the gap. |
| [`03-agentic-growth-startup.md`](walkthroughs/03-agentic-growth-startup.md) | Agentic / Automation | Series-C startup | Ghost-score surfaces a repost-cadence warning. Shows Block G producing a "Proceed with Caution" label. |

---

## On the data

The JDs used in these walkthroughs are anonymized versions of real public postings. Company identifiers, specific compensation bands, and any posting-specific fingerprints are replaced with generic stand-ins so the **tool's behavior** is the thing visible, not any specific application of mine.

The candidate profile referenced in these walkthroughs is also a template — it uses the same domain structure (A1–A12) that jobe's [`portfolio.js`](https://github.com/montebelle/jobe-skill/blob/main/lib/portfolio.js) keyword index uses, but the evidence is generic. Real use of jobe requires populating `reference.md` and `modes/_profile.md` with your own details.

## License

MIT — see [`LICENSE`](LICENSE). Walkthrough content is authored; feel free to adapt the format for your own tool documentation.
