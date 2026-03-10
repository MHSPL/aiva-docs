---
title: Analysis Categories
description: Create and manage custom analysis categories in AIVA's Analysis Hub, with presets for common clinical and research workflows.
---

# Analysis Categories

Categories organize the Analysis Hub into focused workspaces, each containing a curated set of [analysis cards](analysis-cards.md) relevant to a specific aspect of variant interpretation. AIVA provides built-in presets for common workflows and allows you to create custom categories tailored to your needs.

---

## Built-In Category Presets

AIVA includes pre-configured categories for common analysis workflows:

### Clinical Significance

Focus on variant pathogenicity assessment.

- ClinVar classification lookup
- Population frequency analysis (gnomAD)
- In silico prediction scores (CADD, SIFT, PolyPhen)
- ACMG criteria evaluation

### Pharmacogenomics

Explore drug-gene interactions and prescribing implications.

- PGx card with drug-variant interactions
- PharmGKB data lookup
- Metabolizer status prediction
- Prescribing guideline references

### Protein Function

Analyze the structural and functional impact of variants.

- Protein interaction networks
- Domain and structure mapping
- Conservation analysis
- Functional prediction scores

### Phenotype Analysis

Connect clinical phenotypes to candidate genes.

- Phenotype association cards
- Phenotype-Gene Prioritization integration
- HPO term mapping
- Gene-phenotype correlation

### Pathway Analysis

Explore biological pathway context for variants.

- Pathway membership lookup
- Network visualization
- Downstream effector analysis
- Drug target identification within pathways

---

## Creating a Custom Category

1. Open the Analysis Hub.
2. Click **New Category** or the **+** button in the category selector.
3. Enter a **category name** and optional **description**.
4. Select the **analysis cards** to include in this category from the available card library.
5. Arrange the cards in your preferred layout.
6. Click **Save**.

The custom category appears in the category selector alongside the built-in presets.

---

## Managing Categories

### Editing a Category

1. Select the category you want to edit.
2. Click the category settings icon.
3. Add or remove analysis cards.
4. Rename the category or update the description.
5. Save your changes.

### Reordering Categories

Drag categories in the category selector to change their display order.

### Deleting a Category

1. Select the category.
2. Click the category settings icon.
3. Select **Delete Category**.
4. Confirm the deletion.

!!! note "Built-in presets cannot be deleted"
    You can customize built-in presets (add or remove cards, change layout) but cannot delete them entirely. To restore a preset to its default configuration, use the **Reset to Default** option.

---

## Category Workflows

Categories are designed to support structured analysis workflows. A typical approach:

1. **Start with Clinical Significance** -- Assess pathogenicity of key variants.
2. **Move to Pharmacogenomics** -- Check for drug-gene implications.
3. **Explore Protein Function** -- Understand the molecular impact.
4. **Review Pathway Analysis** -- Place findings in biological context.
5. **Document in Reports** -- Use findings from each category in your [report](../reports/index.md).

---

## Tips

- **Create task-specific categories** -- If you regularly perform a specific type of analysis (e.g., hereditary cancer panel review), create a category with exactly the cards you need.
- **Share through projects** -- Custom categories created within a [project](../collaboration/projects.md) are available to all project members.
- **Combine with AIVA Chat** -- Use categories for structured analysis and [AIVA Chat](../aiva-chat/index.md) for ad-hoc questions and deep dives.
