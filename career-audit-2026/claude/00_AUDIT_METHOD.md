# Claude Independent Audit — Method & Evidence Notes

**Date:** 2026-09-04
**Branch:** `career-audit-2026`
**Auditor:** Claude (independent first pass — ChatGPT's audit not read, per `../00_CONTEXT.md` §Independent-review rule)

---

## 1. What was inspected

| Source | Access | Notes |
|---|---|---|
| `index.html` (inherited from `main`) | Full, read-only | Single-file site, 611,581 bytes, 942 lines. Primary evidence. |
| Live site `https://mabz-miguel.github.io/` | Fetched read-only | Renders and matches source. Used to confirm published behaviour. |
| Embedded CV (base64 PDF inside `index.html`, ~88 KB) | Extracted and decoded | The PDF ships text via an **embedded subset font with a substitution encoding**. Letters were recovered by frequency/crib analysis (high confidence). Some digits — notably percentage figures and a few certification years — render through a second subset font and are recovered with **medium confidence** only. Flagged inline wherever it matters. |
| Public LinkedIn `https://www.linkedin.com/in/miguelballesteroszafra` | **Blocked** — HTTP 999 (LinkedIn anti-bot) | Confirms the limitation anticipated in `00_CONTEXT.md` §"LinkedIn limitation". No LinkedIn PDF export or screenshots exist anywhere in the repo. See `05_LINKEDIN_AUDIT.md`. |
| `career-audit-2026/chatgpt/**` | **Not opened** | Per instructions. |

## 2. Deliverable numbering — reconciliation

`claude/README.md` and `CLAUDE_MASTER_PROMPT.md` specify overlapping-but-not-identical file lists (README ends at `05_LINKEDIN_AUDIT.md`; the master prompt has `05_TECHNICAL_AUDIT.md` + `06_PRIORITY_MATRIX.md` and folds LinkedIn into positioning/consistency). `00_CONTEXT.md` keeps LinkedIn in explicit scope. This audit produces the **union**, renumbered so nothing collides:

| File | Source of requirement |
|---|---|
| `01_POSITIONING_AUDIT.md` | both |
| `02_PORTFOLIO_CONTENT_AUDIT.md` | both |
| `03_UX_UI_AUDIT.md` | both |
| `04_CV_AUDIT.md` | both |
| `05_LINKEDIN_AUDIT.md` | `README.md` + `00_CONTEXT.md` scope |
| `06_TECHNICAL_AUDIT.md` | `CLAUDE_MASTER_PROMPT.md` (its "05") |
| `07_PRIORITY_MATRIX.md` | `CLAUDE_MASTER_PROMPT.md` (its "06") |

## 3. Evidence conventions

Each finding is tagged:

- **[OBSERVED]** — directly visible copy, DOM, or implementation fact.
- **[INFERENCE]** — a reasoned conclusion from observed evidence.
- **[UNCERTAIN]** — cannot be resolved from available evidence; listed as an open question.
- **[RECOMMENDATION]** — direction only. No final copy, design, or code is proposed in this phase.

Confidence (high / medium / low) is stated on every summary judgement.

## 4. Scope boundary respected

No production file was modified. No CV change, no copy rewrite, no redesign, no refactor. Only documents under `career-audit-2026/claude/` were created.
