# Project image handoff

The portfolio currently reserves one neutral image slot per project. No screenshots or publishable project renders were present in the repository. These slots are placeholders, not project evidence.

| HTML data-project-image | Asset to supply | Fit |
| --- | --- | --- |
| content-qa | Sanitized screenshot of the actual QA comparison and validation interface | contain |
| operations-estimator | Sanitized actual estimator inputs and result | contain |
| process-workshop | Non-verbal workshop / prioritisation image without client identity or readable confidential text | cover |
| automotive-cgi | Publishable automotive interior / lighting CGI render; prioritize this asset | cover |
| genai-workflow | Neutral actual ComfyUI workflow and output screenshot | contain |

Use a 16:10 composition, ideally 1280 × 800, in WebP or JPEG. Keep screenshots readable at the rendered width; crop to the relevant real interface without fabricating results.

For each `data-project-image` figure in index.html, keep its `project-image` frame and replace the SVG with an image:

```html
<img src="assets/projects/content-qa.webp"
     alt="Describe the actual visible interface once supplied"
     width="1280" height="800" loading="lazy" decoding="async">
```

Remove `role="img"` and `aria-label` from the frame when adding the image so its specific alt text provides the accessible description. All frames share aspect ratio, border and radius. The `project-image--photo` modifier crops photographic compositions; interface screenshots use contain to retain their full contents.
