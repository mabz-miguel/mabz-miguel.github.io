# Project SVG icons

User-supplied vector artwork, integrated through external SVG `<use>` references in `index.html`:

| Project | File |
| --- | --- |
| QA System | QA.svg |
| Estimator | stimator.svg |
| Workshop | DT.svg |
| Automotive CGI | CGI.svg |
| GenAI | IA.svg |

Original geometry is preserved. All drawings are centered by translation on a common transparent 144 × 120 viewBox, retaining the same coordinate scale and 2-unit stroke. No background, rasterization or new shapes are added. Export-only metadata and editor classes are omitted.

Each file exposes `#project-icon` with `fill="none"` and `stroke="currentColor"`. The portfolio controls the inherited color through `.project-image { --project-icon-color: #E9EDF0; }` and `.project-icon { color: var(--project-icon-color); }`. All five are intentionally neutral; the existing blue portfolio accent is not applied to the entire artwork.

The shared frame keeps its 16:10 ratio and 24px padding. All SVGs use the same responsive width and aspect ratio. The icons are decorative beside descriptive project headings and remain hidden from assistive technology. No animation or JavaScript is added. Serve the page over HTTP so external SVG references load normally.
