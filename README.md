# AIVA User Guide

Public documentation site for the [AIVA](https://aivaportal.com) platform, built with [MkDocs Material](https://squidfund.github.io/mkdocs-material/).

**Live site:** [https://mhspl.github.io/aiva-docs/](https://mhspl.github.io/aiva-docs/)

## Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Start dev server
mkdocs serve
```

The site will be available at `http://127.0.0.1:8000`.

## Deployment

The site auto-deploys to GitHub Pages via GitHub Actions on every push to `main`.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting corrections or additions.

## Structure

```
docs/
  getting-started/     # Account setup, UI navigation, first upload, subscriptions
  samples/             # File uploads, cloud imports, annotation, job monitoring
  aiva-chat/           # AI assistant, tools, querying data, example workflows
  data-table/          # Navigation, filtering, exporting, large datasets
  analysis/            # Tertiary analysis, ACMG classification, pharmacogenomics
  collaboration/       # Projects, sharing, variant flagging, threaded comments
  reports/             # Clinical report generation, AI auto-fill, templates
  playbooks/           # Browsing, creating, sharing playbooks
  classification/      # Public ACMG/AMP variant classifier
  api/                 # API reference (keys, uploads, chat, classification, exports)
  compliance/          # HIPAA, audit trail
  admin/               # User management, announcements
  faq.md               # Frequently asked questions
  glossary.md          # Genomics terminology
  changelog.md         # Release notes
```
