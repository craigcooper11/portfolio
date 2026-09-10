# AGENTS.md

Context for AI coding agents (Claude Code and similar) working on this repo.

## What this is

A personal portfolio site for Craig Cooper (Senior Agentic AI Lead & Software
Development Manager, IBM). Single-purpose: get hired for agentic AI
engineering / engineering management roles. Audience is technical hiring
managers and recruiters skimming on a laptop or phone.

## Stack

- **One file:** `index.html`. No build step, no package.json, no bundler.
- **Styling:** Tailwind CSS via the CDN script (`cdn.tailwindcss.com`), configured
  inline in a `<script>` block in `<head>`. This is intentional for a static,
  no-build personal site — don't introduce a bundler/PostCSS/Tailwind CLI setup
  unless explicitly asked to. If that ever changes, migrate the `tailwind.config`
  block as-is to a real `tailwind.config.js`.
- **JS:** vanilla, inline at the bottom of `<body>`. No framework. Keep it that way
  unless asked to add one — the two interactive demos (trace explorer, rerank
  toggle) don't need anything heavier.
- **Fonts:** IBM Plex Serif / Sans / Mono, loaded from Google Fonts.
- **Deployment target:** GitHub Pages, serving `index.html` directly from the
  repo root (branch: main, folder: /root). No build or CD — pushes to `main` go
  live as-is. `craigcooper.dev` is the custom domain (see `CNAME`).
- **CI:** `.github/workflows/check.yml` runs on push/PR — link + anchor check
  (lychee, config in `.lycheeignore`) and a placeholder-link guard. Both
  blocking, neither deploys. Keep it green. (No HTML validator — the Tailwind
  CDN `@apply` block trips it by design.)

## Design system

All design tokens live in the `tailwind.config` block at the top of `index.html`:

| Token | Hex | Meaning |
|---|---|---|
| `bg` | `#101b2d` | page background |
| `panel` | `#1d2e49` | demo block background (must stay visibly lighter than `bg`) |
| `paper` | `#ece7dc` | primary text |
| `muted` | `#8fa0b3` | secondary text |
| `accent` | `#3fd1c0` | **reserved for interactive elements only** — links, buttons, toggles, the demo section's top border. Do not use it for static/reference content. |
| `wire` | `#4c6b7a` | static/reference markers (case study bullets, dividers) |
| `wiredim` | `#2a3c4d` | hairline borders between sections |
| `warn` | `#d99a4e` | the one "warn" status state in the trace demo |

**The accent/wire split is a deliberate rule, not a leftover:** bright teal means
"you can click or interact with this," muted slate means "this is reference
info." Keep that distinction when adding new content — don't reach for `accent`
just because something needs to stand out; use `wire` for static emphasis.

Type: IBM Plex Serif for headings, IBM Plex Sans for body, IBM Plex Mono only
for small functional labels (span names, scores, meta lines) — not for general
UI text.

## Content rules — read before editing case studies or adding new ones

- The "Case studies" and any similar first-person technical write-ups are
  **intentionally genericized**: no internal IBM product names, ticket numbers,
  team names, or proprietary specifics. They describe patterns and decisions,
  not internal systems by name.
- Before adding detail to these sections, check it's something Craig is
  actually cleared to say publicly. When in doubt, keep it generic or leave a
  `<!-- EDIT -->` comment flagging it for review rather than guessing.
- Don't invent new metrics, dates, or specifics that weren't already in the
  existing copy — ask instead of fabricating detail to sound more impressive.

## Placeholders

Search the file for `EDIT:` comments — each marks a spot with a placeholder
(email, LinkedIn, GitHub, resume link, homelab repo links, Cloudflare Analytics
token). Don't remove these comments until the real value is filled in; they're
how Craig tracks what's still unfinished.

## Working locally

No server needed — open `index.html` directly in a browser. If a task needs a
local server for some reason (testing service-worker-like behavior, CORS
issues, etc.), a simple `python3 -m http.server` from the repo root is enough;
don't add a dev-server dependency for this.

## Things not to do

- Don't add a JS framework, CSS preprocessor, or build tool without being asked.
- Don't restructure the file into multiple pages/files unless asked — the
  single-file format is deliberate for easy GitHub Pages deployment.
- Don't swap the Tailwind CDN script for a different CSS approach without being
  asked — see "Stack" above for why it's there.
- Don't change the accent/wire color semantics described above without flagging
  it — it's a considered design decision, not an oversight.