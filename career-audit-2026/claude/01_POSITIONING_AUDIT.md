# 01 — Positioning Audit

**Controlling question:** If a recruiter or hiring manager spends 30 seconds with this profile, what professional do they understand Miguel Ángel is, what problems do they believe he solves, what seniority do they infer, and for which roles would they realistically consider interviewing him?

Evidence tags: **[OBSERVED] / [INFERENCE] / [UNCERTAIN] / [RECOMMENDATION]**. Analysis is of `index.html` inherited from `main` plus the embedded CV.

---

## 1. What professional identity is communicated *now*?

### 1.1 The literal signals, in the order a visitor meets them

| Surface | Exact copy | What it asserts |
|---|---|---|
| `<title>` | "Miguel Ángel Ballesteros — AI-Driven Digital Production Systems" | **[OBSERVED]** Identity = a *category he coined*, not a job title. |
| Nav logo | "MABZ" | **[OBSERVED]** Initials only. No role. |
| Hero eyebrow | "Portfolio 2026" | **[OBSERVED]** Frames the page as a *portfolio* (creative-industry convention), not a CV or a leadership profile. |
| `<h1>` | "Miguel / Ángel / Ballesteros" (three lines, `<br>`) | **[OBSERVED]** The single most weighted element on the page is **the name only** — no role, no discipline, no seniority. |
| `<p class="hero-role">` | "AI-Driven Digital Production Systems" | **[OBSERVED]** Repeats the coined category. |
| `<p class="hero-desc">` | "I design systems, workflows and AI-enabled solutions that help teams move beyond fragmented operations toward scalable, measurable transformation." | **[OBSERVED]** Abstract. No domain noun (marketing? content? automotive?), no team-size, no seniority verb ("lead / own / run"), no named outcome. |
| About | "Currently at Accenture Marketing Operations, leading GenAI and digital innovation initiatives. Previously founder of a digital studio and also XR specialist at Accenture Song / Fjord." | **[OBSERVED]** First concrete anchor: Accenture + GenAI + Marketing Operations. Also first hint of a *creative→ops* career arc. |
| Contact | "Currently Assistant Manager at Accenture, leading AI & digital innovation. Open to senior opportunities that genuinely match my profile — Head of Digital Production, Digital Transformation Lead or AI Systems Lead roles…" | **[OBSERVED]** The clearest positioning statement on the entire page — job title *and* three target titles — and it is the **last content block before the footer.** |

### 1.2 Synthesised identity

**[INFERENCE, confidence: high]** The page communicates: *"A long-tenured (20+ yr) creative-and-production professional — art direction → 3D → XR → digital production — who over the last ~2–3 years has moved into GenAI-enabled operations and internal tooling inside Accenture's Marketing Operations, and who now wants to be read as a systems/transformation thinker rather than a maker."*

The **intent** is "AI systems / transformation leader." The **delivered impression** is "senior creative/production generalist, recently AI-adjacent."

The gap between those two is the core positioning problem this audit returns to repeatedly.

---

## 2. What canonical job families / titles does it map to?

Recruiters and ATS filters work from recognised titles and boolean keyword searches. Mapping the evidence:

| Canonical family | Strength of fit from *portfolio evidence* | Why |
|---|---|---|
| **AI / GenAI Enablement & Operations** (e.g. "GenAI Enablement Lead", "AI Operations Manager", "AI Delivery/Workflow Lead") | **Strongest** | **[OBSERVED]** GenAI hub work, ComfyUI enablement programme, AI-assisted QA system, AI in production pipelines, "structured enablement" language. This is the most current, most specific, most differentiated evidence — and it maps to a job family that is hiring. |
| **Digital Production / Studio Operations Management** (e.g. "Head of Digital Production", "Production Operations Manager", "Studio Ops Lead") | **Moderate–strong** | **[OBSERVED]** Studio founder 2016–2020; "Coordinated multidisciplinary teams of up to 50 people" (CV); "Led … a five-person interior lighting team" (Project 07); Accenture Marketing Operations. **[UNCERTAIN]** No evidence of budget/P&L ownership, headcount responsibility, or hiring authority. |
| **Digital / Business Transformation** (e.g. "Digital Transformation Lead / Manager") | **Weak–moderate, aspirational** | **[OBSERVED]** "Operational Transformation" capability; workshop facilitation ("22 stakeholders aligned"); Radisson diagnostic. **[INFERENCE]** Transformation roles at this level usually expect named enterprise programmes with owned, board-visible, quantified outcomes. The evidence here is internal tooling + facilitation, not programme leadership. |
| **Product Management** (e.g. "Product Manager", "Product Lead") | **Weak** | **[OBSERVED]** ESIC Product Manager cert (2025); "Product & Experience Systems" capability; two projects framed as "product concept" / "MVP". **[INFERENCE]** All product work is concept/MVP stage; no shipped product, no roadmap ownership, no user/revenue metrics, no PM job history. Reads as "training + aspiration", not track record. |
| **AI / ML Engineering** (implied by "AI Systems Lead") | **Very weak / misleading** | **[OBSERVED]** CV lists "Python (basic, in progress)". "AI Systems Lead" will attract ML-engineering screens he cannot pass; it mis-signals. |
| **Creative Direction / Art Direction / 3D / XR** | **Present but de-emphasised** | **[OBSERVED]** Deep history (Animum, C.E.V., UTAD XR, Fjord XR, "Hyperreal Asset Production", "SEAT Immersive"). The portfolio deliberately downplays this, but it is the most *proven* part of the record. |

**[INFERENCE, confidence: high]** The page currently maps *cleanly* to **no single canonical title**. Its own coined label — "AI-Driven Digital Production Systems" — returns nothing on a job board, matches no ATS filter, and gives a recruiter no seniority band. The three self-nominated targets (Head of Digital Production / Digital Transformation Lead / AI Systems Lead) point in three different directions and three different departments.

---

## 3. Is the value proposition understandable in 5–30 seconds?

**[OBSERVED] 5-second test (hero only):** A visitor sees the name, "AI-Driven Digital Production Systems", and "I design systems, workflows and AI-enabled solutions that help teams move beyond fragmented operations toward scalable, measurable transformation."

**[INFERENCE, confidence: high]** At 5 seconds the visitor knows: *this person does something with AI and systems, and is a designer/consultant of some kind.* They do **not** know: the industry, the seniority, whether he builds or advises, whether he manages people, or what title to slot him under. Every noun in the hero is abstract ("systems", "workflows", "solutions", "operations", "transformation"). There is no concrete anchor until the About section (Accenture / GenAI / Marketing Operations), which is one scroll down.

**[OBSERVED] 30-second test:** With one or two scrolls the visitor reaches About and the "20+ / 10+ / 5+ / 10+" stat row. They now know: Accenture, GenAI, 20 years, ex-studio-founder, ex-XR. They still do not reach the target-role statement (Contact) or any hard business outcome within 30 seconds of normal scrolling.

**Verdict:** The *theme* (AI + systems + operations) lands in 5 seconds. The *proposition* (what he'd be hired to do, at what level, in what context) does **not** land in 30 seconds. Confidence: high.

---

## 4. Does breadth read as senior multidisciplinary capability, or as dispersion?

**[OBSERVED]** The record spans, chronologically: graphic art & advertising (C.E.V., 2001–03) → digital art/animation (Animum) → 3D / lighting / art direction in studios (≈2009–2016) → founder of a digital studio (2016–2020) → XR specialist at Accenture Song/Fjord (≈2020–2022) → GenAI & digital innovation at Accenture Marketing Operations (≈2022–present). Certifications added in 2025: Google PM, ESIC Product Management, Design Thinking.

**[INFERENCE, confidence: medium-high]** This currently reads **closer to dispersion than to senior multidisciplinary capability**, for three reasons:

1. **The connective tissue is asserted, not shown.** The About section *tells* the reader the breadth "now informs a strategic and systems-oriented approach" (CV) / "structures that actually scale" (portfolio), but the case studies don't demonstrate a moment where the creative depth *created* a transformation outcome that a non-creative couldn't have.
2. **The pivot is recent and the proof is thin.** The most senior-sounding claims (transformation, systems, product) sit on the *newest* ~3 years and on *MVPs, concepts and internal tools*. The most *proven* work (XR delivery, 3D production, team supervision) is the older, de-emphasised part.
3. **The 2025 certification stack** (three certs in one year: PM, Product, Design Thinking) signals *repositioning in progress* to an experienced recruiter — which can read as "credential-building to change lanes" rather than "consolidated seniority."

**[INFERENCE]** Multidisciplinarity *can* be made an asset here (few AI-ops people have shipped hyperreal automotive CGI or run a studio), but only if a single spine is chosen and the breadth is framed as *evidence for that spine*. Right now the breadth is presented as a list, and lists of unlike things read as dispersion.

---

## 5. Does the narrative communicate progression from execution to ownership/leadership?

**[OBSERVED] Ownership/leadership evidence present:**
- "Previously founder of a digital studio" (About) — genuine ownership signal.
- "Coordinated multidisciplinary teams of up to 50 people" (CV).
- "Led the interior lighting function for a team of five, supervising onboarding, reviewing work quality" (Project 07).
- "Designed and facilitated a workshop … 22 stakeholders aligned" (Project 04 / Radisson).
- "Created and delivered a practical enablement program" (Project 06 / ComfyUI).
- Contact: "Currently Assistant Manager at Accenture, leading AI & digital innovation."

**[OBSERVED] Execution / individual-contributor language dominates the case studies:** "designed", "defined", "prototyped", "contributed to", "shaped", "supported". Project verbs by project:
- 01 QA: "designed", "defined and prototyped" — MVP.
- 02 Estimation: "designed", "structured", "defined" — framework, "1 reusable estimation framework designed".
- 03 Try-On: "designed", "positioned" — "End-to-end product concept defined".
- 04 Radisson: "Designed and facilitated" — the one with a stakeholder count.
- 05 SEAT: **"Contributed to the experience architecture…"** — explicitly a contributor, not owner.
- 06 ComfyUI: "Created and delivered" — training programme.
- 07 Hyperreal: "Led and supervised a five-person … team" — the clearest management verb, on the *oldest* project.

**[INFERENCE, confidence: high]** The narrative does **not** currently show a clean execution→ownership arc. It shows a *strong execution/design record* with *scattered, mostly small-scale or facilitative* leadership moments, and the biggest management claim (team of 50, in the CV) is **not surfaced anywhere on the portfolio**. A recruiter looking for "has this person grown into ownership?" will find the answer ambiguous.

**[OBSERVED]** "Assistant Manager" is Accenture's job grade for a mid-level individual contributor / small-team lead (roughly the Consultant–Manager boundary; below "Manager", well below "Senior Manager" / "Director"). Stating it plainly in the Contact section is honest, but it **caps the perceived seniority** at exactly the moment the visitor is deciding whether he's a "Head of" candidate.

---

## 6. What seniority does the page *signal* (vs. claim)?

| Signal | Direction |
|---|---|
| 20+ years experience (About, stat row) | ↑ senior |
| "founder of a digital studio" | ↑ ownership |
| "leading GenAI and digital innovation initiatives" | ↑ (but "initiatives" is vague) |
| "Assistant Manager at Accenture" (stated) | ↓ mid-level |
| Case studies = MVPs, concepts, internal tools, facilitation | ↓ pre-scale / IC |
| "Contributed to…", "shaped…", "supported…" verbs | ↓ IC |
| No P&L, budget, headcount, hiring, org-design evidence | ↓ not "Head of" |
| Three fresh 2025 certs | ↔ / ↓ (repositioning) |
| Named enterprise brands on a logo wall | ↑ (borrowed) |
| Self-described target: "Head of / Lead" roles | ↑ aspiration |

**[INFERENCE, confidence: high]** Net signalled seniority: **mid-to-upper individual contributor / emerging lead** — someone a hiring manager would consider for a *Manager*, *Senior Specialist*, *Lead (small team)*, or *Principal-track* role. The page asks to be read as **Head-of / Director-adjacent**; the evidence does not carry that, and the honest "Assistant Manager" line actively contradicts it. This mismatch is a credibility risk (see §8).

---

## 7. Which claims are credible, and which need stronger proof?

### Credible on current evidence
- **[OBSERVED]** 20+ years across creativity/technology/business — consistent across portfolio and CV; long history is self-evidently real from the certification/education dates (C.E.V. 2001–03 onward).
- **[OBSERVED]** Studio founder 2016–2020 — plausible, specific, repeated.
- **[OBSERVED]** XR/3D/CGI production depth — heavily corroborated (UTAD XR Expert, Animum, Fjord, "Hyperreal Asset Production", tool list: Unreal, Unity).
- **[OBSERVED]** Currently at Accenture Marketing Operations doing GenAI enablement — specific, internally consistent, matches the tool list (ComfyUI, Claude Code, Stable Diffusion, Flux, Microsoft 365 + Copilot).
- **[OBSERVED]** Ran a diagnostic workshop with 22 stakeholders — concrete and modest enough to be believable.
- **[OBSERVED]** Delivered a ComfyUI enablement programme — believable, matches profile.

### Needs stronger proof
| Claim | Where | Problem |
|---|---|---|
| "10+ End-to-end systems designed & delivered" | Stat row | **[OBSERVED]** Only ~5–7 are shown, several are MVP/concept, "delivered" is doing heavy lifting. Unsupported. |
| "5+ Industries transformed" | Stat row | **[INFERENCE]** "Transformed" is a very strong verb for what the case studies show (mostly diagnosis + tooling). |
| "10+ Global brands worked with" | Stat row + logo wall | **[UNCERTAIN]** No indication of role, depth, or recency per brand. Reads as agency-roster borrowing. |
| ≈30% cost reduction / ≈40% faster time-to-market / up to ≈40% productivity gain | **CV body only** (medium-confidence read; figures behind subset font) | **[INFERENCE]** These are almost certainly *Accenture-capability-level* aggregate figures, attributed here to individual contribution ("Optimized pipelines through AI and automation, contributing to a …% reduction"). Directionally plausible, individually unattributable, and — critically — **absent from the portfolio entirely.** |
| "Anticipated a market direction later validated by mainstream retail adoption" (Project 03) | Portfolio | **[OBSERVED]** Unfalsifiable self-praise. Weakens credibility rather than adding it. |
| "leading AI & digital innovation" (Contact) | Portfolio | **[UNCERTAIN]** vs. stated grade "Assistant Manager". What is actually led — a workstream? a team? a hub contribution? Not resolvable from evidence. |
| "Head of Digital Production" as a realistic target | Contact | **[INFERENCE]** No prior "Head of" title, no org/budget evidence; this is a stretch target stated as if it were a lateral move. |

---

## 8. What is missing for a recruiter to classify the candidate quickly?

**[OBSERVED] Absent from the page:**
1. **A recognised current job title in the hero or About.** (It only appears in Contact, as "Assistant Manager".)
2. **A one-line "I am a ___ who does ___ for ___" statement** using words a recruiter searches for.
3. **Any hard business outcome above the fold or in the stat row** — the CV's percentage figures never appear.
4. **Team-size / scope of leadership** — "up to 50 people" is in the CV, not the portfolio.
5. **Industry/context focus** — is he "marketing operations", "automotive", "enterprise services"? The page avoids committing.
6. **Location / work-authorisation / remote preference** — only "Madrid, Spain" in the CV; the portfolio Contact says "Any industry, any scale" but not *where* or *how* he can work.
7. **Recency framing on the brand wall** — which brands are Accenture-era vs studio-era.
8. **A dated, structured career timeline** — the portfolio has no chronology at all; roles are only in prose in About.
9. **Proof of the "systems that scale" claim** — an artefact, a before/after, a diagram, an adoption number.
10. **A clear, single primary CTA for a recruiter** ("See CV" / "Book a call") — currently the hero CTAs are "Explore my work" and "Get in touch"; "Download CV" is only in Contact.

---

## 9. What target roles appear strongest from the evidence?

Without forcing a predetermined answer, ranked by *fit to demonstrated evidence* (not by ambition):

1. **GenAI Enablement / AI Operations Lead (services, marketing, or content-production context)** — e.g. "GenAI Enablement Lead", "AI Workflow / Delivery Manager", "AI Operations Manager", "Content Automation Lead". **[INFERENCE]** Best match: current role, ComfyUI programme, AI-QA system, estimation system, "structured enablement" framing, tool fluency. Realistic seniority: Manager / Senior Manager / Lead.
2. **Head of / Senior Manager, Digital Production or Studio Operations** — **[INFERENCE]** Supported by studio-founder history + production depth + Accenture MarOps + team coordination, *if* the leadership scope (team of 50, delivery ownership) is evidenced properly. Currently under-proven for "Head of"; solid for "Senior Manager / Production Lead".
3. **Digital Transformation Manager (operations-focused, not strategy-consulting)** — **[INFERENCE]** Plausible as a *stretch* if Radisson-type diagnostic work and internal-tooling outcomes are quantified and expanded. Weak today.
4. **Product Operations / Product Manager (AI tooling / internal products)** — **[INFERENCE]** Only if the QA and Estimation systems are reframed as products with adoption metrics. Currently aspiration + certificate.

**[RECOMMENDATION — direction only, for the cross-review phase]** Pick **one** primary spine (the evidence points hardest at #1, "AI enablement / AI operations", with digital-production leadership as the credible secondary). Rewrite the hero, `<title>`, About opener and the single CTA around that spine. Demote "AI Systems Lead" (mis-signals engineering) and treat "Digital Transformation Lead" as a future target, not a current claim. Do **not** implement yet — validate against real job descriptions first, per `00_CONTEXT.md` §6.

---

## Required summary

### 30-second recruiter interpretation
*"An experienced (20+ yr) creative-and-digital-production professional — studio founder, ex-Accenture Song/Fjord XR — who has spent the last ~3 years moving into GenAI-enabled operations and internal tooling at Accenture Marketing Operations, currently at mid-level grade (Assistant Manager). Strong, articulate systems-thinking narrative; but the concrete work shown is mostly internal MVPs, frameworks, concepts and workshop facilitation rather than shipped products or owned, quantified business outcomes. Unclear whether to slot him as production/ops manager, AI-enablement specialist, or product-leaning generalist. Interesting, not yet classifiable — would need a conversation."*

### Strongest perceived professional identity
**AI/GenAI-enabled operations & workflow designer inside a large services organisation**, sitting on top of a long creative/production and XR foundation. This is also the identity best supported by evidence — but the page currently sells a broader, more senior "systems & transformation leader" identity that the evidence doesn't carry.

### Biggest positioning risk
**The profile is built around a coined category ("AI-Driven Digital Production Systems") that maps to no recruiter search, no ATS filter and no seniority band — while the one plain job title on the page ("Assistant Manager") is buried in the footer and caps perceived seniority.** Result: the strongest, most current, most differentiated asset (operationalising GenAI inside a global consultancy) fails to get classified, and the fallback impression — "senior creative generalist who recently added AI" — drops him into a crowded, lower-seniority applicant pool and works against every one of his three stated target titles.

### Confidence
**High** on the identity gap, the classification failure, and the seniority mismatch (all from directly observed copy). **Medium** on the specific ranked target roles (depends on facts only a conversation or the LinkedIn/CV detail can confirm — team scope, what "leading" means, real outcome ownership).
