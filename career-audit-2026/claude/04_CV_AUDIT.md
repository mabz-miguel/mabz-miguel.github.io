# 04 — CV Audit

## 0. Extraction method & reliability

**[OBSERVED]** The CV is a ~88 KB PDF embedded as a base64 `data:` URI behind the "Download CV" link in `#contact` (single page, judging by layout). It is **not** an image scan — it carries real text — but the text is drawn through an **embedded subset font with a substitution encoding**, so naïve copy/extraction yields scrambled characters.

**Reliability of this audit's reading:**
- **High confidence:** section structure, headings, job titles, employers, bullet wording, project list, tool list, languages, keyword block. Recovered by frequency + crib analysis and cross-checked against the portfolio, which paraphrases the same content.
- **Medium confidence:** the three headline **percentage figures** (cost / time-to-market / productivity) and a few **certification years** — these render through a second subset font whose digits are only partially resolved. Read as *approximate* (≈30% / ≈40% / up to ≈40%).
- **Not resolved:** exact start/end months on some roles.

**[INFERENCE]** The encoding is almost certainly an incidental artefact of the export tool (e.g. a design app flattening custom fonts), **not deliberate**. But it has two real consequences and both are covered in `06_TECHNICAL_AUDIT.md` §3: (a) **copy-paste from the PDF produces garbage**, which breaks a recruiter's normal workflow and many **ATS parsers**; (b) selectable-but-unmappable text can make an ATS score the CV as near-empty.

---

## 1. Reconstructed CV structure

Order as it appears in the file:

1. **Header** — Name; a title line (≈ "AI Transformation & Digital Production Systems | AI Workflows | Operations & Technology"); location "Madrid, Spain"; email `mabz.miguel@gmail.com`; `linkedin.com/in/miguelballesteroszafra`; `mabz-miguel.github.io`.
2. **Summary** (~4 sentences).
3. **Keywords** block (explicit comma-separated list — clearly an ATS device).
4. **Professional Experience** — 4 roles, each with a dated header, bullets, and a "Tools & Tech" line.
5. **Selected Projects** — 5 items.
6. **Certifications** — ~10 items.
7. **Tools & Tech** (consolidated).
8. **Languages**.

---

## 2. Headline / identity

**[OBSERVED]** Title line ≈ *"AI Transformation & Digital Production Systems | AI Workflows | Operations & Technology"* (pipe-delimited).

| Finding | Tag |
|---|---|
| Same coined category as the portfolio ("… Digital Production Systems") | [OBSERVED] — consistent, but see `01`: maps to no standard title / ATS filter. |
| Pipe-stacked keyword phrases rather than a role | [OBSERVED] — reads as SEO string, not a job title a recruiter recognises. |
| No seniority marker in the headline ("Lead", "Manager", "Head of", "Senior") | [OBSERVED] |
| No current employer/role in the headline area (only in the experience section) | [OBSERVED] |

**[INFERENCE, confidence: high]** The CV headline has the same core problem as the portfolio hero: it names an invented category and a keyword cloud instead of a role + level a recruiter can slot.

---

## 3. Summary

**[OBSERVED — reconstructed]:**
> "Specialized in GenAI adoption, operational design and process optimization to improve efficiency, scalability and time-to-market. Combines strategic thinking, hands-on digital production knowledge and cross-functional leadership to connect business, operations and technology. Currently contributing through the GenAI hub to accelerate AI adoption across the capability and turn operational needs from team leads into practical solutions, KPIs and scalable internal initiatives. Experienced in stakeholder management, workshop facilitation, KPI definition, capability building and the design of solutions that transform fragmented processes into measurable business value."

| Finding | Tag |
|---|---|
| Denser and more concrete than the portfolio's About | [OBSERVED] positive — names GenAI hub, KPIs, enablement, workshop facilitation |
| Still opens with an abstraction ("Specialized in … operational design and process optimization") rather than "X years / current role" | [OBSERVED] |
| "contributing through the GenAI hub … across the capability" | [OBSERVED] — honest but signals *contributor within a capability*, not owner/leader |
| "measurable business value" promised; summary itself carries no number | [OBSERVED] |
| No years-of-experience figure in the summary (the portfolio says 20+) | [OBSERVED] inconsistency of emphasis |

---

## 4. Chronology

**[OBSERVED — reconstructed]** 4 roles:

| # | Employer / context | Title (reconstructed) | Dates (approx) |
|---|---|---|---|
| 1 | **Accenture — Marketing Operations** | AI & Digital Innovation lead role; grade **Assistant Manager** (per portfolio Contact) | ≈2022 – Present, Madrid |
| 2 | **Accenture Song / Fjord** | XR Specialist | ≈2020 – 2022 |
| 3 | **[Own] digital studio** | Founder / Creative & Studio Director | ≈2016 – 2020 |
| 4 | **Studio(s)** (creative/tech) | Digital Artist / Art Direction / 3D | ≈2009 – 2016 |

| Finding | Tag |
|---|---|
| Reverse-chronological, standard | [OBSERVED] positive |
| ~2009 start = ~16–17 years of dated experience; portfolio claims "20+" (earlier C.E.V. 2001–03 training likely bridges the gap) | [OBSERVED] minor inconsistency |
| Role 1's exact title in the CV is unclear from the reconstruction; portfolio Contact says "Assistant Manager", About says "leading GenAI and digital innovation initiatives" | [UNCERTAIN] — the single most important title on the CV needs to be verified and made unambiguous |
| Months not resolvable | [UNCERTAIN] |
| Two Accenture entities (Song/Fjord, then Marketing Operations) — reads as internal move; could be framed as continuity or fragmentation | [INFERENCE] |

---

## 5. Experience framing — accomplishments vs responsibilities

### Role 1 — Accenture Marketing Operations (reconstructed bullets)
- "Led GenAI adoption, digital transformation and workflow optimization initiatives within the [capability] to improve operational efficiency and develop new internal capabilities."
- "Contributed through the GenAI hub to accelerate AI adoption across the capability and support team leads by translating operational needs into practical solutions, KPIs and internal tools."
- "Designed systems and solutions for digital production, content QA and project estimation, aimed at standardizing processes and reducing dependence on manual work."
- "Defined AI-enabled proposals and KPIs, including automated QA systems, estimation frameworks and hybrid workflows for marketing operations."
- "Facilitated strategic workshops with stakeholders to diagnose operational issues, align priorities and convert findings into actionable improvement areas."
- "Optimized pipelines through AI and automation, contributing to a **≈30%** reduction in operational costs, a **≈40%** acceleration in time-to-market, and productivity increases of up to **≈40%**." *(figures medium-confidence)*
- "Coordinated multidisciplinary teams of up to **50** people and collaborated cross-functionally with technical, creative and business profiles on international projects."

| Finding | Tag |
|---|---|
| Mix of "Led / Designed / Defined / Facilitated / Coordinated" verbs — reasonable accomplishment orientation | [OBSERVED] positive |
| **Bullet 1 says "Led … digital transformation"; bullet 2 says "Contributed … support team leads"** — internal tension between leader and contributor framing in adjacent lines | [OBSERVED] |
| The only quantified bullet lumps three big percentages into "contributing to" — **attribution is hedged and the numbers are capability-level** | [INFERENCE] credibility risk (also `01` §7, `02` §6) |
| "teams of up to 50 people" — strong scope signal, **buried as the last bullet** and **absent from the portfolio** | [OBSERVED] |
| Several bullets end in "aimed at …" / "to improve …" — intent, not result | [OBSERVED] |

### Role 2 — Accenture Song / Fjord, XR Specialist
- "Contributed to immersive projects and digital experiences for global clients, including realtime showroom environments, VR/AR and product communication."
- "Delivered VR and AR experiences for international brands and events, connecting user experience, interaction and business goals."
- "Collaborated with international teams in high-demand environments, integrating design, technology and digital production."
- Tools: Figma, Adobe Creative Suite, Unreal Engine, Unity, 3D pipelines.

| Finding | Tag |
|---|---|
| "Contributed / Delivered / Collaborated" — mostly responsibility-level, no outcome, no scale | [OBSERVED] |
| No client named, no project named, no metric | [OBSERVED] |

### Role 3 — Digital studio, Founder / Director
- "Led end-to-end digital projects for clients across automotive, healthcare, public administration and communication."
- "Managed client relationships directly, including requirements definition, planning, execution and delivery of digital, interactive and visual solutions."
- "Coordinated external collaborators and held full responsibility for scope, quality, timelines and client delivery."
- Tools: VR/AR, motion graphics, 3D, interactive experiences, Adobe Suite.

| Finding | Tag |
|---|---|
| Best ownership language on the CV ("held full responsibility for scope, quality, timelines and client delivery") | [OBSERVED] positive |
| Still no numbers — clients, revenue, team size, project count, years of runway all absent | [OBSERVED] |
| "founder" not explicitly in the reconstructed title line (portfolio says "founder of a digital studio") | [UNCERTAIN] |

### Role 4 — Studios, Digital Artist / Art Direction / 3D
- "Developed projects in design, branding, advertising, VR/AR and digital production across creative and technology-driven environments."
- "Built a strong technical foundation in visual production and digital experience, which now informs a strategic and systems-oriented approach."

| Finding | Tag |
|---|---|
| Second bullet is a *bridge sentence* (justifying the pivot), not an accomplishment | [OBSERVED] |
| Appropriately short for the oldest role | [OBSERVED] positive |

**[INFERENCE, confidence: high]** Across all four roles: verbs are decent, but **quantified outcomes appear exactly once** (Role 1, hedged, capability-level), and **team/scope numbers appear once** (Role 1, "up to 50", last bullet). Roles 2–4 have **zero** numbers. The CV is responsibility-led with a thin accomplishment layer.

---

## 6. Quantified impact

**[OBSERVED]** The entire quantified content of the CV:
- ≈30% operational-cost reduction / ≈40% time-to-market acceleration / up to ≈40% productivity increase (Role 1, "contributing to", medium-confidence read).
- "teams of up to 50 people" (Role 1).
- "22 stakeholders" (Radisson project).
- "1 reusable estimation framework" (Estimation project — a deliverable count).

**[INFERENCE, confidence: high]**
- The three percentages are the CV's only "impact numbers" and they are **framed as capability outcomes he contributed to**, not outcomes he owned. A sharp interviewer will probe "what exactly did *you* move, and how is it measured?" — and the CV gives no baseline, timeframe, or method.
- **No numbers of the kind leadership roles screen for:** budget managed, headcount reporting to him, number of markets/teams served, adoption rate of a tool he built, hours saved, revenue influenced, NPS/quality delta.
- Roles 2–4 spanning ~13 years contain **no metric at all**.

---

## 7. Leadership / ownership evidence

**[OBSERVED] Present:** studio founder with "full responsibility for scope, quality, timelines, client delivery" (Role 3); "Coordinated multidisciplinary teams of up to 50 people" (Role 1); "support team leads" (Role 1); workshop facilitation with 22 stakeholders (project). **[OBSERVED] Absent:** direct-report headcount, hiring/performance responsibility, budget/P&L, org design, a "Head of / Manager of X" line item.

**[INFERENCE]** The CV supports **"experienced operator who has run a small business and coordinated large cross-functional groups"**. It does **not** yet support **"people manager / department head"**. "Coordinated … up to 50 people" is ambiguous (coordinated ≠ managed) and should be disambiguated.

---

## 8. AI / product / project / operations / technical balance

**[OBSERVED]** Weighting across the CV:
- **AI / GenAI:** heavy and current — summary, Role 1 bullets, 3 of 5 projects, tool list (ComfyUI, Claude Code, Stable Diffusion, Flux, Copilot). **Strongest, most differentiated axis.**
- **Operations / process:** heavy — "operational design", "process optimization", estimation, QA, workshops, KPIs.
- **Project / delivery management:** moderate — "planning, execution and delivery", Google PM cert, "program coordination" keyword.
- **Product:** light — ESIC cert, "product concept" (Try-On), "Product & Experience Systems" framing; no product-role history, no roadmap/metric ownership.
- **Technical / hands-on:** moderate but explicitly bounded — "Python (basic, in progress)"; strong on creative-tech (Unreal, Unity, ComfyUI) not on software engineering.

**[INFERENCE, confidence: high]** The centre of gravity is **AI-enabled operations / enablement**. "Product" and "technical (engineering)" are the weakest axes and are exactly the two that the target title "AI Systems Lead" implies — another argument (with `01`) that this target mis-signals.

---

## 9. ATS clarity & keywords

**[OBSERVED positives:**
- A dedicated **Keywords** block: "AI Transformation, Digital Transformation, Generative AI (GenAI), GenAI Adoption, AI strategy, Operational Design, Workflow Optimization, Process Improvement, Automation, Systems Design, Business Process Analysis, Stakeholder Management, Cross-functional Leadership, Workshop Facilitation, KPI Definition, Capability Building, Project Management, Program Coordination, Quality Assurance, Content QA, Estimation Systems, Innovation Management, Continuous Improvement, Agile, Scrum."
- Standard section names (Professional Experience, Certifications, Languages).
- Single-column layout (reconstruction suggests no multi-column/table trap).

**[OBSERVED / INFERENCE — problems, confidence: medium-high]:**
1. **The embedded-font encoding is an ATS risk.** If the parser reads the glyph codes rather than Unicode, the CV parses as gibberish or as near-empty — which can auto-reject regardless of keyword content. This must be verified with an actual ATS/text-extraction test; it is the single most important CV issue to check. (See `06` §3.)
2. **No standard job titles.** ATS and recruiter boolean searches key on "Manager", "Lead", "Head of", "Consultant", "Director". The CV's headline and Role 1 title (as reconstructed) don't clearly contain any.
3. **Keyword stuffing block** can be down-weighted by modern ATS and reads awkwardly to a human — better to distribute the keywords into real bullets.
4. **"Python (basic, in progress)"** will surface him in "Python" searches for roles he can't do — a false-positive keyword.
5. Contact block has email/phone/links as text — fine for ATS **if** the encoding issue is resolved.

---

## 10. Signal-to-noise

**[INFERENCE, confidence: medium-high]**
- **Signal:** GenAI-hub work, ComfyUI enablement, QA/estimation systems, studio ownership, XR depth, the one quantified bullet, the tool stack.
- **Noise:** the coined pipe-headline, the keyword-stuffing block, "aimed at / to improve" intent-endings, the bridge sentence in Role 4, capability-level percentages presented as personal impact.
- **Buried signal:** "teams of up to 50", the specific tool stack, the studio's "full responsibility" line — all present but positioned late or under-weighted.

For a one-page CV the density is reasonable, but the *most persuasive facts are not in the most prominent positions*, and the headline spends its prime real estate on a keyword string.

---

## 11. Consistency with the portfolio

| Dimension | Portfolio | CV | Consistent? |
|---|---|---|---|
| Coined category "…Digital Production Systems" | ✅ hero + title | ✅ headline | ✅ (consistently problematic) |
| Current employer = Accenture Marketing Operations | ✅ | ✅ | ✅ |
| Current grade "Assistant Manager" | ✅ (Contact only) | ⚠️ unclear in reconstruction | needs check |
| Years of experience | "20+" (About + stat) | not stated numerically | ⚠️ emphasis differs |
| Studio founder 2016–2020 | ✅ (About, undated) | ✅ (dated) | ✅ |
| XR at Song/Fjord | ✅ | ✅ | ✅ |
| Role 4 (2009–2016 studios) | ❌ not mentioned | ✅ | ⚠️ portfolio omits the earliest ~7 years |
| % impact figures (≈30/40/40) | ❌ absent | ✅ (Role 1) | ❌ **portfolio hides the CV's only hard numbers** |
| "Team of up to 50" | ❌ absent | ✅ | ❌ portfolio hides the biggest scope signal |
| Projects: QA, Estimation, Try-On, Radisson, ComfyUI | ✅ (+ SEAT, Hyperreal) | ✅ (5 of 7) | ✅ mostly; portfolio adds 2 |
| Radisson "22 stakeholders" | ✅ | ✅ | ✅ |
| Tool stack (ComfyUI, Claude Code, etc.) | ❌ not shown | ✅ | ❌ portfolio hides it |
| Target roles (Head of DP / Transformation Lead / AI Systems Lead) | ✅ (Contact) | ❌ not stated | ⚠️ CV doesn't declare a target |
| Languages / English B2 | ❌ | ✅ ("English B2, daily use in international environments") | ⚠️ portfolio silent; B2 self-rating is modest for international leadership roles and worth a deliberate decision |

**[INFERENCE, confidence: high]** The two channels are **broadly consistent in story** but **the CV is the stronger evidence document** (dates, tool stack, the only numbers, the 50-person scope) — and the portfolio, which a recruiter sees first, *omits* exactly those stronger facts. The channels are inconsistent in the wrong direction: the weaker-evidence surface is the more prominent one.

---

## 12. What role does the CV currently appear optimised for?

**[INFERENCE, confidence: high]** The CV is optimised for **an AI-enablement / AI-operations / digital-operations role inside a large services or in-house environment**, at roughly **Manager / Senior Manager / Lead** level — driven by the keyword block, the summary, and Role 1. It is **not** optimised for:
- a **people-management / department-head** role (no headcount, budget, or org evidence, and "Assistant Manager" grade);
- a **product** role (no product history or metrics);
- an **engineering / "AI Systems"** role (Python "basic");
- a **strategy-consulting transformation** role (no named enterprise programmes with owned outcomes).

The headline *aims* wider and more senior than the body supports — the same gap identified in `01`.

---

## Summary judgement (CV)

**Strengths:** clear reverse-chronological structure; strong current AI/GenAI content; genuine ownership language in the studio role; concrete tool stack; a keyword-conscious approach; one quantified bullet; the "up to 50 people" scope fact exists.

**Weaknesses (ranked):**
1. **[P0-candidate]** Embedded-font encoding → likely breaks copy-paste and ATS parsing; must be tested and, if confirmed, re-exported as normal selectable Unicode text.
2. **[P1]** Headline is a coined category + keyword string, not a recognised role + level.
3. **[P1]** Only one quantified accomplishment, and it's hedged and capability-level; roles 2–4 (~13 years) have no metrics.
4. **[P1]** Leader-vs-contributor framing is internally inconsistent (Role 1 bullets 1 vs 2).
5. **[P1]** Current title/grade is ambiguous in the document and needs to be stated unambiguously and consistently with the portfolio.
6. **[P2]** Keyword-stuffing block should be dissolved into real bullets.
7. **[P2]** "Python (basic, in progress)" as a keyword; "English B2" self-rating — both need a deliberate keep/reframe decision.
8. **[P2]** The CV's strongest facts (numbers, scope, tools) don't appear on the portfolio — a cross-channel consistency fix.

**Do not rewrite the CV in this phase.** Direction only; decisions to be recorded in the cross-review documentation and validated against real job descriptions (`00_CONTEXT.md` §6, §Implementation rule).

**Confidence:** High on structure and content findings; **Medium** on the exact percentage figures and a few certification years (font-encoding limitation, see §0).
