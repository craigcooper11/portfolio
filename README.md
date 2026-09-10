# portfolio

Personal portfolio site for Craig Cooper — Senior Agentic AI Lead & Software
Development Manager.

Single static file (`index.html`): Tailwind via CDN, vanilla JS, IBM Plex fonts,
no build step. Deployed with GitHub Pages from `main` / root.

## Run locally

No server needed — open `index.html` in a browser. Or:

```bash
python3 -m http.server
```

then open <http://localhost:8000>.

## Layout

| File | Purpose |
| --- | --- |
| `index.html` | the entire site — markup, `tailwind.config`, and the demo script |
| `Craig_Cooper_Resume.pdf` | one-page résumé, linked from the site |
| `AGENTS.md` | context for AI coding agents (and humans) working on this repo |
| `.nojekyll` | tells GitHub Pages to serve files as-is |

See `AGENTS.md` before editing — it covers the design tokens, the accent/wire
colour split, and the content rules for the case studies.
