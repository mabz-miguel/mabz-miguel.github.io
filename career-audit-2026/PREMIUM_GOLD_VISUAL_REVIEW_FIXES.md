# Premium Gold — Visual Review Fixes

Status: review of Claude implementation commit `00653e982ad8bbb09263bfcb6130a6eabb15bffa` against the approved visual reference.

## Decision

The redesign direction is correct and much closer to the approved reference. Do **not** reopen positioning or content architecture. No merge to `main` yet. Apply only the visual/hierarchy corrections below, preserving validated content.

## P1 — Hero must match the approved reference more closely

### 1. Keep the title to two lines on desktop

Current rendered desktop breaks the title into three lines:

- Digital
- Project
- Manager

The approved reference is:

- Digital Project
- Manager

At ~1440px desktop, widen the left hero content and/or reduce the headline size enough to keep `Digital Project` on one line. Preserve `Manager` in warm gold. Do not reduce the visual authority of the title.

Target: the left content block should occupy roughly 46–48% of the hero and the portrait roughly 52–54%.

### 2. Put the four proof cards inside the hero

The approved reference shows the proof cards inside the hero, directly below the introduction and before the primary CTA. Current implementation places the proof band after a full-height hero, so none of the cards are visible in the first viewport.

Move these four items into the left hero area as compact bordered cards:

- `20+` — Years across digital production, design & technology
- `25%` — Operational-cost reduction contribution
- `40%` — Faster time-to-market contribution
- `End-to-end` — Scope, budgets, quality and delivery ownership

`End-to-end` is a capability marker, not an invented metric, and is supported by BlackSheepStudio ownership.

Remove the duplicated standalone impact band once the cards live inside the hero.

### 3. Remove the duplicate full name beneath the H1

The name is already prominent in the top-left identity. The extra `Miguel Ángel Ballesteros Zafra` line below the H1 adds density and is not present in the approved reference. Remove it from the hero.

### 4. Make the portrait brighter while preserving the black blend

The portrait size is good, but the rendered face is noticeably darker than the approved reference. Keep the strong dark blend into the left side, but reduce the overlay over the face/right half so the portrait is more present.

Suggested approach: keep the left-to-right gradient but make the right half effectively transparent and, if needed, use a very subtle image `brightness(1.05–1.10)` / contrast adjustment. Do not retouch or regenerate the face; use the recovered real portrait only.

### 5. Move the handwritten phrase closer to the reference

Keep exactly:

`Good Projects`  
`Build`  
`Better Teams`

Keep Caveat / handwritten styling and the hand-drawn underline. On desktop, place the phrase to the **right of the face / in the right-side negative space**, not over the centre of the torso. It should read as a personal handwritten annotation beside the portrait, like the approved reference.

### 6. First desktop viewport should reveal the next rail

At ~1440×1000, the approved reference already reveals the `What I do / From strategy to execution` rail at the bottom of the first viewport. Current hero consumes the whole first viewport before the impact band.

After moving proof cards into the hero, reduce desktop hero vertical excess so the expertise rail begins at approximately the lower 20–25% of a 1000px-tall viewport. Do not squeeze the content; adjust spacing and hero height proportionally.

Preserve the closing micro-copy:

`BETTER SYSTEMS.`  
`CLEARER DELIVERY.`  
`REAL PROGRESS.`

with the thin gold vertical rule.

## P1 — CV regression introduced during the redesign

The portfolio redesign should not silently replace the previously validated CV strategy.

Claude generated a new two-page PDF and `assets/cv.html`. It also reintroduced the phrase `teams of up to 10 people` in the CV. Miguel explicitly asked not to frame his leadership around the number 10 because it makes the profile feel smaller; use leadership responsibility instead.

Before merge:

- remove `up to 10 people` from the downloadable CV wording;
- preserve the concrete five-person CGI team only inside the specific CGI evidence where context makes the number useful;
- do not expand the CV to two pages merely because the portfolio was redesigned. Prefer the previously validated one-page recruiter/ATS version unless there is a specific evidence-based reason to change it;
- do not change the portfolio positioning while fixing the CV asset.

## P2 — Keep what is already working

Do not undo these successful changes:

- near-black + warm champagne-gold palette;
- real recovered portrait as external image asset, no base64;
- large right-side portrait treatment;
- DM Sans / clean sans-serif UI and Caveat handwriting;
- top-left identity and `Projects / Delivery / Progress` microline;
- outlined `Let's Connect` top-right CTA;
- native accessible `details/summary` accordions;
- compact clients/brands row;
- anonymised client details inside Accenture-related cases;
- no `Assistant Manager` in portfolio;
- no `MVP` labels;
- no invented `50+`, `3x`, `100%`, etc.;
- education hierarchy: core qualifications first, specialist training second;
- responsive/accessibility work already implemented.

## Acceptance check

At desktop 1440×1000 the first view should visually read, in this order:

1. compact premium header;
2. eyebrow;
3. two-line `Digital Project / Manager` title;
4. concise value proposition;
5. four compact proof cards;
6. primary CV CTA;
7. large, clearly visible real portrait on the right;
8. handwritten `Good Projects / Build / Better Teams` beside the portrait;
9. bottom-left `Better systems / Clearer delivery / Real progress` micro-copy;
10. beginning of the `From strategy to execution` capability rail visible at the bottom of the viewport.

Do not merge to `main`. Commit the corrections to `career-audit-2026` and leave them ready for ChatGPT's final visual/recruiter review.
