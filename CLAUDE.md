# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic portfolio site for Jiwen Zhao — a bioinformatics and crop disease resistance researcher. Hosted on GitHub Pages at `cropcoder.github.io`. Static HTML/CSS/JS site with blog articles in Chinese and English.

## Architecture

```
├── index.html                      # Home/resume page (single-page sections + hero)
├── blog/
│   ├── gwas-analysis.html          # Blog: GWAS analysis tutorial (zh-CN)
│   └── rice-disease-resistance.html# Blog: Rice disease resistance review (zh-CN)
├── assets/
│   ├── css/resume.css              # Single stylesheet (~1020 lines)
│   └── js/resume.js                # Nav toggle + scroll-spy active link
├── images/                         # Favicons, profile photo, publication figures
├── .github/FUNDING.yml
├── .nojekyll                       # Disables Jekyll processing for GitHub Pages
└── .gitignore
```

### Key design decisions

- **No build step.** Pure HTML + CSS + JS — `index.html` is both homepage and resume. All blog pages include the same `resume.css` and `resume.js`.
- **Named you must know:** CSS uses BEM-like naming (`site-header`, `hero-copy`, `edu-card`, `life-card`). JS uses data attributes (`[data-nav]`, `[data-header]`) for hooking elements.
- **Blog pages** share the same header/nav structure as the homepage; nav links point to homepage anchors (`../index.html#research`) or sibling blog pages.
- **Active nav link** is driven by a scroll-spy in `resume.js`; blog pages set `.is-active` statically in HTML.
- **Responsive layout** in CSS uses `@media (max-width: 720px)` breakpoint.
- **No dependencies.** No frameworks, no package manager, no bundler.

## Adding a new blog post

1. Create `blog/<slug>.html` starting from an existing blog page as template.
2. Copy the `<header>` block (with shared nav) and the `<script>` tag.
3. Add an entry in `index.html` under `#resources` section — a card linking to `blog/<slug>.html`.
4. Add an entry in the `blog/` page nav if relevant.

## Common commands

- `open index.html` — Preview site locally (no server needed).
- Validate HTML via browser DevTools or the W3C validator.

## Repository conventions

- Commit messages should describe what changed and why.
- Blog articles are written in Chinese (zh-CN), metadata and SEO in English.
- Images should be optimized (compressed) before committing.
