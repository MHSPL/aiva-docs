---
title: Analysis Hub
description: Use AIVA's Analysis Hub to run category-based analyses with customizable layouts and multiple analysis panels in a unified workspace.
---

# Analysis Hub

The Analysis Hub is a dedicated workspace for running structured, category-based analyses on your variant data. It provides a flexible layout system where you can arrange multiple analysis panels side by side, enabling comprehensive variant interpretation in a single view.

---

## Overview

Unlike the free-form chat or the data table view, the Analysis Hub organizes your analysis into predefined **categories**, each containing specialized **analysis cards** that target specific aspects of variant interpretation.

Key concepts:

- **Categories**: Groupings of related analysis types (e.g., Clinical Significance, Pharmacogenomics, Protein Function). See [Categories](categories.md).
- **Analysis Cards**: Individual analysis panels within a category (e.g., PGx Card, Protein Interactions, Pathway Analysis). See [Analysis Cards](analysis-cards.md).
- **Layout Management**: Arrange, resize, and save panel layouts to match your workflow.

---

## Accessing the Analysis Hub

1. Navigate to a sample from the [Samples](../samples/index.md) list.
2. Select the **Analysis** tab or view.
3. The Analysis Hub opens with the default category and layout.

---

## Layout Management

The Analysis Hub supports flexible panel layouts:

### Arranging Panels

- **Drag and drop** panels to reposition them within the workspace.
- **Resize** panels by dragging their edges or corners.
- **Maximize** a panel to full width for detailed examination.
- **Minimize** panels you do not need at the moment.

### Saving Layouts

- Your panel arrangement is saved automatically per category.
- Switch between categories and return to find your layout preserved.
- Reset to the default layout at any time from the layout menu.

### Multiple Panels

Run several analysis cards simultaneously:

- View protein interactions alongside pharmacogenomic data.
- Compare pathway analysis with phenotype associations.
- Monitor multiple aspects of a variant's interpretation in parallel.

---

## Working with the Analysis Hub

### Selecting a Category

1. Use the category selector at the top of the Analysis Hub.
2. Choose from available categories or [create a custom category](categories.md).
3. The workspace loads the analysis cards associated with that category.

### Running an Analysis

1. Select an analysis card from the category.
2. Configure any required inputs (e.g., gene name, variant identifier, phenotype terms).
3. The card executes the analysis and displays results inline.
4. Interact with results. Click on genes, variants, or drugs for more detail.

### Combining Analyses

The Analysis Hub is designed for multi-faceted interpretation:

- Start with a broad category (e.g., Clinical Significance) to identify key variants.
- Switch to a specialized category (e.g., Pharmacogenomics) for targeted analysis.
- Use the [AIVA Chat](../aiva-chat/index.md) alongside the Analysis Hub for AI-assisted interpretation.

---

## Analysis Hub and Other Features

The Analysis Hub integrates with other AIVA features:

- **Data Table**: Variants identified in analysis cards can be located in the [Data Table](../data-table/index.md) for detailed examination.
- **Variant Flagging**: Flag variants directly from analysis card results using the [flagging system](../collaboration/variant-flagging.md).
- **ACMG Classification**: Apply [ACMG criteria](acmg-classification.md) to variants surfaced by analysis cards.
- **Reports**: Include analysis findings in [clinical reports](../reports/index.md).

!!! tip "Use presets for efficiency"
    Pre-configured category presets are available for common workflows like clinical variant interpretation, pharmacogenomic analysis, and rare disease gene prioritization. See [Categories](categories.md) for details.
