# 02 — Portfolio Content Audit

Audit of the *content and hiring storytelling* of `index.html` (inherited from `main`). Evidence tags: **[OBSERVED] / [INFERENCE] / [UNCERTAIN] / [RECOMMENDATION]**.

Page structure (DOM section IDs, in order): `#hero` → `#about` → `#capabilities` → `#projects` → `#clients` → `#formation` → `#contact` → `<footer>`.

---

## 1. Hero

**[OBSERVED] Full hero copy:**
> Portfolio 2026
> **Miguel Ángel Ballesteros**
> AI-Driven Digital Production Systems
> I design systems, workflows and AI-enabled solutions that help teams move beyond fragmented operations toward scalable, measurable transformation.
> [Explore my work →] [Get in touch]
> Scroll

| Aspect | Finding |
|---|---|
| Category label | **[OBSERVED]** "AI-Driven Digital Production Systems" is invented. **[INFERENCE]** Zero search/ATS value; forces the recruiter to do the classification work themselves. |
| Descriptor sentence | **[OBSERVED]** 5 abstract nouns (systems, workflows, solutions, operations, transformation), 0 concrete nouns. No industry, no seniority, no proof, no audience specificity beyond "teams". |
| "measurable" | **[OBSERVED]** The hero promises "measurable transformation" but no measure appears in the hero, the stat row, or any case study on the page. The claim is immediately unbacked. |
| Missing | **[OBSERVED]** No current job title, no location, no availability status (that lives 6 sections down in Contact). |
| CTAs | **[OBSERVED]** "Explore my work →" (primary) and "Get in touch" (secondary). Neither is "See CV" or "Book a call". For a recruiter the fastest path (the CV) is not offered here. |
| Eyebrow "Portfolio 2026" | **[INFERENCE]** Signals creative-industry convention and datedness (will look stale in 2027). |

**[INFERENCE, confidence: high]** The hero optimises for *tone* (confident, minimal, "senior") over *information*. A recruiter leaves the hero knowing the vibe but not the facts.

---

## 2. About / professional narrative

**[OBSERVED] Full copy:**
> **Who I Am**
> I specialise in designing systems that transform the way organisations produce and deliver digital work — connecting strategy, operations and AI into structures that actually scale.
> Over 20 years' experience across creativity, technology and business — from art direction and digital production to product strategy, GenAI integration and operational transformation in enterprise environments.
> Currently at Accenture Marketing Operations, leading GenAI and digital innovation initiatives. Previously founder of a digital studio and also XR specialist at Accenture Song / Fjord.
>
> Tags: AI workflow design · Product systems · Digital production pipelines · Creative ops transformation
>
> **20+** Years across creativity, technology & business
> **10+** Global brands worked with
> **5+** Industries transformed
> **10+** End-to-end systems designed & delivered

| Aspect | Finding |
|---|---|
| First sentence | **[OBSERVED]** Still abstract ("systems that transform the way organisations produce and deliver digital work"). The concrete anchor (Accenture / GenAI) is the *third* sentence. |
| Career arc | **[OBSERVED]** "from art direction and digital production to product strategy, GenAI integration and operational transformation" — the arc is *stated in one clause* and never demonstrated. |
| "structures that actually scale" | **[OBSERVED]** Claim with no artefact, diagram, adoption figure, or before/after anywhere on the page. |
| Stat row | **[OBSERVED]** All four are "N+" soft numbers. Two ("5+ Industries transformed", "10+ End-to-end systems designed & delivered") use very strong verbs with no backing. **[INFERENCE]** Round-and-vague stats read as *marketing*, not *evidence* — the opposite of the intended effect. |
| Chronology | **[OBSERVED]** No dates, no timeline. The reader cannot place "founder of a digital studio" or "XR specialist" in time without opening the CV. |
| "leading GenAI and digital innovation initiatives" | **[OBSERVED]** vs. Contact's "Assistant Manager". **[UNCERTAIN]** what "leading initiatives" concretely means. |
| Tone | **[INFERENCE]** Reads as a positioning statement written *aspirationally* — describing the role wanted, not the role held. |

**[RECOMMENDATION — direction]** About should open with the plain fact (current title + employer + what he does there + years), then the arc, then proof. The stat row should carry at least one hard, attributable number or be removed.

---

## 3. Capabilities & Impact

**[OBSERVED]** Four capability cards, each with a description and a "What changes" list:

1. **Operational Transformation** — "I redesign fragmented production workflows into structured, repeatable systems…"
2. **Scalable Systems Design** — "I design operational systems — estimation models, planning structures, delivery frameworks…"
3. **AI Workflow Integration** — "I integrate AI into production pipelines — not as a tool layer on top of existing processes, but as a structural shift…"
4. **Product & Experience Systems** — "I design product and experience architectures that align design intent, technical logic and interaction…"

| Aspect | Finding |
|---|---|
| Quality of writing | **[OBSERVED]** This is the strongest-written section. The "What changes" bullets are specific and outcome-oriented in *kind* ("Planning becomes predictable — not dependent on who's in the room"). |
| Evidence linkage | **[OBSERVED]** None. No capability card links to the project(s) that prove it. Capability 1 ↔ Radisson, Capability 2 ↔ Estimation System, Capability 3 ↔ QA System + ComfyUI, Capability 4 ↔ SEAT/Try-On — but the reader has to make those connections unaided. |
| "What changes" vs "what changed" | **[OBSERVED]** All bullets are in the *general present/future* ("Teams stop operating on informal agreements…") — i.e. what *would* change. None says "here is where this happened and by how much." Aspirational voice again. |
| Overlap with Projects | **[INFERENCE]** Capabilities and Projects cover the same ground twice at different altitudes without cross-referencing — adds length, not proof. |
| Breadth signal | **[INFERENCE]** Four capabilities spanning ops, systems, AI *and* product/experience reinforces the dispersion risk from `01`. |

**[INFERENCE, confidence: medium-high]** Good copy, wrong job: it *describes a methodology* persuasively but functions as more claims rather than as evidence. Its value would multiply if each card were anchored to a named, dated, quantified project.

---

## 4. Selected Work / case-study structure

**[OBSERVED]** Seven projects, each with a fixed structure: **Context → Problem (3 bullets) → System Designed → Impact (3 bullets)**. Interaction: click a row to expand (accordion). Tags per project (e.g. "AI System / QA Automation / Product Strategy").

### 4.1 The seven-question test (per `CLAUDE_MASTER_PROMPT.md` §02)

| # | Project | 1. Problem? | 2. Exact role & ownership? | 3. What did he decide/lead? | 4. Stakeholders? | 5. What changed? | 6. Measurable outcome / scale? | 7. Skill proven for next level? |
|---|---|---|---|---|---|---|---|---|
| 01 | Intelligent Content QA System | ✅ clear (manual QA slow/inconsistent) | ⚠️ "designed"/"prototyped" — solo IC implied, not stated | ⚠️ system design & rules; no team/stakeholder decisions shown | ❌ none named | ⚠️ "Designed to reduce manual QA workload significantly" — *designed to*, not *did* | ❌ "Functional MVP" — no adoption, no % , no users | ✅ AI+QA systems thinking, product framing |
| 02 | Estimation Intelligence System | ✅ clear | ⚠️ "designed"/"structured" | ⚠️ model logic | ❌ "across capabilities" but none named | ⚠️ "1 reusable estimation framework designed" | ❌ "1 framework designed" is a deliverable count, not an outcome | ✅ operational modelling, standardisation |
| 03 | AI Virtual Try-On Platform | ✅ clear (fashion discovery impersonal) | ❌ "Concept product designed around…" — personal side project? client? unclear | ❌ concept only | ❌ none | ❌ "End-to-end product concept defined" | ❌ none; plus unfalsifiable "Anticipated a market direction later validated by mainstream retail adoption" | ⚠️ product vision — but concept-stage only |
| 04 | Radisson Process Transformation | ✅ clear | ✅ "Designed and facilitated" — clear ownership of the workshop | ✅ workshop design, facilitation, synthesis | ✅ **"22 stakeholders"** (a Paid Media team) | ✅ "Key operational blockers surfaced and structured" | ⚠️ **"22 stakeholders aligned"** — the single hardest number on the page; but alignment ≠ business result | ✅ facilitation, transformation diagnostics, stakeholder management |
| 05 | SEAT Immersive Product Experience | ✅ clear | ❌ **"Contributed to the experience architecture, interaction logic…"** — explicitly a contributor | ❌ not stated | ❌ none | ⚠️ "Realtime experience architecture shaped around product discovery" | ❌ none (no engagement metric, no launch data) | ⚠️ experience architecture — but contribution-level |
| 06 | AI Capability Enablement (ComfyUI) | ✅ clear | ✅ "Created and delivered a practical enablement program" | ✅ curriculum design + delivery | ⚠️ "the team" — size not given | ✅ "Shared learning foundation created for early AI adoption" | ❌ no headcount trained, no pre/post fluency measure, no adoption % | ✅ AI enablement, capability building, teaching |
| 07 | Hyperreal Asset Production with AI | ✅ clear | ✅ **"Led the interior lighting function for a team of five, supervising onboarding, reviewing work quality"** | ✅ clearest people-leadership on the page | ⚠️ team of five + "premium automotive campaigns" client unnamed | ✅ delivery consistency + AI env generation introduced | ⚠️ "five-person team" — real scope number, but small and this is the *oldest* project | ✅ team leadership, quality ownership, AI-in-production |

### 4.2 Cross-cutting content findings

- **[OBSERVED]** 4 of 7 projects have **no measurable outcome** (01 partial, 02 deliverable-count, 03 none, 05 none). Only 04 ("22 stakeholders") and 07 ("team of five") carry a real number, and both are scope numbers, not impact numbers.
- **[OBSERVED]** Role clarity is weakest exactly where seniority matters most: the two most enterprise-brand-adjacent projects (05 SEAT, 03 Try-On) have the vaguest ownership ("Contributed to…", "Concept product designed around…").
- **[OBSERVED]** No project names its client except by inference (Radisson, SEAT in titles; "premium automotive campaigns" = likely Mercedes). No project gives a date or duration.
- **[OBSERVED]** "System Designed" (past participle, passive-leaning) is the recurring verb — reinforces *design* over *own/ship/scale*.
- **[OBSERVED]** Project 03's "Anticipated a market direction later validated by mainstream retail adoption" is the single weakest sentence on the page: unprovable, self-congratulatory, and invites scepticism about the rest.
- **[INFERENCE]** The projects prove Miguel is a capable *systems designer and facilitator*. They do **not** prove he has *shipped and scaled* anything or *owned a business outcome* — which is precisely what "Head of" / "Lead" targets screen for.

**[RECOMMENDATION — direction]** For the cross-review phase, for each project decide: (a) is the number a *scope* number or an *impact* number, and can an impact number be added truthfully; (b) state role in one unambiguous verb ("Owned…", "Led…", "Contributed to…"); (c) add client (or client type) and year; (d) cut Project 03's "anticipated" sentence or replace with what was actually built/learned.

---

## 5. Ownership and role clarity — summary

**[OBSERVED]** Ownership language across the page, strongest → weakest:
- Strong: "founder of a digital studio", "Led the interior lighting function for a team of five", "Designed and facilitated [the workshop]", "Created and delivered [the] enablement program".
- Medium: "leading GenAI and digital innovation initiatives", "designed", "defined".
- Weak: "Contributed to…", "shaped…", "supported…", "Concept product designed around…".

**[INFERENCE, confidence: high]** A recruiter cannot reliably answer "what has this person *owned*?" from the portfolio. The strongest ownership fact (studio founder) is one clause in About; the strongest people-leadership fact (team of 50, from the CV) is missing entirely.

---

## 6. Business impact and metrics

**[OBSERVED] Every number on the portfolio:** "20+ / 10+ / 5+ / 10+" (stat row), "22 stakeholders" (Project 04), "team of five" (Project 07), "01/02/03…" (list numbering). That is the complete set.

**[OBSERVED]** The CV body contains the only percentage impact figures (≈30% operational-cost reduction, ≈40% time-to-market acceleration, up to ≈40% productivity increase — *medium-confidence read*, figures behind an embedded subset font). **None of these reach the portfolio.**

**[INFERENCE, confidence: high]** This is a major content gap. The portfolio's headline promise is "scalable, **measurable** transformation" and it then shows almost no measures. Either:
- the percentage figures are solid and individually attributable → they belong on the portfolio (hero-adjacent, stat row, relevant projects); or
- they're capability-level aggregates → they need honest framing ("as part of the GenAI capability…") and probably shouldn't be headline claims for an individual.

The cross-review phase must resolve which.

---

## 7. Evidence / credibility

**[OBSERVED] Credibility assets present:**
- Accenture (current) + Accenture Song / Fjord (past) — strong institutional anchors.
- Studio founder — ownership signal.
- Logo wall of 9 brands (see §8).
- 10 certifications/courses (see §9).
- LinkedIn link (nav/contact/footer) → `linkedin.com/in/miguelballesteroszafra`.
- Real contact details (email, phone).

**[OBSERVED] Credibility gaps:**
- No testimonials, references, recommendations, or third-party quotes.
- No links out — no GitHub, no published article/talk, no Behance/Dribbble/ArtStation for the CGI/XR work, no case-study writeups hosted elsewhere, no product demo/video.
- No press, awards, or speaking.
- `og:image` points to `https://mabz.miguel.com/og-image.jpg` — a **non-existent domain** (the site is `mabz-miguel.github.io`). Any link share renders broken — a small but real credibility leak (see `06_TECHNICAL_AUDIT.md`).
- The visual work (hyperreal automotive, XR) is *described* but never *shown* — for someone from a visual background, showing nothing visual is a missed proof opportunity and slightly odd.

---

## 8. Client and brand proof

**[OBSERVED]** `#clients` section: heading "Clients & collaborations" + a scrolling marquee of 9 logos (each duplicated for the loop): **Mercedes-Benz, IKEA, Heineken, Pfizer, Renault, Radisson, Repsol, Codere, Sika.**

| Aspect | Finding |
|---|---|
| Context | **[OBSERVED]** Zero. No indication of which were Accenture engagements vs studio clients vs Fjord, what Miguel did for each, or when. |
| Verifiability | **[INFERENCE]** Only Radisson (Project 04) and SEAT (Project 05, not on the logo wall — inconsistency) connect to a case study. The other 7 brands are unlinked to any described work. |
| Effect | **[INFERENCE]** A logo wall with no context reads as *agency-roster borrowing*. Experienced recruiters discount uncontextualised logo walls, and some read them as a slight overclaim. |
| Heading hedge | **[OBSERVED]** "Clients **& collaborations**" — the "& collaborations" quietly admits some are not direct clients. |

**[RECOMMENDATION — direction]** Either contextualise each logo (role + era, even one line on hover) or reduce to the 2–3 that map to shown work. Resolve the SEAT/logo-wall inconsistency.

---

## 9. Capabilities / skills content

**[OBSERVED]** The portfolio has no dedicated skills/tools list. Skills are implicit in the Capabilities section and the project tags. The **CV** lists: ComfyUI, Claude Code, Stable Diffusion, Flux, Unreal Engine, Unity, Figma, Adobe Creative Suite, Perforce, ftrack, Monday, Confluence, Notion, Microsoft 365 + Copilot, Python (basic, in progress).

**[INFERENCE]** For AI-enablement and AI-ops roles, the concrete tool stack (ComfyUI, Stable Diffusion, Flux, Claude Code, Copilot) is a *differentiator* and a *keyword set* — and it is invisible on the portfolio. **[OBSERVED]** "Python (basic, in progress)" is honest but, paired with the target title "AI Systems Lead", it undercuts that specific claim.

---

## 10. Training / certifications

**[OBSERVED]** `#formation` section, grouped "Strategy & Management" (3, badged "Featured") + "Technical Training" (4):

- Product Manager Certification — ESIC Business & Marketing School — **2025** — Featured
- Google Project Management — Google — **2025** — Featured
- Design Thinking — Universidad Nebrija / Euroinnova — **2025** — Featured
- CRO & Product Designer — Gen/D — (no year)
- UX/UI Advanced — Mr Marcel School — (no year)
- VR/AR/XR Development Expert — U-TAD — (no year)
- Digital Art & Animation — Animum Creativity Advanced School — (no year)

(The CV lists the same set plus "IED Madrid — The Creative Process in Graphic Design", "How Designers Make Decisions", and "C.E.V. — Graphic Art and Advertising", with years that are partly unreadable behind the embedded font.)

| Aspect | Finding |
|---|---|
| Recency clustering | **[OBSERVED]** All three "Featured" certs are dated 2025 and are all management/product/strategy. **[INFERENCE]** To an experienced recruiter this reads clearly as *"actively repositioning from creative/technical toward management in the last year"* — which is honest but signals *transition*, not *established seniority*. |
| Substitute for experience | **[INFERENCE]** Featuring 3 certificates prominently, directly under Capabilities/Projects, risks them being read as *compensating* for missing management track record rather than *reinforcing* it. |
| Inconsistent year display | **[OBSERVED]** 2025 certs show a year; older ones show none — makes the older training look vague/undatable. |
| Value | **[OBSERVED]** The XR/3D training (U-TAD XR Expert, Animum) genuinely supports the differentiated CGI/XR foundation and is currently in the lower, unbadged group. |

---

## 11. CTA and contact copy

**[OBSERVED]** `#contact`:
> Open to the right opportunity
> **Let's Build Better Systems.**
> Currently Assistant Manager at Accenture, leading AI & digital innovation. Open to senior opportunities that genuinely match my profile — Head of Digital Production, Digital Transformation Lead or AI Systems Lead roles where systems thinking, operational design and AI integration are at the core.
> Any industry, any scale — if the challenge is right, let's talk.
> [LinkedIn →] [mabz.miguel@gmail.com] [+34 669 43 26 22] [Download CV]

| Aspect | Finding |
|---|---|
| Placement | **[OBSERVED]** This is the most useful block for a recruiter (title, target roles, availability, CV) and it is dead last. |
| "genuinely match my profile" / "if the challenge is right" | **[INFERENCE]** Reads slightly *gatekeeping* for a candidate actively seeking a move — subtly shifts the frame from "hire me" to "convince me". |
| "Any industry, any scale" | **[INFERENCE]** Signals *openness* but also *lack of focus* — the opposite of the specificity a recruiter needs. |
| Three divergent target titles | **[OBSERVED]** Head of Digital Production / Digital Transformation Lead / AI Systems Lead — three departments, three seniority reads, one of them (AI Systems Lead) mis-signalling engineering. |
| CV delivery | **[OBSERVED]** "Download CV" triggers an ~88 KB base64 data-URI download (`download` attribute present). Works, but the CV is not viewable inline and not linkable/shareable as a URL. |
| Missing | **[OBSERVED]** No location, no notice period, no remote/hybrid/on-site preference, no "best way to reach me". |

---

## 12. Signal-to-noise ratio

**[OBSERVED]** Word budget is spent, in order, on: mood-setting hero → abstract About → 4 methodology cards → 7 project accordions → uncontextualised logo wall → 7 certs → target-role statement.

**[INFERENCE, confidence: high]** Signal-to-noise is **low for a recruiter**:
- **High-noise:** the coined category, the abstract hero sentence, the "N+" stat row, the uncontextualised logo wall, the Capabilities/Projects altitude-duplication, "anticipated a market direction…".
- **Buried signal:** current title, target roles, the CV's percentage outcomes, the team-of-50 leadership fact, the concrete AI tool stack, the dates of anything.
- The page is *long* and *well-crafted* but a recruiter has to read ~80% of it, in the right order, to assemble a classification — and some required facts are only in the CV.

---

## 13. Missing evidence (consolidated)

**[OBSERVED] Not present anywhere on the portfolio:**
1. Current job title above the footer.
2. Any hard business-impact number (the CV's %s never appear).
3. Team size / scope of management (CV: "up to 50 people").
4. Dates on roles, projects, or older certs; any timeline.
5. Client context on 7 of 9 logo-wall brands.
6. Concrete AI/tech tool stack.
7. Visual proof of the CGI/XR work (portfolio of someone from a visual field shows no visuals of that work).
8. Third-party validation (testimonial, recommendation, reference).
9. External links (GitHub, article, talk, ArtStation/Behance, product demo).
10. Location / work-authorisation / remote preference.
11. A single recruiter-oriented primary CTA ("See CV") in the hero.
12. Capability-to-project evidence links.

---

## Summary judgement

**[INFERENCE, confidence: high]** The portfolio is **well-written and visually composed but under-evidenced as a hiring instrument.** It is rich in *claims and methodology* and poor in *proof, specifics, numbers and dates*. Its structure front-loads mood and back-loads the facts a recruiter needs (title, targets, CV, availability). The case studies establish Miguel as a strong **systems designer and facilitator** but do not establish him as someone who has **owned, shipped, scaled, or quantified** outcomes — the exact evidence his three target titles require.

**Highest-leverage content moves (direction only, for cross-review):**
1. Put the current title + a plain value proposition + the CV link in the hero.
2. Surface one hard, honestly-framed impact number early; fix or remove the "N+" stats.
3. Rewrite each project to state role in one verb, add client-type + year, and separate scope numbers from impact numbers.
4. Add a dated career timeline.
5. Contextualise or cut the logo wall.
6. Add the concrete AI tool stack (keyword + differentiator value).
7. Cut Project 03's "anticipated a market direction" sentence.
8. Move certifications below Projects and de-emphasise the 2025 cluster, or reframe them as reinforcement.
