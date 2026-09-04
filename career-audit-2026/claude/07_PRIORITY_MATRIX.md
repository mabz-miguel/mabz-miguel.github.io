# 07 — Consolidated Priority Matrix

Consolidates findings from `01`–`06` into one prioritised list.

**Severity scale (per `CLAUDE_MASTER_PROMPT.md`):**
- **P0** — likely to reduce interview conversion / creates fundamental confusion.
- **P1** — materially weakens proof, usability, or perceived seniority.
- **P2** — polish / optimisation / maintainability.

**Surface:** positioning · content · UX · UI · CV · LinkedIn · technical
**Confidence:** high / medium / low
**Recommended direction is direction only** — no final copy, design, or code. Nothing is implemented in this phase (`00_CONTEXT.md` §Implementation rule). All recommendations to be validated against real job descriptions before action (`00_CONTEXT.md` §6).

ID prefixes: `POS` positioning · `CON` content · `UX` · `UI` · `CVX` CV · `LI` LinkedIn · `TEC` technical.

---

## P0 — likely to reduce interview conversion / fundamental confusion

| ID | Surface | Evidence (observed) | Why it matters for hiring | Recommended direction | Confidence |
|---|---|---|---|---|---|
| **CVX-1** | CV / technical | CV PDF ships text through an embedded subset font with non-standard encoding; naïve text extraction and copy-paste return scrambled characters (`04` §0, `06` §3). | If an ATS/résumé parser reads glyph codes instead of Unicode, the CV ingests as gibberish/near-empty → **automatic rejection regardless of content**. Also breaks a recruiter copying details into email/ATS. Could be silently costing interviews now. | **Verify first:** run the PDF through a real ATS/parser + a plain copy-paste test. If confirmed, re-export so text is standard selectable Unicode; distribute as a normal `.pdf` file at a stable URL. | medium-high |
| **POS-1** | positioning | Hero role, `<title>`, and CV headline all use the coined category "AI-Driven / AI Transformation & Digital Production Systems" (`01` §1, `02` §1, `04` §2). | Maps to **no job-board title, no ATS filter, no recruiter boolean, no seniority band**. The recruiter must do the classification the page should do — and the fallback read ("creative generalist who added AI") drops him into a crowded, lower-seniority pool. | Choose one primary spine (evidence points hardest at **AI enablement / AI operations**, with digital-production leadership secondary). Rebuild hero, `<title>`, About opener, CV headline and the primary CTA around a **recognised role + level + domain**. | high |
| **POS-2** | positioning / UX | Current job title appears only in `#contact` ("Assistant Manager at Accenture"); the three target roles appear only in `#contact` — the last section. Hero and About state no recognised role (`01` §1, §8; `03` A2–A3). | A recruiter scanning for 30 seconds never reaches the one block that says what he is and what he wants. Decision-critical info is structurally hidden. | Bring current title + a plain "I am a ___ who does ___ for ___" line + the target direction into the hero/About. Add "CV" to nav + mobile menu. | high |
| **POS-3** | positioning | Page asks to be read as "systems & transformation leader" / "Head of" candidate; evidence = grade "Assistant Manager" (mid-level), case studies that are MVPs / concepts / facilitation, verbs "designed / contributed / shaped / supported" (`01` §5–§7, `02` §4). | The gap between claimed and demonstrated seniority reads as **over-claiming** → credibility doubt across the whole profile, and still no clear level to slot him at. | Align the claim to the evidence: position at the level the proof supports (Manager / Senior Manager / Lead) for the primary spine; treat "Head of / Director" as the *next* step, earned by the strengthened proof, not asserted now. | high |
| **POS-4** | positioning | `#contact`: "Head of Digital Production, Digital Transformation Lead or AI Systems Lead" — three departments, three seniority reads; "AI Systems Lead" + CV "Python (basic, in progress)" (`01` §2, §9; `04` §8–§9). | Three divergent targets tell a recruiter he doesn't know what he is. "AI Systems Lead" attracts ML-engineering screens he can't pass. | Pick **one** primary target + at most one adjacent. Drop "AI Systems Lead". Treat "Digital Transformation Lead" as a stretch/future target, not a current claim. | high |
| **CON-1** | content | Hero promises "scalable, **measurable** transformation"; the portfolio contains almost no outcome numbers. The CV's only impact figures (≈30% cost / ≈40% time-to-market / up to ≈40% productivity) and the "team of up to 50" scope fact are **absent from the portfolio** (`02` §2, §6; `04` §11). | A hiring profile with claims and no proof underperforms against candidates who show results. The stronger evidence (CV) is hidden behind the weaker surface (portfolio). | Decide per figure: is it personally attributable or a capability aggregate? Surface the honestly-framed ones early (hero-adjacent / relevant projects). Add the leadership-scope fact. Fix or drop the unbacked "N+" stats. | high |
| **UX-1** | UX / technical | All 7 case-study panels are `max-height:0;overflow:hidden` and their `tabindex` is **added by JS**; 3 of 4 capability panels are click-only. On mobile the desktop nav is `display:none`. So **JS failure ⇒ case studies unreadable + capabilities partly unreadable + no mobile navigation** (`03` A8, A12; `06` §7, §10, §13/T4). | The substance of the portfolio disappears for a non-trivial minority of sessions (corporate proxies, CSP, extensions, script errors, slow networks). Even with JS, impacts require 7 separate clicks and can't be skimmed. | Render case-study content visible by default; use JS only to *enhance* (collapse/expand). Make interactivity semantic (`<button>` + `aria-expanded`) with `tabindex` in HTML. Ensure mobile nav degrades without JS. | high |

---

## P1 — materially weakens proof, usability, or perceived seniority

| ID | Surface | Evidence | Why it matters | Recommended direction | Confidence |
|---|---|---|---|---|---|
| **CON-2** | content | 7-question test: role/ownership unclear on 5 of 7 projects; the two brand-prestige projects say "Contributed to the experience architecture…" (SEAT) and "Concept product designed around…" (Try-On) (`02` §4). | "What did he own?" is the question that decides interviews, and it's the hardest to answer on the site. | Per project, state role in one unambiguous verb (Owned / Led / Co-led / Contributed to), name the client or client-type, add the year. | high |
| **CON-3** | content | Stat row "20+ / 10+ / 5+ / 10+"; "10+ End-to-end systems designed & delivered" (only ~5–7 shown, several MVP/concept); "5+ Industries transformed" (`02` §2). | Round, vague, unbacked numbers read as marketing and *reduce* credibility. | Replace with a small number of specific, verifiable facts, or remove the row. | medium-high |
| **CON-4** | content | `#clients`: "Clients & collaborations" + marquee of 9 brands (Mercedes-Benz, IKEA, Heineken, Pfizer, Renault, Radisson, Repsol, Codere, Sika), no role/era context; only 2 map to case studies; SEAT is a project but not on the wall (`02` §8). | Uncontextualised logo walls are discounted by experienced recruiters and can read as borrowed credibility. | Contextualise each logo (one line: role + era) or reduce to the few that map to shown work. Resolve the SEAT inconsistency. | medium |
| **CON-5** | content | Project 03: "Anticipated a market direction later validated by mainstream retail adoption." | Unfalsifiable self-praise; invites scepticism about every other claim. | Replace with what was actually built, learned, or decided; or cut. | high |
| **CON-6** | content | `#formation`: 3 management certs (Google PM, ESIC Product, Design Thinking), all dated 2025, all badged "Featured", placed prominently (`02` §10). | To an experienced recruiter this reads as "repositioning in the last year" and risks looking like compensation for a missing management track record. | Move certifications below Projects; de-emphasise the 2025 cluster or reframe as reinforcement of demonstrated work; give older technical training visible dates. | medium |
| **CON-7** | content | No testimonials, recommendations, references, or third-party quotes anywhere on portfolio or CV (`02` §7). | Third-party validation is the cheapest credible proof and it's entirely absent. | Add 2–3 short attributed quotes (manager / client / peer) speaking to ownership and impact. Coordinate with LinkedIn recommendations (LI-2). | high |
| **CON-8** | content | Concrete AI tool stack (ComfyUI, Stable Diffusion, Flux, Claude Code, Copilot) is in the CV only, not the portfolio (`02` §9, `04` §8). | It's both a differentiator and a keyword set for AI-enablement roles — invisible where recruiters look first. | Add a compact, honest capabilities/tools block to the portfolio. | high |
| **CVX-2** | CV | CV headline = coined category + a comma-separated **keyword-stuffing block** (`04` §2, §9). | No recognised title/level for recruiter or ATS boolean search; keyword blocks are down-weighted by modern ATS and read poorly to humans. | Headline = role + level + domain. Dissolve the keyword block into real accomplishment bullets. | high |
| **CVX-3** | CV | Exactly one quantified accomplishment (Role 1, hedged "contributing to", capability-level); Roles 2–4 (~13 years) have zero metrics; Role 1 bullets 1 ("Led … digital transformation") and 2 ("Contributed … support team leads") conflict on leader vs contributor (`04` §5–§6). | Leadership roles screen on owned, quantified outcomes and consistent framing; the CV supplies neither. | Add truthful metrics/scope where they exist (adoption, hours saved, headcount, markets, project count). Resolve the leader/contributor framing to one consistent story. | high |
| **CVX-4** | CV / consistency | Current title/grade is ambiguous in the reconstructed CV; portfolio says "Assistant Manager" (Contact) and "leading … initiatives" (About) (`04` §4, §11). | Recruiters and ATS key on the current title; ambiguity here undermines every downstream search and the credibility of the "leading" claim. | State the current title unambiguously and identically across CV, portfolio, and LinkedIn; specify concretely what is "led". | medium |
| **UX-2** | UX / technical | **No `:focus` / `:focus-visible` CSS anywhere**; `role=` count in document = 0; capabilities & project rows are `<div>`s; capability panels keyboard-inoperable (`03` A12; `06` §7). | WCAG 2.4.7 failure + broken keyboard operation. The accessibility-literate audience Miguel targets notices immediately → credibility hit. | Add visible focus styles; convert disclosures to real `<button>` widgets with `aria-expanded`; make all interactive content keyboard-operable. | high |
| **UX-3** | UX | CV absent from nav and mobile menu; no "View CV" CTA; CV delivered as a forced ~88 KB base64 download, not viewable/shareable (`02` §11; `03` A4, A10). | The recruiter's most likely next action is unsupported until the final section and is friction-heavy. | Put a "CV" link in the nav + mobile menu + hero; serve as a real PDF that opens inline and has a shareable URL. | high |
| **UX-4** | UX | Decision-critical section (Contact) is last; no career timeline anywhere; evidence layer isn't scannable (impacts hidden in accordions; `.pr-short` hidden on mobile) (`03` A2–A7). | High cognitive load; the recruiter must assemble the positioning themselves, in the right order, partly from the CV. | Reorder so title/proposition/proof/CV are reachable in the first 1–2 viewports; add a dated timeline; make ≥1 impact visible without a click. | high |
| **UI-1** | UI | Visual language ("Portfolio 2026" eyebrow, name-as-hero, dark showcase aesthetic, project thumbnails over results, Education as a peer section) reads as "senior creative IC / boutique studio" (`03` B9–B10). | It argues visually for a more junior, different job than the leadership/transformation roles targeted. | Shift ~20% toward "operator/leader" cues (timeline, outcomes, scope, stakeholder language) without losing the craft. | medium-high |
| **UI-2** | UI | `--muted #6b7f91` on `#030507` ≈ 4.6:1 (fails AA for normal text) used on small secondary copy; base font 15px; microcopy 9–13px uppercase + letter-spaced (`03` B4; `06` §7). | Readability cost (esp. mobile) + visible AA failures for a UX-literate audience. | Raise `--muted` to meet AA at the sizes used; lift base to 16px; enlarge the smallest microcopy. | medium-high |
| **TEC-T2** | technical / UI | Verified: the Google Fonts request the page makes returns `@font-face` for **DM Sans only** — "Clash Display" (used for the hero name + every `<h2>` + nav logo + contact headline) is not a Google Fonts family and never loads; falls back to `sans-serif` (`03` B2; `06` §5). | Every heading renders in generic Arial/Helvetica in production — a direct hit to the design-craft credibility the portfolio relies on. Cheapest high-impact fix on the site. | Self-host Clash Display (Fontshare) or choose a hosted display face; self-host DM Sans too (removes render-blocking third party + GDPR nit). | high |
| **TEC-T3** | technical | `og:image` = `https://mabz.miguel.com/og-image.jpg` — wrong domain (site is `mabz-miguel.github.io`); file 404s; `og:url` absent (`06` §8). | Every shared link (Slack, LinkedIn, WhatsApp, email preview) renders a broken/blank card — bad first impression before the page opens. | Fix the URL; add a real 1200×630 share image (name + title); add `og:url`. | high |
| **LI-1** | LinkedIn | Cannot verify (HTTP 999, no export). By cross-channel pattern, the headline likely uses the coined category rather than searched titles (`05` §1.4, §3.1). | LinkedIn Recruiter / boolean search is upstream of every other funnel step; a non-searchable headline means recruiters never find him. | Obtain the profile export/screenshots; rewrite the headline for recruiter-search + seniority; run the consistency matrix (`05` §3.9). | medium |
| **LI-2** | LinkedIn | Cannot verify; recommendations are absent from portfolio and CV and are commonly thin on LinkedIn too (`05` §1.4, §3.6; `02` §7). | Recommendations are the one credible third-party proof missing from *all* channels; leadership hires weight them heavily. | Once artefacts arrive, audit; target 3–5 recommendations from managers/clients speaking to ownership and impact. | medium |
| **TEC-T6** | technical / UX | ~600 KB (mostly inline base64 images + the CV) downloaded on every visit, all in the critical path; no lazy-loading possible with data URIs (`06` §2). | Slow first paint on poor/throttled/corporate connections → drop-off before the page is usable. | Externalise images to responsive files, lazy-load below-the-fold, serve the CV as a separate cacheable file. | high |

---

## P2 — polish / optimisation / maintainability

| ID | Surface | Evidence | Recommended direction | Confidence |
|---|---|---|---|---|
| **TEC-T7** | technical | No favicon / `rel="icon"` — default globe in every tab & bookmark (`06` §8). | Add a favicon (initials or mark). | high |
| **TEC-T5** | technical / a11y | No `<main>`; no skip link; `<h2>`s non-descriptive ("Who I Am"); mobile menu is a `<div>` with no focus trap / background not `inert` (`06` §6; `03` A4). | Add `<main>` + skip link; give sections descriptive headings; trap focus + `inert` background in the mobile menu. | high |
| **TEC-T9 / UI-3** | technical / UI | `prefers-reduced-motion` only shortens durations; 4 infinite animations (`pulse`, `marquee`, `blink`, `scrollLine`) keep looping (`03` A14; `06` §7). | Use `animation:none` for infinite decorative motion under the media query. | high |
| **TEC-T8** | technical / privacy | Personal Gmail + personal mobile as plain-text `mailto:` / `tel:` (`06` §11). | Miguel's decision: dedicated job-search alias, obfuscation, or contact form; reconsider publishing the mobile. | high |
| **TEC-SEO** | technical | No `<link rel="canonical">`, no `og:url`, no JSON-LD `Person` schema, no sitemap/robots (`06` §8). | Add canonical + `og:url`; add a `Person` JSON-LD block (`jobTitle`, `worksFor`, `alumniOf`, `sameAs:[LinkedIn]`). | medium |
| **TEC-ARCH** | technical | Single 942-line file with ~550 KB inline base64 → unreadable diffs, hard to edit safely (`06` §1, §9). | Externalise CSS/JS/images/CV to files; keep the no-framework, no-build simplicity. Matters because the site now needs repeated positioning edits. | high |
| **TEC-DOM** | technical | Custom domain never configured (evidence: `mabz.miguel.com` in `og:image`); `*.github.io` reads slightly hobbyist for a senior candidate (`06` §8). | Cost note: register a custom domain (~€10–15/yr), point GitHub Pages at it. Miguel's call. | medium |
| **TEC-CLEAN** | technical | Leftover `<span class="vid-badge" style="display:none">`; `--lime` custom prop is actually sky-blue; `active=2` hard-coded in the capabilities script (`06` §9, §12). | Remove dead node; rename token; derive default active state from markup. | high |
| **UI-4** | UI | SEAT is a project but not on the logo wall; most logo-wall brands aren't projects (`03` B5; `02` §8). | Make the client set and the project set consistent. | high |
| **UI-5** | UI / content | Zero imagery of the actual CGI / XR / hyperreal work the copy describes (`02` §7; `03` B6). | For a candidate from a visual field, show a small amount of the visual work (or link ArtStation/Behance). | medium |
| **CVX-5** | CV | "Python (basic, in progress)" listed as a skill/keyword; "English B2" self-rating (`04` §8, §9, §11). | Deliberate keep/reframe decision per item; "Python basic" surfaces him in searches for roles he can't do. | medium |
| **CON-9** | content | "Portfolio 2026" hero eyebrow will read as stale in 2027 (`02` §1; `03` A1). | Drop the year or make it evergreen. | high |
| **CON-10** | content | Footer link labelled "LinkedIn Spain" (`02` — footer; `05` §1.2). | Label it "LinkedIn". | high |
| **UX-5** | UX | Accordion state not in URL — case studies can't be deep-linked/shared; back button doesn't close panels (`03` A4, A8). | Reflect open panel in the URL hash. | medium |
| **TEC-FONTS-GDPR** | technical / privacy | Google Fonts loaded per-visit exposes visitor IP to Google (EU grey area) (`06` §5, §11). | Self-hosting fonts (TEC-T2) resolves this too. | medium |

---

## Top 10 issues most likely to block or reduce interviews

1. **CVX-1 — the CV may not survive ATS parsing** (font-encoding). Verify immediately; if confirmed it is silently costing interviews. *(P0)*
2. **POS-1 — the coined category means recruiters can't classify or find him** — no searchable title, no seniority band. *(P0)*
3. **POS-3 — claimed seniority outruns the evidence** → over-claim read + still no clear level to interview him for. *(P0)*
4. **CON-1 — no proof of business outcomes on the portfolio**, and it hides the CV's only numbers and the team-of-50 fact. *(P0)*
5. **POS-2 — the current title and the target roles are buried in the last section**; the hero has no role at all. *(P0)*
6. **POS-4 — three divergent target titles**, one ("AI Systems Lead") actively mis-signalling engineering. *(P0)*
7. **CON-2 — case studies don't establish ownership** ("Contributed to…" on the prestige projects); the "what did he own?" question is the hardest to answer. *(P1)*
8. **UX-1 — case-study substance is hidden and JS-gated**; mobile nav dies without JS. Core content unreachable for a real slice of visitors. *(P0)*
9. **LI-1 — the LinkedIn headline is probably not built for recruiter search** — upstream of the entire funnel (needs verification). *(P1)*
10. **TEC-T2 + TEC-T3 — Arial headings in production + a broken social-share card** — two craft/first-impression hits that undercut a design-credibility profile. *(P1)*

## Top 5 strengths that should be protected

1. **Genuinely differentiated substance.** Operationalising GenAI inside a global consultancy — GenAI hub contribution, a delivered ComfyUI enablement programme, AI-assisted QA and estimation systems — sitting on top of a rare creative / XR / hyperreal-CGI foundation. Few competitors have this combination. Protect it by making it the spine, not one item in a list.
2. **A disciplined, coherent visual design system.** Consistent components, restrained palette, confident typographic scale, tasteful and consistent motion. Real craft — worth preserving through any repositioning (once the display font actually loads).
3. **The Capabilities section's writing.** The "What changes" bullets are specific and outcome-shaped ("Planning becomes predictable — not dependent on who's in the room"); they show a clear, senior point of view on *how* he works. Keep the voice; anchor it to evidence.
4. **Real ownership signals exist.** Studio founder with "full responsibility for scope, quality, timelines and client delivery"; a concrete people-leadership example (interior-lighting team of five, onboarding + quality); a 22-stakeholder facilitation. Small but true — build on them, don't inflate them.
5. **A clean, durable technical and identity foundation.** No dependencies, no trackers, privacy-clean, cheap to host, fast to change; a clean LinkedIn vanity URL (`/in/miguelballesteroszafra`); consistent contact details across channels. Good instincts to keep.

## Questions that cannot be answered from current evidence

**About the candidate (needed to finish positioning):**
1. What is Miguel's **exact current job title / grade**, and what does he **concretely lead** — a team (how many reports?), a workstream, or a contribution to the GenAI hub?
2. Are the **≈30% / ≈40% / ≈40%** figures his **personally attributable** impact or **capability-level aggregates**? What is the baseline, timeframe, and measurement method?
3. "**Coordinated multidisciplinary teams of up to 50 people**" — managed with authority, or coordinated within a project? Direct reports ever?
4. The **digital studio**: how many years, how many clients, what scale/revenue, why did it end?
5. For the **logo-wall brands** — which are direct client work, which are Accenture-account, which are "collaborations", and in which era?
6. **Which of the three target roles does Miguel actually want most?** This decision drives the entire repositioning and cannot be made for him.
7. **Location / work authorisation / remote-hybrid-onsite preference / relocation** willingness, and **target market(s)** (Spain, EU, UK, global-remote)?
8. Is **English B2** current and accurate, and is it sufficient for the markets the target roles sit in?
9. Are there **NDA / client-confidentiality constraints** that prevent naming clients or citing metrics? (Would explain — and partly excuse — the vagueness, and changes the recommendations.)
10. **Compensation / seniority band** he would accept — affects whether "Manager/Lead" vs "Head of" framing is even the right fight.

**About the artefacts (needed to finish the audit):**
11. **LinkedIn** — entire content: headline, About, Experience bullets, Featured, Skills (+ endorsements), Recommendations (count + content), Activity, visibility settings, "Open to work" configuration. (Provide PDF export or full screenshots — `05` §2.)
12. **The CV** — a plain-text or properly-encoded copy to confirm this audit's reconstruction, exact dates/months, whether it is genuinely one page, and whether any section is truncated.
13. **Real ATS parse result** for the current CV (the CVX-1 verification).
14. **Real performance data** — Lighthouse / Core Web Vitals on mobile and desktop; real-device behaviour of the accordions and marquee on a low-end phone.

---

## Cross-review handoff note

This is Claude's independent first pass, produced without reading `career-audit-2026/chatgpt/`. Points of likely disagreement to examine in cross-review: (a) whether the primary spine is "AI enablement/operations" vs "digital production leadership" vs "digital transformation"; (b) whether the coined category is a fatal flaw or a recoverable brand; (c) how aggressively to surface the ≈30/40/40% figures given the attribution uncertainty; (d) whether the single-file architecture should be kept. Disagreement here is expected and useful (`00_CONTEXT.md` §Independent-review rule).
