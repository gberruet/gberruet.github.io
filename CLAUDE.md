# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

This is a static personal portfolio/landing page for Gastón Berruet, served directly by GitHub Pages from the repo root (`gberruet.github.io`). There is no build system, package manager, bundler, or test suite — it's plain HTML/CSS/JS deployed as-is. Pushing to `main` deploys the live site.

## Working with the code

- `index.html` is the single page for the whole site. Sections (About, Servicios, Clientes, Proyectos, Contacto) are plain `<section>` blocks in one file — there is no templating engine or component system.
- `assets/css/style.css` is the actual stylesheet loaded by the page and is **hand-edited directly**. Do not assume it is regenerated from the SCSS.
- `assets/scss/` (theme-1.scss..theme-4.scss, `theme/_base.scss`, `_mixins.scss`, `_responsive.scss`) is leftover source from the original "devAid" Bootstrap 5 theme this site was built from. `index.html` does not link any of these `.scss` files, and custom classes added since (e.g. `.service-card`, `.whatsapp-float`) only exist in `style.css`, not in the SCSS. Treat the SCSS as reference/unused rather than the source of truth — don't try to "keep them in sync" or run a Sass build for it (there is no build tooling configured in this repo; the original theme used CodeKit, a GUI Mac app, which isn't present here).
- `assets/plugins/` (Bootstrap, Prism, Gumshoe/Popper) and `assets/fontawesome/` are vendored third-party libraries — don't hand-edit them; update by replacing the vendored files if a version bump is ever needed.
- `assets/js/main.js` is small (header scroll animation only) and plain vanilla JS, no module system.
- Content is bilingual-leaning-Spanish (the visible site copy is in Spanish); keep new user-facing copy consistent with that unless told otherwise.

## Verifying changes

There is no build or test command. To check changes, open `index.html` directly in a browser (or serve the directory with any static file server, e.g. `python3 -m http.server`) and visually verify the affected section.
