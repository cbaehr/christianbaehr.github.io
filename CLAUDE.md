# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal academic website for Christian Baehr (Ph.D. Candidate in Politics, Princeton University), built with Jekyll and deployed via GitHub Pages. Pushing to `main` triggers an automatic GitHub Pages build — there is no separate CI/CD step.

## Commands

```bash
# Install dependencies
bundle install

# Run local dev server (auto-reloads on file changes, except _config.yml)
bundle exec jekyll serve

# Build static site to _site/
bundle exec jekyll build
```

> After changing `_config.yml`, restart the server — it is not hot-reloaded.

## Architecture

This is a **single-page site**. Nearly all content lives in `index.markdown`, which uses the `home` layout.

**Layout chain:** `index.markdown` → `_layouts/home.html` → `_layouts/default.html` → includes `_includes/header.html` and `_includes/footer.html`.

**Styling:**
- `assets/main.scss` imports the `minima` theme and adds site-wide overrides (max content width, font size, image/icon layout).
- Inline `<style>` blocks in `index.markdown` handle page-specific layout (the profile image float, `.spaced-lines`, collapsible `<details>` styling).
- Icon fonts are self-hosted: Academicons in `css/academicons.min.css` + `fonts/`, Font Awesome in `css/fontawesome/all.min.css` + `css/webfonts/`. They are loaded in `_includes/header.html`.

**Icons:** Academic icons use the `ai ai-*` class (e.g. `ai-cv`, `ai-google-scholar`). Social/UI icons use Font Awesome classes (`fas`, `fab`).

**Navigation:** Pages are sorted by `navigation_weight` front matter. Currently, no pages have a title set, so the nav bar is effectively empty — the site is single-page.

**Site metadata** (`_config.yml`): `title`, `email`, `description`, `twitter_username`, `github_username`. Uses `github-pages` gem to match GitHub Pages' build environment.
