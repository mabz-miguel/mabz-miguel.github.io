# ChatGPT Independent Audit — 03 UX/UI

Status: first-pass independent audit. Claude's audit has not been read.

## Method and limitation

This first pass is based on the current production source structure, copy, responsive CSS and interaction semantics. It can reliably assess information hierarchy, interaction structure, accessibility signals and likely recruiting flow.

A final pixel-level UI judgment still needs rendered desktop/mobile validation. I will not pretend source inspection is equivalent to visually using the site.

## Executive diagnosis

The portfolio has a coherent, deliberate visual system: dark interface, blue accent, large editorial typography, strong spacing, motion and structured sections. It does not look accidental or unfinished.

The main UX/UI issue is **hierarchy serving personal-brand spectacle slightly more strongly than recruiter classification**.

The hero visually gives enormous priority to the name while the professional role is much smaller. For a personal creative portfolio this is defensible; for a job-search portfolio whose current problem is role ambiguity, the hierarchy should work harder to surface *what Miguel is and why he is relevant* before or alongside the visual signature.

## 5-second comprehension test

### What is likely understood quickly
- Miguel Ángel Ballesteros is the person behind the site.
- The site is technology/AI-oriented.
- The presentation is intentional and senior-looking rather than template-like.
- There is a clear route to “Explore my work”.

### What is not yet guaranteed in 5 seconds
- What canonical job role Miguel maps to.
- Whether he is primarily a manager/leader, systems designer, product profile, AI specialist, creative technologist or digital-production expert.
- What his most important business outcome is.

**Result:** visual identity passes; role classification does not yet fully pass.

## 30-second recruiter journey

Current likely flow:

1. Large name / personal identity.
2. “AI-Driven Digital Production Systems”.
3. Abstract value proposition around systems, workflows and AI-enabled solutions.
4. CTA to work.
5. About / capabilities / work / brands / formation / contact.

The sequence is logically sound, but the **information priority inside the hero** can be improved for hiring conversion.

---

## UX findings

### UX-P0-01 — Hero hierarchy over-prioritizes the name relative to role clarity
**Severity:** P0  
**Confidence:** high

**Evidence:**
- `.hero-name` scales up to `14vw` / `14rem`.
- `.hero-role` is `0.7rem`, uppercase.
- The h1 is the three-line name; the professional identity sits below it.

**Hiring impact:** A recruiter already knows whose site they opened. The scarce first-screen attention should disproportionately answer “what does this person do?” and “why should I continue?”

**Direction:** Preserve the distinctive oversized-name aesthetic if desired, but increase the visual and semantic prominence of the role/value proposition. This does not necessarily mean making the role physically larger than the name; it means making it impossible to miss or misclassify.

---

### UX-P0-02 — Information architecture does not yet resolve the role ambiguity created by the hero
**Severity:** P0  
**Confidence:** high

**Evidence:** The next major concept is “Capabilities & Impact”, with categories such as Operational Transformation, Scalable Systems Design, AI Workflow Integration and Product & Experience Systems.

**Hiring impact:** These are valuable capabilities, but they continue describing what Miguel can do rather than categorizing what he should be hired as.

**Direction:** Once a target role is chosen, structure the first screens as:

> role/value proposition → strongest proof → selected case studies → broader capabilities.

Capabilities should support the identity, not be asked to define it.

---

### UX-P1-03 — Interactive capability rows use non-semantic clickable containers
**Severity:** P1  
**Confidence:** high from source

**Evidence:** Capability accordions are implemented as `<div class="cap" data-cap="…">` with a plus icon and cursor interaction rather than semantic `<button>`/accessible accordion controls.

**Impact:** Potential keyboard and assistive-technology friction. It also makes state/expanded semantics less explicit.

**Direction:** Use accessible accordion patterns: button control, `aria-expanded`, `aria-controls`, keyboard focus, visible focus state and programmatic state.

---

### UX-P1-04 — Long capability copy can increase scanning cost
**Severity:** P1  
**Confidence:** medium-high

**Evidence:** Each capability has a substantial explanatory paragraph plus an expandable “What changes” list.

**Hiring impact:** A recruiter often scans rather than reads. Long explanatory capability content before clear case-study evidence can consume attention without increasing conviction.

**Direction:** Shorten top-level capability statements and move deeper explanations behind optional exploration. Use proof links or case references wherever possible.

---

### UX-P1-05 — Brand marquee is useful social proof but likely low-information motion
**Severity:** P1  
**Confidence:** medium-high

**Evidence:** A marquee animation exists and the clients section duplicates brand assets to create a continuous moving track.

**Hiring impact:** Movement attracts attention but the recruiter learns little beyond brand association. It can compete with higher-value evidence.

**Direction:** Keep social proof, but reduce the visual dominance/motion if necessary and make important brands contextual rather than purely decorative.

---

### UX-P1-06 — “Explore my work” is the right primary CTA; project discoverability must remain immediate
**Severity:** P1  
**Confidence:** medium

The current primary CTA links directly to `#projects`, which is strategically correct. Any redesign should protect this short path.

The later review should confirm:
- projects are scannable without interaction overhead,
- project cards reveal role/outcome before a click,
- no horizontal interaction hides important evidence on mobile,
- a recruiter can compare projects quickly.

---

### UX-P2-07 — Motion handling has a good foundation
**Severity:** strength / P2 validation

**Evidence:** The stylesheet includes `@media(prefers-reduced-motion:reduce)` and aggressively reduces animation/transition durations.

**Conclusion:** This is a positive accessibility implementation and should be preserved. The final audit should verify that scripted motion also respects the preference in practice.

---

## UI findings

### UI-P0-01 — Visual seniority is stronger than role seniority
**Severity:** P0  
**Confidence:** medium-high

The interface itself feels deliberately designed: Clash Display + DM Sans, restricted dark palette, strong cyan accent, consistent border/panel language, editorial scale and generous section spacing.

That gives **visual authority**.

However, visual authority cannot compensate for unclear occupational classification. A recruiter can think “this looks senior” while still being unsure whether the candidate is senior as a designer, technologist, product person or manager.

**Direction:** Do not solve this with more polish. Solve it with hierarchy and evidence.

---

### UI-P1-02 — Huge-name treatment may read more like creative-director/personal-brand portfolio than management/product portfolio
**Severity:** P1  
**Confidence:** medium

This is not inherently negative. It gives personality and differentiates the site. But if the target market becomes Project/Program/Product/Operations/AI Transformation management, the balance may need adjustment so the design signals **clarity, systems thinking and evidence** at least as strongly as creative authorship.

**Direction:** Preserve personality, reduce anything that makes the recruiter work to find role, scope or outcomes.

---

### UI-P1-03 — Small uppercase labels can become secondary-information noise
**Severity:** P1  
**Confidence:** medium-high

The system uses many small uppercase labels around `0.64–0.7rem` with tracking. This is visually coherent, but role-critical information should not be encoded only in this secondary typographic treatment.

**Direction:** Reserve micro-label styling for taxonomy/eyebrows. Important role and outcome information needs normal reading priority.

---

### UI-P2-04 — Base palette contrast is generally viable
**Severity:** strength / validation

From the defined tokens:
- `#6b7f91` muted text on `#030507` is approximately 4.93:1.
- brighter body and cyan text have substantially stronger contrast.

This suggests the palette can meet common text-contrast thresholds in many uses. Final rendered validation is still required for exact sizes, opacity combinations and text over layered backgrounds.

---

### UI-P2-05 — Decorative visual layers should not become performance/attention tax
**Severity:** P2

**Evidence:** fixed noise overlay, animated orb, grid, marquee and multiple reveal/keyframe systems.

These create a polished technology aesthetic. The question is not whether they look good but whether they improve the recruiter journey enough to justify their cost.

**Direction:** Keep motion that supports orientation or hierarchy; remove/reduce motion that only repeats the “tech” aesthetic if performance or attention suffers.

---

## Responsive observations from source

The code contains a responsive architecture including hidden desktop/mobile nav variants and fluid typography via `clamp()`. This is a good foundation.

The final rendered audit must specifically test:
- hero name wrapping at 320–430 px,
- hero role readability,
- CTA position above the fold,
- About grid collapse,
- capability accordion touch targets,
- project card stacking/ordering,
- logo marquee speed/overflow,
- contact actions,
- CV download behavior.

These are validation items, not current confirmed failures.

## Accessibility priority list

1. Convert interactive non-semantic capability rows into accessible controls.
2. Verify visible keyboard focus across nav, CTAs, projects and accordions.
3. Verify project interactions do not depend on hover.
4. Preserve reduced-motion support.
5. Validate heading order and landmarks.
6. Validate alt text for meaningful project imagery; decorative graphics should be hidden appropriately.
7. Check color/opacity combinations in rendered state.

## What should be protected

- Strong visual identity.
- Restricted design system rather than random styling.
- Primary CTA to work.
- Responsive typography foundation.
- Reduced-motion CSS support.
- Clear use of sections and consistent panel/border language.

## UX/UI conclusion

The site does **not** need a generic visual modernization. It already has a credible contemporary identity.

The redesign opportunity is more strategic:

> Rebalance the interface from “strong personal technology portfolio” toward “high-clarity recruiting interface for a senior person who leads meaningful AI-enabled production transformation.”

The most important UI change may ultimately be content hierarchy rather than aesthetics.