# IMPLEMENTATION BRIEF — Premium Black / Warm Gold Portfolio

## Objective
Rebuild the **real portfolio on branch `career-audit-2026`** so that its visual direction is as close as practical to the approved reference image shared in ChatGPT: premium near-black interface, warm-gold accents, oversized portrait on the right, large editorial typography on the left, compact impact cards, handwritten statement beside the portrait, and a horizontal capabilities strip immediately below the hero.

This is **not a moodboard task**. Implement the design in the real `index.html` and supporting assets. Preserve the validated career content and positioning. Do not modify `main`.

## Source of truth
Repository: `mabz-miguel/mabz-miguel.github.io`
Working branch: `career-audit-2026`
Current real page: `index.html`

Professional identity is locked:
**Digital Project Manager**

Supporting positioning:
**Digital Production · AI-Enabled Workflows · Cross-functional Delivery**

Do not reopen the positioning unless a factual contradiction is discovered.

---

# 1. VISUAL DIRECTION — MATCH THE REFERENCE

The approved reference is defined by these traits. Reproduce them in HTML/CSS, not as a screenshot:

- very dark / almost black background
- warm champagne-gold accents instead of cyan
- large, premium, editorial typography
- huge portrait occupying roughly the right half of the hero
- clean split composition: content left / portrait right
- portrait blends naturally into black background with gradient/overlay
- small uppercase tracking-heavy eyebrow text
- `Digital Project` in warm white and `Manager` in gold
- thin gold separators and borders
- compact dark metric cards with subtle warm-gold icons
- handwritten gold statement next to the portrait
- understated, premium navigation
- horizontal capabilities strip below the hero
- large breathing room and visual rhythm
- no corporate-blue/cyan anywhere
- no generic SaaS/dashboard look

The result should feel closer to a premium creative/directorial portfolio than to a CV turned into a webpage.

## Recommended colour system
Use this as the starting palette and adjust only slightly if needed for contrast:

```css
--bg: #070707;
--bg-soft: #0b0c0d;
--panel: #101112;
--panel-2: #131313;
--text: #f3f1ed;
--soft: #c7c1b9;
--muted: #8f8a83;
--gold: #d7ad72;
--gold-soft: #bb9461;
--gold-pale: #e3c18d;
--line: #2b2926;
--line-soft: rgba(215,173,114,.20);
```

Remove the current cyan visual system entirely.

## Typography
Aim for the reference's clean geometric sans + handwritten accent.

Preferred:
- Main UI / headings: `DM Sans` or `Manrope`
- Handwriting: `Caveat`

If external fonts are used, load them correctly and provide sensible fallbacks. Do not request a font that is never actually served.

---

# 2. RECOVER AND USE THE REAL PORTRAIT

The original portrait is still embedded in the `main` branch's old `index.html` as a Base64 data URI inside:

```html
<div class="about-right">
  <img ... alt="Miguel Ángel Ballesteros" ...>
</div>
```

Extract that exact portrait from `main:index.html` and save it as a normal asset in the working branch, preferably:

`assets/miguel-angel-ballesteros-portrait.jpg`

Do **not** leave it embedded as Base64 in the final portfolio.

The recovered file should be the original JPEG (~1536×1024, roughly 76 KB).

## Portrait treatment
Desktop hero:
- portrait should be **as large as possible** without compromising the title/content
- visual target: image occupies approximately 50–55% of viewport width
- hero should feel close to full-screen on a common desktop viewport
- crop with `object-fit: cover`
- preserve the face and shoulders/arms
- use `object-position` around center / upper-centre and tune visually
- image should reach the right edge of viewport
- no rounded profile-photo treatment
- no LinkedIn-style headshot card
- blend the image into the left side using a dark gradient rather than a hard vertical seam
- keep natural skin tones; do not apply a strong colour filter

This photo is a central part of the page, not decoration.

---

# 3. HEADER / NAVIGATION

Recreate the approved reference structure.

Left block:

**MIGUEL ÁNGEL BALLESTEROS**

Below, small spaced text:

`PROJECTS / DELIVERY / PROGRESS`

Navigation on desktop:
- Home
- Selected Work
- Expertise
- Experience
- Education
- Contact

Right CTA:
`Let's Connect  →`

The CTA scrolls to Contact.

Visual treatment:
- transparent / almost-transparent dark header
- thin bottom line only if necessary
- active Home link with subtle gold underline
- generous horizontal spacing
- small elegant typography

Mobile must remain fully keyboard-accessible and usable.

---

# 4. HERO — CONTENT AND EXACT HIERARCHY

The hero must be the strongest visual moment of the entire site.

## Eyebrow
Use:

`TURNING IDEAS INTO REAL DELIVERY`

Small uppercase, wide tracking, warm gold.

## Main title
Two-line composition:

`Digital Project`
`Manager`

- first line warm white
- `Manager` warm gold
- very large scale, matching the reference
- strong tight leading
- no giant name dominating the hero

## Main copy
Keep the validated copy, but format it compactly:

> I lead digital projects from business need to delivery — coordinating people, scope, budgets, quality and timelines across creative, technical and business environments.

Second paragraph:

> 20+ years in digital production, 3D/CGI, XR and design give me the technical depth to make realistic project decisions. AI and automation are tools I use when they add value.

Do not add extra paragraphs.

## Handwritten statement
Place it beside the portrait, visually similar to the reference, in gold handwritten typography:

**Good Projects**
**Build**
**Better Teams**

Use real HTML text styled with the handwriting font, not a rasterised text image.
Add a small hand-drawn-style underline/stroke using CSS or SVG.
Slight rotation is welcome (~ -4deg to -7deg), but keep it elegant and readable.

## Hero impact cards
Use four compact cards to reproduce the rhythm of the reference while keeping only defensible evidence:

1. **20+**
   `Years across digital production, design & technology`

2. **25%**
   `Operational-cost reduction contribution`

3. **40%**
   `Faster time-to-market contribution`

4. **End-to-end**
   `Scope, budgets, quality and delivery ownership`

The fourth card is qualitative — do NOT invent a fake numeric metric.

Do not reintroduce `10 people`, `50+ projects`, `3x`, `100%`, or any other invented/reference-only metric.

## Hero CTAs
The user explicitly asked to remove the redundant `See work / View my work` CTA because Selected Work follows immediately.

Therefore the hero has only:

`Download CV`

The top navigation can still contain `Let's Connect`.

## Small closing phrase
Bottom-left area of hero, similar to the reference:

`BETTER SYSTEMS.`
`CLEARER DELIVERY.`
`REAL PROGRESS.`

Use tiny uppercase lettering with a thin vertical gold line.

---

# 5. FIRST SECTION BELOW HERO — EXPERTISE STRIP

This should visually continue the approved reference, not abruptly return to the old card grid.

Left:

small label: `WHAT I DO —`

large statement:

`From strategy`
`to execution.`

Make `to execution.` gold.

To the right, four horizontally distributed capability items with subtle line icons and thin vertical separators:

### Project Management
`Aligning people, priorities and progress.`

### Digital Production
`Delivering work with structure, quality and flow.`

### AI & Workflow Improvement
`Using AI to work smarter when it adds value.`

### Client & Team Coordination
`Connecting stakeholders, delivery and outcomes.`

This replaces the current visually generic 2×2 capability cards.

On tablet/mobile it may collapse to 2×2 / 1-column while preserving the same hierarchy.

---

# 6. SELECTED BRANDS & CLIENTS

Keep the section because the user explicitly wants it back.

Use a compact premium presentation, ideally one horizontal band/row rather than a huge logo wall.

Heading:
`Selected brands & clients`

Copy:
`Selected brands and organisations I have worked with directly or as part of agency and consultancy teams.`

Names currently validated for display:
- Mercedes-Benz
- IKEA
- Heineken
- Pfizer
- Renault
- Radisson
- Repsol
- Codere
- Sika

Use text-based wordmarks / restrained typographic treatment unless actual reusable logo assets are already available and clearly appropriate. Do not make the brands visually overpower Miguel's work.

---

# 7. SELECTED WORK

Preserve the information architecture of expandable projects because it solves the density problem.

Do not return to a long wall of open text.

Keep five projects:
1. Intelligent Content QA System
2. Marketing Operations Estimator
3. Process Transformation Workshop
4. Automotive CGI Production & Team Leadership
5. GenAI Enablement & Workflow Adoption

Important content rules:
- no `MVP` label anywhere
- QA is a functional, reusable system
- Estimator is a working product/framework that continues evolving
- the user is considering commercialising QA, so do not frame it as a toy prototype
- preserve defensible ownership and outcomes
- client details inside cases remain anonymised where currently anonymised

Visual redesign:
- gold project numbers
- thin warm-gold rules
- large clean titles
- compact tags
- black-on-black panel depth
- expansion arrow / plus in gold
- expanded content should remain concise
- keep native `details/summary` or an equally accessible semantic implementation

Do not use project imagery from confidential Accenture/client work.

---

# 8. EXPERIENCE

Preserve the expandable structure and keep it visually concise.

Current Accenture entry must NOT display `Assistant Manager` in the portfolio.
Use the functional market-facing line already approved:

`Digital Project Management · GenAI Adoption & Digital Innovation`

Company:
`Accenture Marketing Operations`

Do not falsely state that the formal Accenture title is `Manager`; simply describe the functional area as above.

BlackSheepStudio must preserve the newly confirmed evidence:
- founder / studio director
- direct client relationships
- requirements
- project/product definition
- scope
- estimates
- project budgets
- planning
- production
- external collaborators
- quality
- timelines
- final delivery

The visual style should use gold dates / companies and restrained accordion rows.

---

# 9. EDUCATION — KEEP HIERARCHY

Do not flatten all education into equal cards.

Primary / high-priority qualifications should be clearly more prominent:
- Project Management Certificate — Google — 2025
- Product Management Certification — ESIC — 2025
- CRO & Product Designer — Gen/D — 2022
- UX/UI Advanced — Mr Marcel School — 2020
- VR / AR / XR Development Expert — UTAD — 2017–2018
- Design Thinking — Universidad Nebrija / Euroinnova — 2025

Secondary specialist training should sit below in a more restrained list:
- The Creative Process in Graphic Design — IED Madrid — 2021
- How Designers Make Decisions — La Nave Nodriza — 2021
- Digital Art for Animation and Video Games — Animum — 2013
- Graphic Art and Advertising — C.E.N.P. — 2001–2004

Restyle primary cards into the same black/gold language. Secondary education should be visually quieter.

---

# 10. CONTACT / FOOTER

Contact section should feel like the conclusion of the same premium visual system.

Headline can remain:
`Let's make the project work.`

Keep:
- Email
- LinkedIn
- Download CV

Use warm-gold button styling and dark panels.

Footer:
`© 2026 Miguel Ángel Ballesteros Zafra`
`Digital Project Manager · Madrid, Spain`

---

# 11. DENSITY RULE

A major user complaint was that the portfolio had become too dense and repetitive.

Apply this editorial rule throughout:

> Every important idea appears once as a message and, at most, once again as evidence.

Do not repeat `project delivery`, `cross-functional`, `AI workflows`, `stakeholders`, etc. in every section.

The visible, collapsed page should be easy to scan in under a minute.
Details should be available only when the recruiter chooses to open a project or role.

---

# 12. RESPONSIVE BEHAVIOUR

Desktop fidelity to the reference is the priority, but mobile must be deliberately designed.

Desktop:
- hero roughly 90–100vh
- left content ~45–50%
- portrait ~50–55%
- handwritten statement floats in the portrait transition area

Tablet:
- preserve two-column hero as long as readable
- metric cards may become 2×2

Mobile:
- do not try to squeeze the desktop split layout
- use a deliberate stacked composition
- title/copy first
- portrait becomes a large full-width visual block (not a tiny avatar)
- handwritten statement can overlay the image with safe contrast
- metrics become 2×2 or horizontal-scroll if necessary, but no cramped 4-column row
- capability strip becomes 1- or 2-column
- all accordions remain usable

No horizontal overflow.

---

# 13. ACCESSIBILITY / TECHNICAL QUALITY

Do not regress fixes already made during the audit.

Must retain or improve:
- semantic `<main>`
- skip link
- keyboard-accessible navigation
- visible focus states (use gold rather than cyan)
- native accessible accordion behaviour
- `prefers-reduced-motion`
- responsive navigation
- canonical URL
- OG metadata
- JSON-LD
- robots/sitemap already present
- valid heading hierarchy

Contrast must remain readable despite the muted luxury palette.

Avoid unnecessary JavaScript. The design should work with HTML/CSS first.

---

# 14. PERFORMANCE

The original portfolio was ~600 KB+ largely because of embedded assets.
Do not repeat that architecture.

- extracted portrait must be a normal image asset
- no Base64 photos in final HTML
- no huge embedded media
- use responsive sizing
- lazy-load below-the-fold imagery if any is later added
- do not add project imagery merely for decoration

---

# 15. DO NOT DO

- Do not touch `main`.
- Do not change the primary identity away from `Digital Project Manager`.
- Do not reintroduce `Assistant Manager` in the portfolio.
- Do not invent metrics from the design reference.
- Do not use `MVP` for QA or Estimator.
- Do not reintroduce a redundant `See work` CTA in the hero.
- Do not add confidential screenshots or client-production imagery.
- Do not make all training visually equal.
- Do not turn the site back into a long open-text CV.
- Do not use cyan/blue as the main accent.
- Do not replace the real portrait with an AI-generated face.

---

# 16. VALIDATION BEFORE REPORTING COMPLETE

Before saying the redesign is finished:

1. Render/test the actual `index.html` at desktop, tablet and mobile widths.
2. Compare the desktop hero visually against the approved reference direction.
3. Verify the real recovered portrait is used.
4. Verify no content overflows the portrait or navigation.
5. Verify no cyan remains except accidental browser defaults (which should also be removed).
6. Verify `Assistant Manager` is absent from portfolio text.
7. Verify `MVP` is absent from portfolio text.
8. Verify `10 people`, `50+`, `3x`, `100%` or other reference-only invented metrics are absent.
9. Verify Download CV link still works.
10. Verify `details/summary`, keyboard focus, mobile menu and reduced motion.
11. Report changed files and commit SHA.

## Deliverable
Implement the redesign directly on branch `career-audit-2026`, commit it, and provide a concise implementation report. Do not merge to `main`.
