# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the public documentation site for the **AIVA** (AI-powered genomic data Visualization and Analysis) platform by MHS Precision Labs. It is a static documentation site built with **MkDocs Material** and deployed to GitHub Pages.

Live site: https://mhspl.github.io/aiva-docs/

## Commands

```bash
# Install dependencies (use the .venv Python 3.13 virtual environment)
pip install -r requirements.txt

# Start local dev server (http://127.0.0.1:8000)
mkdocs serve

# Build the site (strict mode, same as CI)
mkdocs build --strict
```

## Deployment

Pushes to `main` trigger the GitHub Actions workflow (`.github/workflows/deploy.yml`) which builds with `mkdocs build --strict` and deploys to GitHub Pages. The `dev` branch is used for development work before merging to `main`.

## Architecture

- **mkdocs.yml**: Single config file defining site structure, theme (Material), plugins, markdown extensions, and navigation hierarchy. The `nav:` section is the source of truth for page ordering.
- **docs/**: All content lives here as Markdown files organized into subdirectories by feature area (samples, aiva-chat, data-table, analysis, collaboration, reports, playbooks, classification, api, compliance).
- **docs/index.md**: Landing page with custom HTML mockups (pipeline flow, chat, variant table, report) styled via custom CSS. Not a typical Markdown page.
- **docs/assets/stylesheets/custom.css**: All custom styling (feature mockups, classification badges, tier badges, admonition overrides, typography). Uses `aiva-` prefixed CSS classes and supports both light/dark themes via `[data-md-color-scheme="slate"]` selectors.
- **site/**: Build output (gitignored in CI, but present locally).

## File Size Limit

Documentation files should not exceed 500 lines. If a page grows beyond that, split it into smaller, focused sub-pages.

## Writing Conventions

- Audience: clinical and research users (geneticists, bioinformaticians, lab directors), not software engineers
- Headings: sentence case ("Uploading your first sample")
- UI elements: bold ("Click **Upload**")
- File formats: uppercase (VCF, CSV, TSV)
- Product names: "AIVA Chat", "AIVA", not informal variants
- Callouts use MkDocs admonitions: `!!! tip`, `!!! warning`, `!!! info`, `!!! note`
- Screenshots go in `docs/assets/images/screenshots/{feature}/`
- Do not use em dashes (`--` or `—`) in documentation. Use colons, commas, semicolons, or separate sentences instead
- Cross-link between pages using relative paths

## Key Plugins & Extensions

- **pymdownx.superfences** with mermaid fence support
- **pymdownx.tabbed** (alternate style) for tabbed content
- **pymdownx.tasklist** with custom checkboxes
- **glightbox** for image lightboxes
- **minify** for HTML minification in production

## Custom CSS Classes

The landing page and docs use custom CSS classes prefixed with `aiva-`:
- `.aiva-badge--path`, `.aiva-badge--lpath`, `.aiva-badge--vus`, `.aiva-badge--lben`, `.aiva-badge--ben`: ACMG classification badges
- `.tier-free`, `.tier-trial`, `.tier-plus`, `.tier-pro`: subscription tier badges
- `.aiva-feature`, `.aiva-card`, `.aiva-quicklink`: landing page layout components
