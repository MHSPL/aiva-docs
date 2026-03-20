---
title: Analysis
description: Overview of AIVA's analysis capabilities including tertiary analysis, ACMG variant classification, and AI-assisted interpretation.
---

# Analysis

AIVA provides analysis tools that go beyond data exploration, supporting structured variant interpretation workflows used in clinical and research settings.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Tertiary Analysis

Analyze samples with the data table and AI chat side by side. Filter, flag, and interpret variants in a unified workspace.

[:octicons-arrow-right-24: Tertiary Analysis](tertiary-analysis.md)

</div>

<div class="card" markdown>

### ACMG Classification

Apply ACMG/AMP criteria to variants with an interactive evidence-based classifier. Auto-calculated five-tier classifications from Pathogenic to Benign.

[:octicons-arrow-right-24: ACMG Classification](acmg-classification.md)

</div>

</div>

---

## Analysis Workflow

A typical analysis workflow in AIVA proceeds through the following stages:

1. **Upload and annotate**: Upload a VCF file with optional [Small Variant Annotation](../samples/small-variant-annotation.md) or [Structural Variant Annotation](../samples/structural-variant-annotation.md).
2. **Explore in the data table**: Use the [Data Table](../data-table/index.md) to browse, filter, and sort variants.
3. **Tertiary analysis**: Open the [Tertiary Analysis](tertiary-analysis.md) view to work with the data table and AI chat simultaneously.
4. **Flag and comment**: [Flag variants](../collaboration/variant-flagging.md) of interest and add [comments](../collaboration/threaded-comments.md) documenting your interpretation.
5. **Classify**: Apply [ACMG criteria](acmg-classification.md) to variants requiring formal evidence-based classification.
6. **Export and report**: [Export](../collaboration/exporting-flags-comments.md) your findings and generate clinical reports.

---

## AI-Assisted Analysis

The [AIVA assistant](../aiva-chat/index.md) supports every stage of analysis:

- **Data queries**: Ask AIVA to find specific variants, count categories, or summarize patterns in your data.
- **Literature search**: Use AIVA to search biomedical literature, ClinVar, and the web for evidence relevant to specific variants or genes.
- **Knowledge graph**: Query the gene-protein-drug interaction graph for pathway analysis and drug-target relationships.
- **Statistical analysis**: Ask AIVA to run statistical tests or generate plots using the Code Interpreter.
- **Clinical trials**: Search for relevant clinical trials based on genes, conditions, or interventions.

See [AI Tools Reference](../aiva-chat/ai-tools.md) for a complete description of all tools available to AIVA.

!!! tip "Combine tools for comprehensive interpretation"
    For variant interpretation, a powerful pattern is to ask AIVA a compound question: "Look up ClinVar and gnomAD data for this variant, search for relevant literature, and check for related clinical trials." AIVA chains multiple tools to deliver a comprehensive answer.
