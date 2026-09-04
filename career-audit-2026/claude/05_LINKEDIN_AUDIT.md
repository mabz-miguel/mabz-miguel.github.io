# 05 — LinkedIn Audit

## 0. Access limitation (read this first)

**[OBSERVED]** The only LinkedIn artefact available to this audit is the profile URL, referenced three times in `index.html` (nav, contact, footer):

`https://www.linkedin.com/in/miguelballesteroszafra`

**[OBSERVED]** A direct fetch of that URL returns **HTTP 999** — LinkedIn's standard anti-scraping block for unauthenticated automated requests. No profile content (headline, About, experience, skills, recommendations, activity) is retrievable.

**[OBSERVED]** There is **no LinkedIn PDF export and no screenshots** anywhere in the repository (`git ls-files` shows only `index.html` and the audit markdown files). `00_CONTEXT.md` §"LinkedIn limitation" explicitly anticipates this and states: *"A complete audit should therefore use a LinkedIn PDF export and/or screenshots of the relevant sections."*

**[INFERENCE]** A substantive LinkedIn content audit **cannot be completed in this phase.** What follows is: (1) what can still be assessed from available evidence; (2) the exact artefacts needed to finish; (3) a ready-to-use checklist for when they are provided.

---

## 1. What can be assessed now

### 1.1 The vanity URL
**[OBSERVED]** `/in/miguelballesteroszafra` — clean, full-name, custom slug. **[INFERENCE]** Good: professional, memorable, no digits/hashes. No action needed.

### 1.2 URL consistency across channels
**[OBSERVED]** The same URL appears in the portfolio nav, the `#contact` block ("LinkedIn →"), and the footer ("LinkedIn Spain"), and in the CV header. **[INFERENCE]** Consistent and easy to find — positive. Minor: the footer label "LinkedIn Spain" is odd phrasing (see `02`/`06`); "LinkedIn" alone is clearer.

### 1.3 External indexability
**[OBSERVED]** `00_CONTEXT.md` notes the public profile "can be partially indexed externally." **[UNCERTAIN]** Whether Miguel's profile is set to public, and how much is visible logged-out, could not be checked (999 block). This matters: a recruiter often first meets the profile via a Google result or a logged-out view.

### 1.4 Inferred risks by analogy with the portfolio and CV
**[INFERENCE, confidence: medium]** LinkedIn profiles by the same person usually inherit the same positioning decisions. The issues found in `01`–`04` are therefore *likely* to recur on LinkedIn and should be checked specifically:
- Headline likely uses the coined category ("AI-Driven Digital Production Systems" / "AI Transformation & Digital Production Systems") rather than a searched job title + level → **recruiter-search (LinkedIn Recruiter / boolean) visibility risk**.
- "About" likely opens abstractly rather than with role + scope + outcome.
- Experience bullets likely responsibility-led with few metrics (mirrors the CV).
- The `≈30/40/40%` figures and "team of up to 50" may or may not appear — needs checking for consistency.
- Skills section / endorsements, recommendations, and "Featured" items are unknown and are exactly where LinkedIn can *add* proof the portfolio lacks.

---

## 2. Artefacts required to complete this audit

Provide **either**:

- **A) LinkedIn "Save to PDF" export** (Profile → *Resources* / *More* → *Save to PDF*) — captures headline, About, Experience, Education, Licenses & Certifications, Skills. Fastest single artefact.

**and/or**

- **B) Screenshots (logged-in, full-length)** of each section:
  1. Top card — profile photo, background banner, **headline**, location, "Open to work" status, follower/connection count, custom button.
  2. **About** (expanded, full text).
  3. **Featured** (what's pinned, if anything).
  4. **Experience** — every role, expanded, with bullets, media, and dates.
  5. **Education** and **Licenses & certifications**.
  6. **Skills** — full list + which are endorsed / top-3 pinned.
  7. **Recommendations** — received and given (count + content).
  8. **Activity** — recent posts/comments (last ~3 months), or confirmation it's inactive.
  9. **Services** page, if enabled.

**Also useful:**
- A **logged-out view** screenshot (open the profile in a private window) — shows what a cold recruiter/Google visitor sees.
- Confirmation of **profile visibility settings** (public on/off) and **"Open to work"** configuration (recruiters-only vs public badge).
- The profile's **"Skills" search terms** and whether **Creator mode** is on.

---

## 3. Checklist to apply once artefacts are provided

### 3.1 Headline (the highest-leverage field)
- [ ] Does it contain a **recognised job title** a recruiter would search ("Manager", "Lead", "Head of", "Consultant", "AI/GenAI", "Operations", "Digital Production")?
- [ ] Does it state **seniority** and **domain**, not just a coined phrase?
- [ ] Is it consistent with the CV headline and the portfolio — or deliberately differentiated per channel (allowed per `00_CONTEXT.md` §5)?
- [ ] Is the current employer visible (Accenture)?
- [ ] ≤ ~220 chars, front-loaded with the most-searched terms?

### 3.2 About
- [ ] First 2 lines (the part shown before "…see more") carry role + scope + a proof point?
- [ ] Contains the quantified outcomes (and are they framed consistently with the CV — personal vs capability-level)?
- [ ] States what roles he's targeting / open to?
- [ ] Keyword coverage for LinkedIn Recruiter (GenAI, AI adoption, workflow, operations, enablement, digital production, transformation)?
- [ ] First person, readable, not a keyword dump?

### 3.3 Experience
- [ ] Every role has a clear title, dates, and location/format (remote/hybrid).
- [ ] Accenture role: is the **title** the internal grade ("Assistant Manager") or a functional title? Is what he "leads" specified?
- [ ] Bullets accomplishment-led with metrics — or the same responsibility-led text as the CV?
- [ ] Is the pre-2016 history present (the portfolio omits it; LinkedIn usually shouldn't)?
- [ ] Media attached (decks, links, the portfolio, project visuals)?
- [ ] Two Accenture entities shown as continuity, not fragmentation?

### 3.4 Featured
- [ ] Is the **portfolio** pinned here? (It should be — highest-value link.)
- [ ] Any post, deck, article, or case study pinned?
- [ ] Or is Featured empty (missed opportunity)?

### 3.5 Skills
- [ ] Top 3 pinned skills = the target positioning (e.g. "Generative AI", "Digital Transformation", "Operations Management")?
- [ ] Are the differentiating tools listed (ComfyUI, Stable Diffusion, etc.)?
- [ ] Endorsement counts on the key skills (social proof)?
- [ ] Any stray legacy skills (pure 3D/art) crowding the top and pulling positioning backward?

### 3.6 Recommendations
- [ ] How many received? From whom (managers? clients? peers?)?
- [ ] Do they speak to leadership/ownership/impact — the exact gaps in the portfolio/CV?
- [ ] Any given (reciprocity signal)?
- [ ] **If zero or few: this is a priority action** — recommendations are the cheapest credible third-party proof and neither the portfolio nor the CV has any.

### 3.7 Certifications
- [ ] Do the LinkedIn "Licenses & certifications" match the portfolio/CV list and dates?
- [ ] Are the 2025 management certs (Google PM, ESIC, Design Thinking) present with credential links?

### 3.8 Top card / visual identity
- [ ] Professional headshot consistent with the portfolio portrait?
- [ ] Background banner used deliberately (not default) and consistent with the portfolio's visual language?
- [ ] "Open to work" — set to **recruiters-only** (discreet) or **public green badge** (visible but can read as "actively job-hunting")? Deliberate choice needed.
- [ ] Location and connection count (>500 preferred for credibility).

### 3.9 Consistency matrix (fill once data is available)
| Field | LinkedIn | CV | Portfolio | Aligned? |
|---|---|---|---|---|
| Job title / headline | ? | coined category | coined category | ? |
| Current grade/title | ? | "Assistant Manager" (unclear in doc) | "Assistant Manager" | ? |
| Years of experience | ? | not stated | 20+ | ? |
| % impact figures | ? | ≈30/40/40 | absent | ? |
| Team scope | ? | "up to 50" | absent | ? |
| Pre-2016 roles | ? | present | absent | ? |
| Target roles stated | ? | no | yes (Contact) | ? |
| Tool stack | ? | present | absent | ? |

### 3.10 Recruiter-SEO / discoverability
- [ ] Run the likely boolean a recruiter would use for each target role; does the profile plausibly surface?
- [ ] Are the target-role *titles* (not just skills) present somewhere in headline/About/Experience so title-filtered searches match?
- [ ] Location and "open to" set so that recruiter filters include him?

---

## Summary judgement (LinkedIn)

**[OBSERVED]** Cannot be completed this phase — no PDF export or screenshots exist, and unauthenticated access is blocked (HTTP 999), exactly as `00_CONTEXT.md` predicted.

**[INFERENCE, confidence: medium]** Based on cross-channel patterns, the most probable LinkedIn issues are: (1) a headline built on the coined category rather than searchable titles → **reduced visibility in recruiter search**, which is the single biggest LinkedIn risk because it happens before any human reads the profile; (2) an abstract About opener; (3) responsibility-led experience bullets mirroring the CV; (4) likely **thin or absent recommendations**, which is the highest-value gap to close because it's the one credible third-party proof missing from *all* channels; (5) unknown Featured section that could cheaply add proof.

**Priority actions the moment artefacts arrive:**
1. Audit and rewrite the **headline** for recruiter-search + seniority.
2. Check/*request* **recommendations** (target: 3–5 from managers/clients speaking to ownership and impact).
3. Verify the **Featured** section pins the portfolio + best proof.
4. Run the **consistency matrix** (§3.9) and resolve every misalignment, deciding per-channel depth deliberately.
5. Confirm **"Open to work"** and **public visibility** settings are intentional.

**Confidence:** Low on specifics (no data). High only on the access limitation and the URL-level observations.
