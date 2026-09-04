# 06 — Technical Audit

The portfolio implementation is audited **as evidence that affects hiring UX, credibility, and perceived professional quality** — not as an engineering-style code review. Each finding is marked **[HIRING-UX]** (a recruiter/hiring manager could be affected) or **[ENG-PREF]** (engineering hygiene, low direct hiring impact).

Evidence tags: **[OBSERVED] / [INFERENCE] / [UNCERTAIN]**. All facts are from `index.html` inherited from `main`, plus a live fetch of `https://mabz-miguel.github.io/` and the Google Fonts endpoint.

---

## 1. Architecture: single-file site

**[OBSERVED]**
- One file: `index.html`, **611,581 bytes**, 942 lines, minimum line length ~35,405 chars (base64 blobs on single lines).
- One inline `<style>` (24,343 chars), one inline `<script>` (3,025 chars). No external JS.
- No build system, no minification (CSS/JS are hand-formatted), no framework, no dependencies.
- External requests: Google Fonts stylesheet + `preconnect` to `fonts.googleapis.com` / `fonts.gstatic.com`. Nothing else.
- Hosting: GitHub Pages (`*.github.io`).

**[INFERENCE]**
- **[ENG-PREF]** Positive: zero dependency rot, no build to break, trivial to host, will run unchanged for years.
- **[HIRING-UX + ENG-PREF]** Negative: **maintainability is poor**. See §9 — this matters here specifically because the whole point of the audit is that the site will need iterative positioning changes.

---

## 2. Embedded / base64 assets & page weight

**[OBSERVED]** 27 `data:` URIs inside the HTML:

| Type | Count | Encoded size |
|---|---|---|
| image/jpeg | 7 | ~311 KB |
| image/png | 15 | ~134 KB |
| image/svg+xml | 4 | ~14 KB |
| application/pdf | 1 | ~90 KB (the CV) |
| **Total base64** | **27** | **~549 KB** (≈ 412 KB decoded) |

Largest single blobs: a 101 KB PNG, JPEGs of 64/53/51 KB, the 88 KB PDF.

**[OBSERVED / INFERENCE]**
- **[HIRING-UX]** The **entire ~600 KB is downloaded on every visit**, before first render is complete, regardless of whether the visitor scrolls to the images or ever downloads the CV. Base64 inflates binary by ~33% and base64 of already-compressed JPEG/PNG **compresses poorly under gzip/brotli**, so the transfer size stays close to 600 KB even compressed.
- **[HIRING-UX]** No `loading="lazy"` and no `srcset`/`<picture>` — and because the images are `data:` URIs embedded in the DOM, lazy-loading is not really possible without restructuring. All image bytes are in the critical HTML payload.
- **[INFERENCE]** On a fast connection this is a ~1s nuisance; on a poor mobile connection or a throttled corporate network it is a multi-second blank/partial page. For a recruiter opening a link between meetings, slow first paint is a small but real drop-off risk.
- **[UNCERTAIN]** Real Lighthouse/Core-Web-Vitals numbers were not measured in this pass. LCP is likely the hero name (system-font fallback — see §5 — so it paints fast); total blocking is dominated by parsing the 600 KB document and decoding images.

**[ENG-PREF]** Direction: move images to real files (`/assets/…`), serve responsive sizes, lazy-load below-the-fold; keep the CV as a real `.pdf` file (also fixes §3 and enables inline viewing + a shareable link).

---

## 3. Embedded CV — encoding defect

**[OBSERVED]** The CV is a base64 `application/pdf` data URI (~88 KB) behind "Download CV" (`download` attribute present, so it saves rather than navigates). The PDF contains **real text**, but drawn through an **embedded subset font with a non-standard character mapping**: extracting or copy-pasting the text yields scrambled characters (see `04` §0 for how this audit recovered the content).

**[INFERENCE, confidence: medium-high — needs a direct test]**
- **[HIRING-UX — potentially P0]** Two concrete risks:
  1. **Copy-paste is broken.** A recruiter copying a line (a title, a bullet, contact details) into an email or ATS gets gibberish.
  2. **ATS / résumé parsers may fail.** If the parser reads glyph indices instead of Unicode, the CV is ingested as gibberish or as near-empty — which can cause **automatic rejection regardless of content**.
- **Required next step:** run the actual PDF through (a) plain text copy in a PDF viewer, and (b) a real ATS or a parser like the ones Workday/Greenhouse/Lever use (or a free résumé-parser test). If confirmed, the CV must be **re-exported so text is standard selectable Unicode** (export from the source tool with fonts outlined *off* / text preserved, or rebuild in a tool that embeds standard font encodings).
- **[ENG-PREF]** Also: distribute the CV as a normal file at a stable URL (`/cv/Miguel-Ballesteros-CV.pdf`) rather than a base64 blob — smaller HTML, shareable link, inline preview, cacheable.

---

## 4. Caching implications

**[OBSERVED]** Everything is in one HTML document; there are no separately-addressable asset URLs (images, CSS, JS, CV are all inline). GitHub Pages typically serves HTML with a short/revalidated cache lifetime.

**[INFERENCE]**
- **[HIRING-UX, minor]** A returning visitor (e.g. a recruiter who bookmarks the page and comes back with a colleague) re-downloads the full ~600 KB because the images/CSS/JS can't be cached independently of the HTML.
- **[ENG-PREF]** Splitting assets to files lets the browser and GitHub Pages' CDN cache the heavy, rarely-changing parts (images, fonts, CV) with long lifetimes while the HTML stays fresh.

---

## 5. Fonts — render-blocking external request + display font not loading

**[OBSERVED — verified against the live Google Fonts endpoint]**
- The page links: `https://fonts.googleapis.com/css2?family=Clash+Display:wght@400;500;600;700&family=DM+Sans:…&display=swap`.
- **Clash Display is not a Google Fonts family** (it is distributed by Fontshare). The Google Fonts response for that URL contains **`@font-face` rules for DM Sans only** — Clash Display is silently dropped.
- `index.html` uses `font-family:'Clash Display',sans-serif` in **14 declarations**: the hero name, every `<h2>`, the nav logo "MABZ", the big contact headline.

**[INFERENCE, confidence: high]**
- **[HIRING-UX — high impact, low fix cost]** **In production, all display type renders in `sans-serif` fallback** — the visitor's OS default (Arial / Helvetica / Roboto / system-ui). The distinctive, "designed" layer of the typography **does not exist for any visitor**. For a portfolio whose credibility rests partly on design craft, shipping generic Arial headings is a visible competence signal working against him. This is the single highest effort-to-impact fix on the site.
- **[ENG-PREF / privacy]** `fonts.googleapis.com` is a render-blocking third-party request that also exposes visitor IP to Google (a live GDPR grey area in the EU). Since only DM Sans actually loads, **self-hosting DM Sans** (and self-hosting a real display face) removes the external dependency, the blocking request, and the privacy question in one move.
- Positive: `display=swap` is set (no invisible-text flash); `preconnect` hints are present.

---

## 6. Semantic HTML

**[OBSERVED]**

| Element | Status |
|---|---|
| `<html lang="en">` | ✅ present (content is British English — consistent) |
| `<nav>` | ✅ (desktop nav) |
| `<footer>` | ✅ |
| `<section id>` × 7 | ✅ all sections landmarked with IDs |
| `<main>` | ❌ **absent** |
| `<header>` (page/hero) | ❌ hero is a bare `<section>` |
| Heading order | ✅ one `<h1>`, `<h2>` per section, `<h3>` for projects/certs — no skipped levels |
| `<h1>` content | ⚠️ **name only** ("Miguel Ángel Ballesteros") — no role; SEO/positioning cost (see `01`, `02`) |
| `<h2>` content | ⚠️ several non-descriptive ("Who I Am", "Let's Build Better Systems") — weak for scanning + SEO |
| Mobile menu | ❌ `<div id="navMobile">`, not `<nav>` / `<dialog>` |
| Interactive widgets | ❌ capability cards & project rows are `<div>`s; document `role=` count = **0**; only one real `<button>` (the hamburger) |
| Lists | ✅ problem/impact/"what changes" items are `<ul><li>` |

**[INFERENCE]**
- **[HIRING-UX]** Missing `<main>` + no skip link + non-descriptive headings degrade the experience for screen-reader users and slightly weaken SEO (headings are a ranking/scannability signal). Search engines and LLM-based "candidate summarizers" lean on `<h1>`/`<h2>` — a name-only `<h1>` tells them nothing about what he does.
- **[HIRING-UX]** `<div>` widgets with no roles: see §7 and `03` A12.

---

## 7. Accessibility attributes & behaviour

**[OBSERVED]**

| Check | Result |
|---|---|
| `alt` on images | ✅ 26/26 — **but** project images use the project *name* as `alt` (not a description of the image), and marquee brand logos repeat each name (some `aria-hidden` present — likely on the loop duplicates, which would mitigate) |
| `aria-label` | 1 (hamburger "Open menu") |
| `aria-expanded` | 1 (hamburger only) — **not** on the capability or project disclosure widgets |
| `aria-hidden` | 7 (likely decorative SVGs / marquee duplicates) |
| `role=` | **0 in the entire document** |
| `:focus` / `:focus-visible` CSS | **none anywhere** → WCAG 2.4.7 (Focus Visible) likely failure; focus rings rely on UA default, weak/invisible on custom-styled `<a>` and script-focusable `<div>` on a near-black background |
| Skip link | ❌ absent |
| Keyboard: project accordions | operable (Enter/Space/Esc) **only after JS runs** — `tabindex="0"` is **added by JavaScript**, not in the HTML; no `role="button"`, no `aria-expanded` |
| Keyboard: capability cards | **not operable at all** — plain `<div>`, click-only; 3 of 4 detail panels unreachable by keyboard (panel is `max-height:0;opacity:0` until a mouse click toggles `.cap-on`) |
| Colour contrast | `--muted #6b7f91` on `#030507` ≈ **4.6:1** → fails AA for text < ~18.7px; used for small secondary copy and microcopy (~9–13px). `--dim #8ea3b4` ≈ 6.5:1 ok. Body `--wht` excellent. |
| `prefers-reduced-motion` | ⚠️ **partial** — `@media(prefers-reduced-motion:reduce){*{animation-duration:.01ms!important;transition-duration:.01ms!important}}` shortens durations but does **not stop the 4 infinite animations** (`pulse` 10s, `marquee` 30s, `blink` 2s, `scrollLine` 2.5s); correct pattern is `animation:none` for infinite decorative motion |
| Content without JS | ❌ case studies unreadable, 3/4 capability panels unreadable, **and on mobile the nav is `display:none` so mobile + broken JS = no navigation at all** |

**[INFERENCE]**
- **[HIRING-UX]** Portfolios in the UX/product space are frequently reviewed by accessibility-literate people. "No focus states, `role=` count zero, div-buttons, sub-AA text" is a fast credibility hit for exactly the audience Miguel is targeting. Most of it is low-cost to fix.

---

## 8. SEO & social metadata

**[OBSERVED]**

| Tag | Status |
|---|---|
| `<title>` | ✅ "Miguel Ángel Ballesteros — AI-Driven Digital Production Systems" (good structure; but the second half is the coined category, not a searched title — see `01`) |
| `<meta name="description">` | ✅ present — *"I design systems that combine AI, product thinking and production workflows to transform how organisations create, scale and deliver digital value."* (differs in wording from the hero; no searched job titles) |
| `og:title` / `og:description` / `og:type` | ✅ present |
| `og:image` | ❌ **`https://mabz.miguel.com/og-image.jpg`** — **wrong domain** (site is `mabz-miguel.github.io`); file almost certainly 404 |
| `og:url` | ❌ absent |
| `twitter:card` | ✅ `summary_large_image` |
| `<link rel="canonical">` | ❌ absent |
| Favicon / `rel="icon"` | ❌ absent — browser tab shows the default globe (reads as "unfinished") |
| `theme-color` | ❌ absent (minor) |
| JSON-LD / structured data | ❌ absent — no `Person` schema (`jobTitle`, `worksFor`, `alumniOf`, `sameAs:[LinkedIn]`) |
| `robots` meta / `robots.txt` / `sitemap.xml` | none (defaults to indexable — acceptable for one page) |

**[INFERENCE]**
- **[HIRING-UX — real]** **The broken `og:image`** means every time the link is shared — a recruiter dropping it in Slack, LinkedIn, WhatsApp, email preview — the card renders with a missing/blank image. First impression of the link is "broken". Fixing it (correct URL + an actual 1200×630 image, ideally with name + title) is high value, low cost.
- **[HIRING-UX]** No favicon is a small "unfinished" signal on every browser tab and bookmark.
- **[ENG-PREF → mild HIRING-UX]** A `Person` JSON-LD block helps Google and AI candidate-summarizers understand who he is and tie the portfolio to his LinkedIn. Cheap to add.
- **[OBSERVED / INFERENCE]** The `mabz.miguel.com` in `og:image` shows the metadata was written for a **custom domain that was never registered/configured**. **[INFERENCE — cost note]** A custom domain (~€10–15/yr) would read as more professional than `*.github.io` for a senior candidate and is trivially supported by GitHub Pages. This is a product decision for Miguel, flagged not mandated.

---

## 9. Maintainability

**[OBSERVED / INFERENCE]**
- **[ENG-PREF, but relevant to this project]** A single 942-line file with ~550 KB of inline base64 is **hard to edit safely**: changing an image means re-encoding and pasting a 100 KB string; editing copy means navigating past giant blobs; **git diffs are unreadable** (a one-word copy change shows as a whole-line change on a 35,000-char line). Reviewing a positioning change — which is precisely what this audit will generate — is unnecessarily painful.
- CSS: one 24 KB block, custom-property-driven (good), terse class names (`.W`, `.sr`, `.pr`, `.cap`), sparse comments. Workable, not friendly to a future editor.
- JS: ~3 KB, vanilla, readable, defensive (`if(!burger||!menu)return`). Fine. One brittle spot: `active=2` hard-coded in the capabilities IIFE (silent breakage if markup order changes).
- Leftover: `<span class="vid-badge" style="display:none">` — unused inline-styled element.
- Variable naming: `--lime` is actually sky-blue (`#38bdf8`); harmless but confusing for a future editor.

**[INFERENCE]** Direction (for later): externalise CSS/JS/images/CV into files; keep the no-framework, no-build simplicity. This makes iterative positioning edits (the ongoing need) reviewable and safe.

---

## 10. Browser robustness

**[OBSERVED / INFERENCE]**
- Modern-browser features used (`backdrop-filter` + `-webkit-` prefix, `IntersectionObserver`, CSS `clamp()`, custom properties, grid, `mix-blend-mode`) — all well-supported today; graceful degradation where not.
- JS is ES5-style (`var`, `function`) — runs in old engines; no transpilation needed.
- **Biggest robustness risk: JS failure.** If the script doesn't run (CSP, extension interference, network blip on an external-blocked corporate proxy, JS error): case studies can't open, most capability detail is hidden, and **on mobile there is no navigation at all** (nav links are `display:none`, hamburger is dead). The site's core content becomes unreachable.
- **[HIRING-UX]** Some corporate mail/proxy filters block or strip large `data:` URIs and `data:application/pdf` downloads → the CV download may silently fail for some recruiters.

---

## 11. Privacy / spam exposure

**[OBSERVED]**
- `mabz.miguel@gmail.com` (personal Gmail) and `+34 669 43 26 22` (personal mobile) appear as plain-text `mailto:` / `tel:` links in the HTML — **harvestable by scrapers**.
- No analytics, no cookies, no trackers, no consent banner needed. Only third parties: LinkedIn (link) and Google Fonts (loads on every visit).

**[INFERENCE]**
- **[HIRING-UX / personal]** Expect scraper spam to the address and possibly the phone. Options (Miguel's call): a dedicated job-search email alias, light obfuscation, or a simple contact form. Publishing a personal mobile number is a conscious personal-data decision — flag it, don't force it.
- **[ENG-PREF / GDPR]** Self-hosting fonts (see §5) removes the only involuntary third-party data flow.

---

## 12. JS interactions — functional review

**[OBSERVED]** 5 IIFEs: (1) scroll-reveal via `IntersectionObserver` — but `.sr` base and `.on` states are identical (`opacity:1`), so it's a no-op that safely does nothing; (2) nav active-state via `IntersectionObserver` (works well); (3) capabilities toggle — click only, `active=2` hard-coded; (4) projects accordion — click + keyboard + `Esc` + `scrollIntoView`, `tabindex` set in JS; (5) hamburger — correct, with `aria-expanded` and body scroll-lock.

**[INFERENCE]** Code quality is fine for the scope. The problems are *architectural* (content visibility depends on JS; interactivity added to non-semantic elements) rather than bugs.

---

## 13. Technical issues ranked by hiring impact

### Affects hiring UX / credibility — fix in the implementation phase
| # | Issue | Why it matters for hiring |
|---|---|---|
| T1 | **CV PDF text is font-encoded** → copy-paste broken, likely ATS-parse failure | Can cause silent auto-rejection; breaks recruiter workflow. **Verify first, then re-export.** |
| T2 | **Display font (Clash Display) never loads** → Arial headings in production | Direct hit to the design-craft credibility the portfolio depends on. Cheapest high-impact fix. |
| T3 | **`og:image` points to a non-existent domain** | Every shared link renders a broken preview card — bad first impression before the page even opens. |
| T4 | **Case studies (and 3/4 capability panels) require JS**; mobile nav is `display:none` so mobile + JS-failure = no navigation | Core content unreachable in a non-trivial minority of sessions. |
| T5 | **No focus-visible styles; `role=` count 0; div-buttons; sub-AA muted text** | Fast credibility loss with the accessibility-literate audience Miguel targets; genuine WCAG failures. |
| T6 | **~600 KB downloaded every visit, all in the critical path** | Slow first paint on poor/throttled connections → drop-off. |
| T7 | **No favicon** | "Unfinished" signal on every tab/bookmark. |
| T8 | **Personal email + mobile in plain text** | Scraper spam; personal-data exposure (Miguel's decision). |
| T9 | **`prefers-reduced-motion` only shortens, doesn't stop, infinite animations** | Ignores an explicit accessibility preference; wastes CPU/battery. |

### Engineering preference — lower hiring impact
- Single-file architecture + base64 assets → maintainability (matters for iterating positioning); externalise assets.
- No `<main>`, no canonical, no `og:url`, no JSON-LD `Person`, no sitemap/robots.
- Google Fonts as a render-blocking third party (self-host).
- `github.io` vs a custom domain (~€10–15/yr) — perception, Miguel's call.
- Leftover `vid-badge` span; `--lime` misnamed; `active=2` hard-coded.
- No minification/build (acceptable given the no-dependency philosophy).

---

## Summary judgement (technical)

**[INFERENCE, confidence: high]** The implementation is **simple, dependency-free and durable** — good instincts — but it ships **several defects that a recruiter or hiring manager can actually feel**: a CV that may not survive ATS parsing, headings rendering in fallback Arial, a broken social-share image, case-study content that disappears without JavaScript, and no accessibility affordances for an audience that checks. None of these are hard to fix, and none require abandoning the no-framework approach. The engineering-preference items (single-file architecture, asset externalisation, metadata completeness) matter mainly because this site now needs to be **edited repeatedly** as the positioning sharpens — and the current structure makes safe iteration harder than it should be.

**Must-verify before the implementation phase:** run the CV PDF through a real ATS/résumé parser and a plain copy-paste test (T1) — this is the one finding that could be silently costing interviews right now.
