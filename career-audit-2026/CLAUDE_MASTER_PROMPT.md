# Claude Code — Independent Career Portfolio Audit Brief

## Mission
Perform an independent, evidence-based audit of Miguel Ángel Ballesteros Zafra's professional positioning and portfolio with one goal: improve his probability of being shortlisted and interviewed for a stronger new role.

This is not a redesign task yet. It is a diagnostic task.

## Mandatory setup
1. Work only on branch `career-audit-2026`.
2. Read:
   - `career-audit-2026/00_CONTEXT.md`
   - `career-audit-2026/claude/README.md`
   - this file
3. Inspect the current portfolio source inherited from `main` as read-only evidence.
4. **Do not read any file under `career-audit-2026/chatgpt/` until explicitly told that the independent-review phase is over.** This is a blind first pass and avoiding cross-contamination is part of the methodology.
5. Do not modify `index.html`, production content, CSS, JavaScript, assets, CV content, or published-site behavior.
6. Only create/update audit documentation under `career-audit-2026/claude/`.

## Critical mindset
Audit what the portfolio actually communicates, not what Miguel says he wants it to communicate.

Do not optimize for politeness or agreement. Separate:
- observable evidence,
- inference,
- uncertainty,
- recommendation.

The controlling question is:

> If a recruiter or hiring manager spends 30 seconds with this profile, what professional do they understand Miguel Ángel is, what problems do they believe he solves, what level of seniority do they infer, and for which roles would they realistically consider interviewing him?

## Deliverables
Create the following Markdown files:

### `01_POSITIONING_AUDIT.md`
Evaluate:
- What professional identity is communicated now?
- What canonical job families/titles does it map to, if any?
- Is the value proposition understandable in 5–30 seconds?
- Does breadth read as senior multidisciplinary capability or as dispersion?
- Does the narrative communicate progression from execution to ownership/leadership?
- What seniority does the page signal?
- Which claims are credible and which need stronger proof?
- What is missing for a recruiter to classify the candidate quickly?
- What target roles appear strongest from the evidence, without forcing a predetermined answer?

End with:
- **30-second recruiter interpretation**
- **Strongest perceived professional identity**
- **Biggest positioning risk**
- confidence level

### `02_PORTFOLIO_CONTENT_AUDIT.md`
Audit content and hiring storytelling:
- Hero
- About / professional narrative
- Selected work / case-study structure
- ownership and role clarity
- business impact and metrics
- evidence / credibility
- client and brand proof
- capabilities / skills
- training / certifications
- CTA and contact copy
- signal-to-noise ratio
- missing evidence

For every major project/case study, ask:
1. What was the problem?
2. What was Miguel's exact role and ownership?
3. What did he decide or lead?
4. Who were the stakeholders?
5. What changed because of the work?
6. What measurable outcome or scale can be proved?
7. What skill relevant to the desired next level does the project prove?

### `03_UX_UI_AUDIT.md`
Treat the site as a recruitment product, not just a creative portfolio.

#### UX
Include:
- 5-second comprehension test
- 30-second recruiter journey
- information architecture
- navigation and orientation
- scannability
- hierarchy of evidence
- cognitive load
- discoverability of case studies
- friction to understand role/impact
- CTA journey
- mobile/responsive behavior
- keyboard/navigation considerations
- accessibility
- motion and reduced-motion behavior

#### UI
Include:
- visual hierarchy
- typography
- spacing
- density
- contrast
- component consistency
- use of imagery and logos
- motion/animation
- perceived quality
- perceived seniority
- whether the visual language supports a manager/innovation/product/technology profile or unintentionally over-indexes toward an execution/creative-showcase profile

Do not recommend visual novelty for its own sake. Every recommendation must improve comprehension, credibility, differentiation, or hiring conversion.

### `04_CV_AUDIT.md`
Inspect the CV embedded/downloadable from the portfolio if you can reliably extract/read it. If extraction is not reliable, state the limitation rather than guessing.

Audit:
- headline/identity
- summary
- chronology
- experience framing
- accomplishments vs responsibilities
- quantified impact
- leadership/ownership evidence
- AI / product / project / operations / technical balance
- ATS clarity and keywords
- signal-to-noise
- consistency with portfolio
- what role the CV currently appears optimized for

Do not rewrite the CV yet.

### `05_TECHNICAL_AUDIT.md`
Audit the portfolio implementation as evidence affecting UX, maintainability and professional quality:
- single-file architecture
- embedded/base64 assets
- embedded CV
- page weight and caching implications
- runtime/performance risk
- semantic HTML
- accessibility attributes
- keyboard behavior
- responsive implementation
- animation/motion behavior
- JS interactions
- SEO metadata
- maintainability
- browser robustness
- privacy/spam exposure if relevant

Separate technical issues that actually affect hiring UX from purely engineering preferences.

### `06_PRIORITY_MATRIX.md`
Create a consolidated priority matrix.

Use:
- **P0** = likely to reduce interview conversion / creates fundamental confusion
- **P1** = materially weakens proof, usability or perceived seniority
- **P2** = polish / optimization / maintainability issue

For every issue include:
- ID
- severity
- surface (positioning/content/UX/UI/CV/technical)
- evidence
- why it matters for hiring
- recommended direction (not final copy/design)
- confidence: high / medium / low

Finish with:
- **Top 10 issues most likely to block or reduce interviews**
- **Top 5 strengths that should be protected**
- **Questions that cannot be answered from current evidence**

## Evidence requirements
Whenever possible cite:
- exact visible copy,
- section names,
- DOM/implementation evidence,
- project structure,
- observable interactions.

Avoid claims such as “modern”, “clean”, “senior”, “confusing” or “premium” without explaining the evidence and recruiting consequence.

## Do not do yet
- Do not redesign the site.
- Do not rewrite hero copy.
- Do not rewrite case studies.
- Do not refactor the code.
- Do not change the CV.
- Do not read ChatGPT's audit.
- Do not decide the final target role before the evidence is compared later.

## Completion
Commit only the audit Markdown files under `career-audit-2026/claude/` to branch `career-audit-2026` with a clear audit-only commit message.

When finished, report only:
1. that the independent audit is complete,
2. which files were created,
3. the commit SHA,
4. whether any evidence could not be inspected reliably.

Do not modify production files.