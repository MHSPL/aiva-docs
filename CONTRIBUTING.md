# Contributing to AIVA User Guide

Thank you for helping improve the AIVA documentation! We welcome contributions from the community.

## How to Contribute

### Reporting Issues

If you find inaccurate or unclear documentation, please [open an issue](https://github.com/MHSPL/aiva-docs/issues/new) describing:

- Which page has the issue (include a link)
- What is incorrect or confusing
- What the correct information should be (if known)

### Submitting Changes

1. **Fork** this repository
2. **Create a branch** for your changes: `git checkout -b fix/description-of-change`
3. **Make your edits** in the `docs/` directory
4. **Preview locally** (see below)
5. **Submit a pull request** with a clear description of your changes

### Local Preview

To preview the docs site locally:

```bash
# Install dependencies
pip install -r requirements.txt

# Start the dev server
mkdocs serve
```

The site will be available at `http://127.0.0.1:8000`.

## Writing Guidelines

- Use clear, concise language
- Write for clinical and research users who may not be software engineers
- Include step-by-step instructions where appropriate
- Use admonitions (`!!! tip`, `!!! warning`, `!!! info`) for callouts
- Add screenshots in `docs/assets/images/screenshots/{feature}/` when they help illustrate a workflow
- Cross-link to related pages using relative paths

## Style Conventions

- **Headings**: Use sentence case (e.g., "Uploading your first sample")
- **UI elements**: Bold (e.g., Click **Upload**)
- **Code/commands**: Use inline code backticks or code blocks
- **File formats**: Uppercase (e.g., VCF, CSV, TSV)
- **Feature names**: Use the product name (e.g., "AIVA Chat", not "the chatbot")

## Code of Conduct

Be respectful and constructive. We are building documentation to help the genomics community.
