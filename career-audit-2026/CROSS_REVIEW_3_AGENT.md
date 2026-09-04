# CROSS REVIEW — ChatGPT + Claude + Codex

Date: 2026-09-04

Independent first-pass sources:
- ChatGPT: `career-audit-2026/chatgpt/01–06`
- Claude commit: `e3b7b2dbf91afb0011998576ceaf223124e81173`
- Codex commit: `4193dcabfc1fb5cc400ead32adf14d26b08749c6`

No production changes are approved by this document.

---

# 1. Executive synthesis

The three independent reviews converge strongly on the same central diagnosis:

> The portfolio does not have a quality-of-work problem first. It has a **classification + proof problem**.

Miguel's actual evidence is broad and differentiated: GenAI adoption, process/workflow redesign, discovery and workshops, MVPs/internal systems, digital production depth, direct client ownership in his studio period, cross-functional coordination and training. But the current site makes recruiters perform too much interpretation before they can decide what role he belongs to.

The correct response is **not a full visual redesign**. The current design language is coherent enough to preserve. The first intervention should be:

1. choose a market-recognisable primary role family;
2. rewrite hierarchy around role + ownership + outcomes;
3. make the strongest proof scannable;
4. replace the stale/embedded CV with a clean current source-of-truth PDF;
5. fix the confirmed accessibility, font, social-preview and performance defects;
6. only then refine visual polish.

---

# 2. The strongest convergence

## A. The current category is not recruiter-searchable

**ChatGPT:** `AI-Driven Digital Production Systems` sounds sophisticated but creates classification friction.

**Claude:** calls it a coined category that maps to no job-board title, ATS filter or seniority band.

**Market benchmark:** current vacancies use titles such as `AI Adoption & Transformation Lead`, `AI Transformation Manager`, `Digital Transformation Project Manager`, `Product Operations Manager` and `GenAI Enablement Lead`.

**Verdict: AGREED / P0.**

The phrase can survive as a supporting proposition, but it should not be the primary professional title.

---

## B. Leadership/ownership proof is underweighted

**ChatGPT:** leadership, decisions and business impact are less visible than systems/technical sophistication.

**Claude:** the project verbs are dominated by `designed`, `defined`, `contributed`, `shaped`, `supported`; the strongest ownership evidence is scattered.

**Market benchmark:** manager/lead vacancies repeatedly ask for roadmap ownership, cross-functional programs, prioritization, adoption, governance, success metrics and stakeholder influence.

**Verdict: AGREED / P0.**

Every selected case should state, explicitly:
- problem;
- Miguel's role;
- what he owned/decided;
- stakeholders/team scale;
- what changed;
- evidence/metric;
- relevance to the target role.

---

## C. Generic Product Manager is not the strongest immediate target

**ChatGPT:** product thinking is real, but formal PM history and product lifecycle metrics are limited.

**Claude:** Product Management is a weak current evidence match; `Product Operations` is more defensible.

**Market:** current Product Ops roles value workflow governance, content operations, AI-assisted processes, quality and stakeholder coordination — areas that map directly to Miguel's QA/estimation/operations work.

**Verdict: AGREED.**

Use product thinking as a differentiator. Do not make `Product Manager` the main identity today.

---

## D. `AI Systems Lead` is the wrong signal

**ChatGPT:** risks pushing the profile into engineering/architecture expectations.

**Claude:** explicitly flags the contradiction with `Python (basic, in progress)` and weak ML-engineering evidence.

**Codex:** confirms the portfolio is technically simple frontend work, not evidence of AI/ML systems engineering leadership.

**Verdict: AGREED.**

Drop `AI Systems Lead` as a target label.

---

## E. The visual hierarchy is recruitment-suboptimal, but the aesthetic should be preserved

**ChatGPT:** the hero name is enormous while the role is tiny; hierarchy privileges identity over employability.

**Claude:** reaches the same conclusion and says the page visually reads closer to senior creative IC / boutique studio than transformation operator.

**Codex:** confirms the CSS values and additionally discovers that the intended display font (`Clash Display`) is not actually being served.

**Verdict: AGREED.**

Do not rebuild from zero. Preserve the dark, premium visual system, but rebalance approximately 20–30% of the hierarchy toward:
- role;
- current level/employer;
- outcome proof;
- ownership;
- recruiter CTA.

---

# 3. Recommended primary positioning after market validation

The market review changes the initial hypotheses in a useful way.

## Recommended primary spine

### **AI Adoption & Digital Transformation Manager**

Supporting proposition:

> GenAI Enablement · Operational Transformation · Workflow & Process Design · Cross-functional Delivery

Why this is the best synthesis:

- **AI Adoption / GenAI Enablement** is the axis Claude found best supported by evidence.
- **Digital Transformation** is a much more common external recruiting category than the invented portfolio phrase.
- **Manager** is more defensible than `Head of` or enterprise `AI Strategy Lead` given the current proof.
- It preserves the real differentiator: Miguel understands production/creative/technical workflows deeply enough to transform them, rather than approaching AI only from theory.

## Strong adjacent role families

1. **GenAI Enablement Lead / AI Enablement Manager**
2. **Digital Transformation Project Manager**
3. **AI Adoption & Transformation Lead** — stretch where enterprise scale is required
4. **Product Operations Manager** — especially content/digital/AI-enabled operations
5. **Innovation Project / Program Manager**

## Stretch roles, not default positioning

- enterprise AI Transformation Manager / AI Strategy Manager;
- Technical Program Manager at senior engineering-program scale;
- Transformation Program Manager with large-budget / multi-country governance;
- Head of AI / Head of Transformation / Director roles.

## Avoid as primary title

- Generic Product Manager
- AI Systems Lead
- IT Transformation Manager
- Head of Digital Production as the main external identity unless stronger people/budget/department ownership is proven

---

# 4. Important market evidence

## Santander — AI Adoption & Transformation Lead, Boadilla del Monte

This is the most strategically useful live benchmark found.

It asks for:
- AI adoption strategy and roadmap;
- process discovery and AI opportunity assessment;
- cross-functional Business / IT / Operations coordination;
- success metrics and implementation milestones;
- communication, training and AI literacy;
- AI-assisted productivity/automation tooling;
- project/program management;
- stakeholder influence.

It requires **English B2**, not C1, and treats a university degree as preferred rather than strictly mandatory.

This is important because it shows that English C1 and a STEM degree are **not universal blockers** for the whole role family. They are blockers for some vacancies (for example KPMG), not all.

Main gaps versus this exact Santander archetype:
- 5+ years of clearly evidenced large-scale transformation leadership;
- cross-country / multi-entity program ownership;
- executive governance forums / steering committees;
- formal adoption dashboards / Power BI;
- organizational change management;
- banking domain.

The role family is highly relevant even if this specific senior vacancy may be a stretch today.

## GenAI Enablement Lead market archetype

Current roles explicitly ask for people who:
- listen to teams and diagnose workflow pain;
- translate needs into AI use cases;
- run training/workshops;
- build practical resources;
- test tools hands-on;
- scale what works;
- combine strategic thinking with implementation.

This maps unusually well to Miguel's strongest real evidence.

---

# 5. CV — major cross-review finding: there are two versions

This is one of the most important discoveries from combining the reviews.

## Claude audited the CV embedded inside `index.html`

That embedded PDF appears older and has problematic font encoding during extraction. Claude reconstructed figures such as approximately 30/40/40 and a team scope of up to 50 people, but explicitly marked parts of that extraction as uncertain.

## ChatGPT independently retrieved a newer saved CV

The newer `Miguel_Angel_Ballesteros_CV_EN.pdf` is a two-page, cleanly parsed document and states:
- `AI & Digital Transformation Lead`;
- `Accenture Marketing Operations — Assistant Manager | GenAI Adoption & Digital Innovation`;
- 25% operational-cost reduction;
- 40% faster time-to-market;
- productivity increases up to 40%;
- coordinated multidisciplinary teams up to 10 people.

## Decision

**Do not propagate Claude's reconstructed `50 people` or `≈30%` claims automatically.** They may belong to an older CV and need factual verification.

The production portfolio is currently serving an **older/stale CV version**. This must be fixed before launch of the revised career package.

Recommended future implementation:
- choose one current CV source of truth;
- export it with normal Unicode/selectable text;
- run text extraction / ATS parsing test;
- store it as a real file, e.g. `assets/Miguel_Angel_Ballesteros_CV_EN.pdf`;
- link to it rather than embedding it as Base64;
- keep the portfolio, LinkedIn and CV title/metrics synchronized.

---

# 6. LinkedIn — cross-review correction

Claude could not access LinkedIn and correctly documented that limitation.

ChatGPT later obtained current public-indexed data. Confirmed public signals include:
- current employer: Accenture España;
- public About begins with `Lidero iniciativas de transformación digital y de IA...`;
- recent activity includes AI/3D/VFX exploration and the Paid Media workshop;
- ESIC Product Management and Google Project Management credentials are public;
- English is listed using LinkedIn's broad professional-proficiency label.

Therefore Claude's hypothesis that the LinkedIn About probably repeats the portfolio's coined phrase is **not supported**. The About is already directionally more concrete.

The remaining LinkedIn risks are:
- exact headline still not verified;
- Experience wording/order not fully retrievable;
- Featured section unknown;
- top Skills unknown;
- Recommendations need direct inspection;
- current activity can still make the profile look split between 3D/creative technology and transformation unless Featured/content is curated.

A LinkedIn PDF export or screenshots are still required before rewriting it.

---

# 7. Technical audit — Codex adds important objective findings

## P0 accessibility

Capabilities are click-only `div` elements. Keyboard users cannot operate most of them.

**Decision:** must be corrected before considering the site technically finished.

## P1 semantic interaction

Projects simulate buttons with `div` + script-added focus but lack proper disclosure semantics (`button`, `aria-expanded`, `aria-controls`, hidden state).

Mobile navigation is visually hidden when closed but its links remain in the keyboard tab order.

**Decision:** convert to native semantic controls and manage focus/state correctly.

## P1 intended font is not loading

Both Claude and Codex independently found that `Clash Display` is requested from Google Fonts but Google does not serve it. The site falls back to generic sans-serif for its most important display typography.

**Decision:** fix. This is a real design-quality defect, not a stylistic opinion.

## P1 social preview is broken

`og:image` points to `mabz.miguel.com`, which does not resolve.

**Decision:** fix before actively sharing the portfolio.

## P1 distribution/performance

Codex measured:
- ~612 KB single HTML;
- 27 embedded `data:` resources;
- ~412 KB decoded binary inside the document;
- 26 images;
- zero lazy-loaded images;
- embedded CV.

**Decision:** externalize images/CV and allow independent caching/lazy loading. Do not overengineer into a SPA; a simple static site is still appropriate.

## Progressive enhancement

Without JavaScript, most project/capability detail is visually inaccessible.

**Decision:** content should remain readable without JS and interactivity should enhance rather than gate it.

---

# 8. One disagreement resolved by cross-review

## Colour contrast

Claude estimated `--muted #6b7f91` on the main black background at about 4.6:1 and treated it broadly as an AA failure.

Codex calculated the exact solid-colour ratios:
- on `#030507`: **4.93:1** — passes AA normal text;
- on `#07090d`: **4.81:1** — passes;
- on `#111820`: **4.31:1** — fails AA normal text.

**Decision:** Codex's measured result wins. Do not globally label the muted token inaccessible. Fix the specific usages on lighter surfaces and visually validate tiny/opacified text.

This is a good example of why independent review improves the result: Claude detected the area of risk; Codex measured it more precisely.

---

# 9. Another disagreement / nuance resolved

## How senior should the external positioning sound?

Claude was stricter, reading the current site as `mid-to-upper IC / emerging lead` and warning strongly against Head-of claims.

ChatGPT's market review sees credible manager-level evidence in:
- formal Assistant Manager level;
- studio-founder/client ownership;
- cross-functional coordination;
- workshops/discovery;
- AI adoption initiatives;
- training/capability building;
- measurable operational improvements.

**Resolution:**

- `Head of / Director` should not be the default positioning now.
- `Manager` is defensible.
- `Lead` is defensible when it describes a workstream/domain (`GenAI Enablement Lead`, `AI Adoption Lead`) rather than implying large department ownership.
- The portfolio must clearly distinguish **coordinated**, **led**, **managed**, **owned** and **contributed** instead of treating them as interchangeable.

---

# 10. What should change first — consolidated P0/P1 sequence

## Phase 1 — Strategy / content

1. Lock the primary role family: proposed **AI Adoption & Digital Transformation Manager**.
2. Remove `AI Systems Lead` and de-emphasize Head-of claims.
3. Rewrite hero around recognised role + current context + specific value proposition.
4. Bring CV access into the first viewport/navigation.
5. Select only the 3–4 cases that best prove the target role.
6. Rewrite each selected case around ownership + measurable/scoped evidence.
7. Replace vague stats (`5+ industries transformed`, `10+ systems delivered`) unless fully defensible.
8. Contextualize or reduce the logo wall.
9. Preserve the visual identity; do not redesign from scratch.

## Phase 2 — CV / LinkedIn consistency

10. Establish one current CV source of truth and replace the stale embedded version.
11. Test PDF parsing/ATS extraction.
12. Align professional title, metrics, role wording and dates across CV/portfolio/LinkedIn.
13. Complete LinkedIn audit from export/screenshots.
14. Curate Featured/Skills/Recommendations around the target identity.

## Phase 3 — Technical quality

15. Fix semantic accordions and keyboard accessibility.
16. Fix mobile-menu focus/hidden state.
17. Add focus-visible styles and proper reduced-motion behavior.
18. Fix the display font.
19. Fix `og:image`, canonical/social metadata and favicon.
20. Externalize images/PDF; lazy-load lower content.
21. Add a small automated quality gate (HTML + axe + keyboard + responsive + links + Lighthouse baseline).

---

# 11. What should NOT change yet

- Do not rewrite production before the positioning decision is approved.
- Do not let Claude or Codex independently replace another agent's work.
- Do not rebuild the portfolio in a framework merely because the single HTML is large.
- Do not invent management metrics.
- Do not hide the 3D/XR/creative-production history; subordinate it to the transformation story.
- Do not claim C1 English before it is true.
- Do not treat lack of C1 or STEM degree as universal exclusion: current relevant roles vary materially.

---

# 12. Proposed final recruiter story

> **Miguel is a manager-level AI adoption and digital transformation professional with deep digital-production and creative-technology experience. He identifies operational friction, aligns stakeholders, translates needs into practical AI-enabled workflows/MVPs, and helps teams adopt scalable ways of working. His technical background allows him to bridge business, operations and specialist teams without presenting himself as an AI engineer.**

The creative/3D/XR history becomes the differentiator underneath this identity — not a competing career direction.

---

# 13. Decisions requiring Miguel's approval before implementation

1. Approve / reject the primary spine: **AI Adoption & Digital Transformation Manager**.
2. Decide whether `GenAI Enablement Lead` should be the strongest secondary title.
3. Confirm the correct current metrics and team scope; specifically resolve the old-vs-new CV discrepancy.
4. Approve removing `AI Systems Lead` and Head-of language from the primary positioning.
5. Choose which 3–4 projects become the main proof set.
6. Approve preserving the current visual identity rather than redesigning from zero.
7. Provide/export LinkedIn for the final detailed audit before changing it.

Once these are approved, implementation should occur on isolated branches/worktrees and be reviewed by a different agent before merge.
