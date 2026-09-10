# Project SVG icons

Five inline SVG illustrations live in the project accordions in `index.html`. They are conceptual icons, not screenshots or business evidence.

| data-project-image | Icon |
| --- | --- |
| content-qa | Question and validation speech bubbles |
| operations-estimator | Two modules connected to a cost symbol |
| process-workshop | Person connected to stakeholder nodes |
| automotive-cgi | Drawing tablet with stylus |
| genai-workflow | Two profiles with connected AI nodes |

All use a 96 × 96 viewBox, no background or text elements, a 2-unit stroke, rounded caps and joins, and the same responsive size and 24px frame padding. The existing 16:10 layout allocation is preserved.

The `.project-image` custom property `--project-icon-color` defaults to `var(--accent)`. The shared `.project-icon` rule controls stroke color, thickness and sizing. SVG paths remain inline so CSS can style them directly, including individual paths if needed.

The icons are decorative alongside the existing project headings: `aria-hidden="true"` and `focusable="false"` avoid redundant screen-reader announcements or keyboard stops. They introduce no motion or JavaScript.
