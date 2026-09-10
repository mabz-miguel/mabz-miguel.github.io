# Project SVG icons

User-supplied vector artwork. The normalized source files remain in this directory, and their geometry is embedded inline in `index.html` for reliable local and hosted rendering:

| Project | File |
| --- | --- |
| QA System | QA.svg |
| Estimator | stimator.svg |
| Workshop | DT.svg |
| Automotive CGI | CGI.svg |
| GenAI | IA.svg |

Original geometry is preserved. All drawings are centered by translation on a common transparent 144 × 120 viewBox, retaining the same coordinate scale and 2-unit stroke. No background, rasterization or new shapes are added. Export-only metadata and editor classes are omitted.

Each source file exposes `#project-icon` with `fill="none"` and `stroke="currentColor"`. The inline instances use the same attributes. The portfolio controls their inherited color through `.project-image { --project-icon-color: var(--accent); }` and `.project-icon { color: var(--project-icon-color); }`. All five use the same blue accent as the rest of the portfolio (#5BAFD6).

The frame follows the adjacent text height, without an imposed image ratio or vertical padding. All SVGs share a 128px width and 144:120 aspect ratio, with 16px horizontal frame padding on desktop and none on mobile. The icons are decorative beside descriptive project headings and remain hidden from assistive technology. No animation or JavaScript is added. Inline geometry avoids browser security restrictions that block external SVG `<use>` references when `index.html` is opened directly through a `file:` URL.
