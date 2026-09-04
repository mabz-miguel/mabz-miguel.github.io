# 03 — UX / UI Audit

The site is evaluated as a **recruitment product**: its job is to let a recruiter or hiring manager classify Miguel, judge his level, and take the next step (read CV / contact) with minimum friction. Evidence tags: **[OBSERVED] / [INFERENCE] / [UNCERTAIN] / [RECOMMENDATION]**.

Implementation facts referenced here are cross-checked in `06_TECHNICAL_AUDIT.md`.

---

# PART A — UX

## A1. 5-second comprehension test

**[OBSERVED]** In the first viewport a visitor sees: nav ("MABZ" + 5 section links), "Portfolio 2026", the name in very large type, "AI-Driven Digital Production Systems", the one-sentence descriptor, and two CTAs ("Explore my work →", "Get in touch").

**[INFERENCE, confidence: high]** After 5 seconds the visitor can state the *theme* ("AI + systems + operations, some kind of senior designer/consultant") but **cannot state**: the job title, the seniority band, the industry, whether he builds or advises, or whether he manages people. Every hero noun is abstract (see `02` §1). The test is **partially passed** — mood transfers, classification does not.

## A2. 30-second recruiter journey

**[OBSERVED]** Natural scroll path: Hero → About (+ stat row) → Capabilities (4 cards) → Projects (7 collapsed rows) → Clients (logo marquee) → Education (7 certs) → Contact.

**[INFERENCE, confidence: high]** Within 30 seconds a scanning recruiter reaches About and the stat row, and probably the top of Projects. In that time they learn: Accenture + GenAI + Marketing Operations, 20+ years, ex-studio-founder, ex-XR. They do **not** reach:
- the current job title and the three target roles (Contact — last section);
- any hard business outcome (none exist on the page);
- the CV (only in Contact).

**[OBSERVED]** The case-study *substance* is behind a click each — 7 accordions collapsed by default with the instruction "Click any project to explore context, problem, system and impact." A 30-second visitor sees 7 project *titles* and *tags*, not a single project *impact*.

**[INFERENCE]** The journey front-loads atmosphere and back-loads decision-critical facts. The recruiter's three key questions (what level? what role? proof?) are answered late, weakly, or not at all.

## A3. Information architecture

**[OBSERVED]** Single page, 7 anchored sections, sticky top nav with scrollspy (`IntersectionObserver` toggles `.active` on nav links). No `<main>` landmark, no separate pages, no `/cv` route, no per-project URLs.

| Issue | Evidence | Consequence |
|---|---|---|
| Decision-critical section is last | **[OBSERVED]** `#contact` holds title + targets + availability + CV and sits after everything else. | **[INFERENCE]** Recruiters who don't scroll to the end never see the clearest positioning content. |
| CV not in nav | **[OBSERVED]** Nav = About / Capabilities / Projects / Education / Contact. No "CV". | **[INFERENCE]** The fastest artefact for a recruiter is 5 scroll-lengths away and not signposted. |
| Capabilities ≈ Projects | **[OBSERVED]** Both describe the same body of work at different altitudes, with no cross-links. | **[INFERENCE]** Length without added proof; reader does the linking. |
| No timeline / chronology | **[OBSERVED]** Roles exist only as prose in About; nothing is dated. | **[INFERENCE]** Recruiter can't reconstruct the career shape without opening the CV. |
| Education = its own top-level section | **[OBSERVED]** 7 certs get a full section between Projects and Contact. | **[INFERENCE]** Over-weights training relative to delivery evidence (see `02` §10). |

## A4. Navigation and orientation

**[OBSERVED]** Sticky nav, blurred backdrop, scrollspy active-state, smooth-scroll anchors. Mobile (≤768px): nav links hidden, hamburger button (`#burger`, real `<button>`, `aria-label="Open menu"`, `aria-expanded` toggled) opens a full-screen overlay `#navMobile` (a `<div>`); Esc closes; body scroll locked while open; links close the menu on click.

| Finding | Tag | Notes |
|---|---|---|
| Scrollspy + smooth scroll work well | [OBSERVED] | Good orientation on desktop. |
| Mobile menu has **no CV link** | [OBSERVED] | Only section anchors. Mobile recruiter cannot reach the CV from the menu. |
| Mobile menu is a `<div>`, not `<nav>`/`<dialog>` | [OBSERVED] | No focus trap, background not `aria-hidden`/`inert` while open. **[INFERENCE]** Keyboard/AT users can tab "behind" the overlay. |
| Accordion state not in URL | [OBSERVED] | A recruiter cannot deep-link or share a specific case study; back button doesn't close panels. |
| No skip-link | [OBSERVED] | Keyboard users tab through the full nav on every section jump. |

## A5. Scannability

**[OBSERVED]**
- Case-study impacts are **not scannable** — hidden in collapsed accordions; must open each of 7.
- On mobile, `.pr-short` (the one-line project summary) is `display:none` — mobile users see only title + tag chips before opening.
- Body base font is 15px; many labels/eyebrows/tags/nav items are `.6rem–.72rem` (~9–11.5px), uppercase, letter-spaced, in `--muted (#6b7f91)` or `--dim (#8ea3b4)`.
- Stat row ("20+ / 10+ / 5+ / 10+") is scannable but low-information (see `02` §2).

**[INFERENCE, confidence: high]** A recruiter cannot skim this page for evidence. The scannable layer (hero sentence, stat row, project titles, cert names) is the *low-signal* layer; the *high-signal* layer (project impacts, role clarity) requires deliberate interaction. Small, muted, letter-spaced microcopy adds reading friction, especially on mobile.

## A6. Hierarchy of evidence

**[OBSERVED]** Visual weight, largest → smallest: name (up to ~14rem) › section headings › capability/project titles › body copy › impact bullets (small) › tags/eyebrows (smallest, muted).

**[INFERENCE]** The hierarchy is **inverted for hiring purposes**: the name (lowest information value to a recruiter who already has it from LinkedIn) is the single heaviest element, and the *outcomes* (highest value) are among the smallest, dimmest, and most hidden. Nothing in the visual hierarchy elevates a business result, because none is present to elevate.

## A7. Cognitive load

**[OBSERVED]** To classify Miguel the recruiter must: read the abstract hero, scroll to About for the first concrete anchor, parse 4 methodology cards, open and read ≥3 of 7 accordions, mentally map capabilities↔projects, discount an uncontextualised logo wall, scroll past 7 certs, and reach Contact for the title and targets — then open the CV for dates and the only quantified outcomes.

**[INFERENCE, confidence: high]** Cognitive load is **high**. The page asks the recruiter to assemble the positioning that the page should have handed them.

## A8. Discoverability of case studies

**[OBSERVED]** Projects section is clearly labelled and positioned. **[OBSERVED]** But every case study's content is collapsed (`.pr-panel { max-height:0; overflow:hidden }`) and the `tabindex="0"` that makes rows keyboard-openable is **added by JavaScript**, not in the HTML. **[INFERENCE]** With JS disabled/broken/slow, all 7 case studies are unreadable and unfocusable (see `06`). Even with JS, the impacts are invisible until 7 separate clicks.

## A9. Friction to understand role / impact

**[OBSERVED]** Role clarity is weakest on the most brand-prestigious projects ("Contributed to…" for SEAT; "Concept product designed around…" for Try-On). Impact is absent on 4 of 7 projects. The team-of-50 leadership fact and the percentage outcomes are CV-only.

**[INFERENCE, confidence: high]** The two questions that decide an interview — *what did he own?* and *what changed because of it?* — are the highest-friction questions on the site.

## A10. CTA journey

**[OBSERVED]** Hero CTAs: "Explore my work →" (to Projects), "Get in touch" (to Contact). Contact CTAs: LinkedIn, email, phone, Download CV. No CTA anywhere says "View CV" or "Book a call". No sticky/persistent contact affordance. CV download is an ~88 KB base64 `data:` URI with a `download` attribute — it works but the CV can't be *viewed inline* or *shared as a link*.

**[INFERENCE]** The recruiter's likely next action (get the CV) is unsupported until the final section and is delivered as a forced download rather than a view.

## A11. Mobile / responsive behaviour

**[OBSERVED]** Dedicated breakpoints at 1100px and 768px. At ≤768px: hamburger nav, single-column grids, hero type `clamp(2.9rem,14vw,4.9rem)` with forced `<br>` breaks, `.pr-short` hidden, `.hero-scroll` hidden, footer stacked, section padding 120px→80px.

| Finding | Tag |
|---|---|
| Layout adapts cleanly (grids collapse to 1-col) | [OBSERVED] positive |
| `14vw` hero type: on a 360px screen ≈ 50px — very large, forced breaks help but the name dominates the first screen even more than on desktop | [INFERENCE] |
| Mobile menu lacks CV link and focus trap | [OBSERVED] (A4) |
| Mobile users get *less* project info (`.pr-short` hidden) yet the same 7-tap cost to see impacts | [INFERENCE] friction |
| No horizontal-scroll issues found in the CSS review; `overflow-x:hidden` on body | [OBSERVED] |
| `-webkit-backdrop-filter` present alongside `backdrop-filter` | [OBSERVED] positive (Safari) |

**[UNCERTAIN]** Real-device rendering (tap target sizes on the accordion arrows, marquee performance on low-end phones) not verified in this pass.

## A12. Keyboard / navigation

**[OBSERVED]**
- **No `:focus` or `:focus-visible` rule anywhere in the CSS.** Focus indication depends entirely on the UA default, which is weak/none on custom-styled `<a>` and script-focusable `<div>` elements, and low-contrast on the near-black background. **WCAG 2.4.7 (Focus Visible) — likely failure.**
- Project rows: keyboard-operable (Enter/Space toggle, Esc closes) **but only after JS runs**, and they are `<div>`s with a script-added `tabindex` and **no `role="button"` and no `aria-expanded`** — a screen-reader user hears "clickable" at best, with no state.
- Capability cards (`.cap`): **not keyboard-operable at all** — plain `<div>`s, click-only, no `tabindex`, no role, no `aria-expanded`. The "What changes" panel is `max-height:0;opacity:0` until `.cap-on` is toggled by mouse/touch click. Card index 2 ("AI Workflow Integration") is open by default; the other three cards' detail is **unreachable by keyboard**.
- No skip-link; no `<main>`.
- Hamburger: correct (`<button>` + `aria-expanded`). Positive.

**[INFERENCE, confidence: high]** Keyboard accessibility is **partly broken**: a keyboard-only recruiter (or anyone using assistive tech) cannot open 3 of 4 capability panels and gets no visible focus ring anywhere.

## A13. Accessibility (summary — full list in `06` §7)

| Check | Result | Tag |
|---|---|---|
| `lang="en"` on `<html>` | ✅ present | [OBSERVED] |
| Single `<h1>`, ordered headings | ✅ (though `<h1>` is name-only, `<h2>` "Who I Am" non-descriptive) | [OBSERVED] |
| `<main>` landmark | ❌ absent | [OBSERVED] |
| Skip link | ❌ absent | [OBSERVED] |
| `alt` on images | ✅ 26/26 have `alt` — but project images use the project *name* as alt (not a description), and marquee logos repeat each brand twice (some `aria-hidden` present — likely mitigates the duplicate) | [OBSERVED] |
| Visible focus indicator | ❌ no focus CSS | [OBSERVED] |
| Interactive elements are real controls | ❌ capabilities & projects are `<div>`s; `role=` count in document = 0 | [OBSERVED] |
| `aria-expanded` on disclosure widgets | ❌ only on hamburger; not on capabilities or project rows | [OBSERVED] |
| Colour contrast (small muted text) | ⚠️ `--muted #6b7f91` on `#030507` ≈ 4.6:1 → fails AA for text below ~18.7px; used on sub-headline copy and microcopy at ~9–13px | [INFERENCE] |
| Content works without JS | ❌ case studies & capability details are JS-gated | [OBSERVED] |
| Motion respects `prefers-reduced-motion` | ⚠️ partial — only shortens durations; 4 infinite animations not stopped (see A14) | [OBSERVED] |

## A14. Motion & reduced-motion

**[OBSERVED]** Keyframe animations: `fadeIn`, `fadeUp`, `pulse` (10s, infinite — hero orb), `marquee` (30s, infinite — logo strip), `blink` (2s, infinite — scroll cue / cursor), `scrollLine` (2.5s, infinite), `drIn`. Reduced-motion rule: `@media(prefers-reduced-motion:reduce){*{animation-duration:.01ms!important;transition-duration:.01ms!important;}}`.

**[INFERENCE]** The reduced-motion handling is **incomplete**: shortening an *infinite* animation to `.01ms` does not stop it — it loops at maximum frequency (browser-clamped), keeping compositor churn and, for `marquee`/`blink`, an unstable end state. The correct pattern for infinite decorative motion is `animation: none`. Not a photosensitivity hazard here (sub-perceptible opacity/translate), but it defeats the purpose of the user's setting and wastes CPU/battery.

**[OBSERVED]** `.sr` (scroll-reveal) elements are `opacity:1` in *both* the base and `.on` state — so scroll-reveal is effectively a no-op and does **not** hide content. Positive: no reveal-on-scroll dependency for content visibility.

---

# PART B — UI

## B1. Visual hierarchy

**[OBSERVED]** Strong size contrast: hero name `clamp(5rem,14vw,14rem)` desktop; section headings `clamp(2.5–3.5rem,…)`; contact headline `clamp(3rem,8vw,7.5rem)`. Body 15px/1.65. Accent colour (`--lime:#38bdf8`, actually sky-blue) used sparingly on numbers, active states, list markers, primary button.

**[INFERENCE]** Typographically confident and consistent, but see A6 — the hierarchy elevates identity over evidence, which is the wrong priority for hiring. The near-absence of a mid-level "callout" treatment (pull quote, metric badge, highlighted outcome) means there is no visual mechanism to make a result stand out even if one were added.

## B2. Typography

**[OBSERVED — verified]** The page requests two families from Google Fonts: **DM Sans** (body) and **Clash Display** (all display type — hero name, every `<h2>`, nav logo "MABZ", contact headline; used in 14 `font-family` declarations). **Clash Display is not a Google Fonts family** (it is distributed by Fontshare). The Google Fonts stylesheet the page links returns `@font-face` rules for **DM Sans only** — Clash Display is silently omitted.

**[INFERENCE, confidence: high]** **In production the display font never loads.** Every heading and the hero name fall back to `sans-serif` — i.e. the visitor's OS default (Arial / Helvetica / Roboto / system-ui). The distinctive, "designed" part of the type system is absent for all users. For a portfolio whose credibility partly rests on design craft, shipping generic Arial headings is a material perceived-quality defect and a straightforward one to fix (self-host Clash Display from Fontshare, or choose a Google-hosted display face).

**[OBSERVED]** Other type notes: base 15px (below the 16px convention); many microcopy sizes 9–11px uppercase + letter-spacing (readability cost, esp. mobile); `text-rendering:optimizeLegibility` and `-webkit-font-smoothing:antialiased` set.

## B3. Spacing & density

**[OBSERVED]** `section{padding:120px 0}` desktop / `80px` mobile; `.W{max-width:1280px;padding:0 56px}` / `24px` mobile. Generous vertical rhythm, wide gutters.

**[INFERENCE]** Spacing is comfortable and "premium-feeling" but contributes to **page length**: 7 full-height-ish sections + 120px pad each means a recruiter scrolls a long way to reach Contact. Density is low — appropriate for a creative showcase, costly for a scannable hiring document.

## B4. Contrast

**[OBSERVED]** Palette (CSS custom props): bg `#030507`; text `--wht #eef2f5` (excellent contrast), `--wht2 #ccd8e2` (good), `--dim #8ea3b4` (≈6.5:1, ok), `--muted #6b7f91` (≈4.6:1 — **fails AA for normal text**, borderline for large), accent `#38bdf8` (good on black). Hairline borders `rgba(255,255,255,.04–.07)` — near-invisible, decorative only.

**[INFERENCE]** The frequent use of `--muted` for *small* secondary copy (section eyebrows, tags, some descriptive lines) puts a meaningful amount of text below AA. On a portfolio being judged by UX/design-literate reviewers this is a visible competence signal, not just a compliance box.

## B5. Component consistency

**[OBSERVED]** Consistent system: eyebrow label + heading pattern per section; card treatment with hairline borders and `--r:8px` radius; accent-on-hover/active; "+45°/rotate" toggle affordance on both capabilities and projects; number prefixes ("01", "02"…) used in nav-less lists. **[INFERENCE]** Component language is coherent and disciplined — a genuine strength. One inconsistency: SEAT appears as a project but not on the logo wall; brands on the logo wall mostly don't appear as projects.

## B6. Use of imagery & logos

**[OBSERVED]** 26 base64 images: 1 portrait, 7 project images, 18 brand-logo instances (9 logos × 2 for the marquee loop). Project image `alt` = project name. **[OBSERVED]** No imagery of the actual CGI / XR / hyperreal work that the copy describes — the portrait and abstract project thumbnails are the only visuals.

**[INFERENCE]** For a candidate from a visual discipline, showing zero examples of the visual work is a missed credibility opportunity and mildly incongruent. The logo marquee (moving, uncontextualised) is the weakest imagery use (see `02` §8).

## B7. Motion / animation (UI craft view)

**[OBSERVED]** `cubic-bezier(.22,1,.36,1)` easing token used consistently; hero orb `pulse`; logo `marquee`; accordion `max-height` transitions (0 → 1300px for projects, 0 → 200px for capabilities). **[INFERENCE]** `max-height` transitions on large values produce a slight easing lag / non-linear feel on expand; acceptable but not the crispest approach. Motion is tasteful and restrained overall — consistent with a senior *designer* aesthetic.

## B8. Perceived quality

**[INFERENCE, confidence: medium-high]** Intended perceived quality is high (dark, spacious, big confident type, restrained accent, custom easing). **Actual** perceived quality is dented by concrete defects a design-literate reviewer will notice: headings rendering in fallback Arial (B2), no focus states (A12), some sub-AA text (B4), a broken `og:image` on share (`06`), and case studies that don't open without JS. The gap between intended and delivered polish is itself a signal.

## B9. Perceived seniority

**[INFERENCE, confidence: high]** The visual language reads as **"senior creative individual / boutique studio"** — a designer's portfolio. It does **not** read as "operations leader", "transformation lead", "product director", or "Head of". Cues pushing the creative-IC read: "Portfolio 2026" eyebrow, name-as-hero, dark showcase aesthetic, project *thumbnails* over org charts / dashboards / results, an Education section given equal billing to delivery.

## B10. Does the visual language support the target profile?

**[OBSERVED]** Stated targets (Contact): Head of Digital Production / Digital Transformation Lead / AI Systems Lead.

**[INFERENCE, confidence: high]** The UI **over-indexes toward an execution / creative-showcase profile** and under-serves the manager / innovation / product / technology profile Miguel is aiming for. A transformation or production-leadership hire is looking for evidence of scope, teams, governance, stakeholders, and outcomes; the interface gives them atmosphere, methodology and hidden case studies. The design competence is real, but it's arguing for a different (and more junior, relative to his target) job than the one he wants.

---

## Summary judgement

**[INFERENCE, confidence: high]**

- **UX:** The site works as an *atmosphere piece* and fails as a *recruitment product*. Decision-critical facts (title, targets, outcomes, CV) are last, hidden, or CV-only; the evidence layer isn't scannable; case studies are JS-gated; keyboard access and focus visibility are partly broken.
- **UI:** Coherent, disciplined, tasteful design system — genuinely a strength — but undermined in production by the display font not loading (Arial headings), missing focus states, some sub-AA text, and a visual language that argues for "senior creative IC" rather than the leadership/transformation roles being targeted.

**Highest-leverage UX/UI moves (direction only, for cross-review):**
1. Fix the display font (self-host Clash Display or pick a hosted display face). Highest effort-to-impact ratio on the page.
2. Add real focus-visible styles; convert capabilities and project rows to real `<button>` disclosure widgets with `aria-expanded`; put the `tabindex`/interaction in HTML, not JS, or render case-study content visible-by-default and use JS only to enhance.
3. Bring the current title + one plain proposition + a "View CV" action into the hero; add "CV" to the nav and the mobile menu.
4. Make at least one case-study impact visible without a click; add a metric/callout component and use it.
5. Raise `--muted` to meet AA at the sizes it's used; lift base font to 16px; enlarge the smallest microcopy.
6. Replace incomplete reduced-motion duration hack with `animation:none` for the infinite decorative animations.
7. Add `<main>`, a skip link, and a focus trap + background `inert` on the mobile menu.
8. Reconsider whether the visual register should shift ~20% toward "operator/leader" (timeline, outcomes, scope) without losing the craft.
