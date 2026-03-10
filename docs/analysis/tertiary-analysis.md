---
title: Tertiary Analysis
description: Perform per-sample tertiary analysis in AIVA with a side-by-side data table and AI chat workspace.
---

# Tertiary Analysis

Tertiary analysis in AIVA provides a unified workspace where the data table and AI chat are displayed side by side. This layout is designed for focused, per-sample variant interpretation -- you can filter, sort, and flag variants in the table while simultaneously querying AIVA for context, literature, and computational analysis.

---

## Accessing Tertiary Analysis

1. Navigate to the **Analysis** section from the main navigation.
2. Select a sample from the sample list.
3. The tertiary analysis view opens with two panels:
   - **Left panel**: The [Data Table](../data-table/index.md) displaying the sample's variant data.
   - **Right panel**: An [AIVA Chat](../aiva-chat/index.md) session scoped to the selected sample.

---

## Layout and Workflow

The side-by-side layout enables a continuous interpretation workflow:

### Data Table Panel

The left panel provides the full data table experience:

- **All columns** are available via the [column chooser](../data-table/navigation-and-layout.md#column-chooser), including VCF fields, INFO subfields, and Variant Effect Prediction / Structural Variant Annotation columns.
- **Filtering** lets you narrow the variant list using [text, numeric, date, and multi-select filters](../data-table/filtering.md).
- **Sorting** by any column to prioritize variants of interest.
- **Variant flagging** directly in the table to mark variants as Pathogenic, VUS, Benign, etc. See [Variant Flagging](../collaboration/variant-flagging.md).
- **Threaded comments** on individual variants for discussion and documentation. See [Threaded Comments](../collaboration/threaded-comments.md).
- **ACMG classification** accessible from the variant row for evidence-based assessment. See [ACMG Classification](acmg-classification.md).

### AI Chat Panel

The right panel provides a chat session connected to the selected sample's data:

- AIVA can query the sample's data directly using the [Genomic Data Query tool](../aiva-chat/ai-tools.md#genomic-data-query).
- Ask questions about specific variants visible in the table, or request summaries across the entire dataset.
- Use [Variant Annotation](../aiva-chat/ai-tools.md#variant-annotation) for real-time ClinVar, gnomAD, and prediction score lookups.
- Search literature with the [Biomedical Literature](../aiva-chat/ai-tools.md#biomedical-literature) tool and the web for evidence.
- Generate plots and run statistical tests with the [Code Interpreter](../aiva-chat/ai-tools.md#code-interpreter).

!!! tip "Refer to table data in your queries"
    You can reference specific variants visible in the table when asking AIVA questions. For example: "What is the ClinVar classification for the BRCA1 variant at position 41245466?" AIVA looks up the answer using its tools.

---

## Typical Tertiary Analysis Workflow

### Step 1: Initial filtering

Apply filters to reduce the variant list to candidates of interest:

1. Filter `FILTER` column to `PASS` to exclude low-quality calls.
2. Filter by allele frequency (e.g., gnomAD AF < 0.01) to focus on rare variants.
3. Filter by consequence type (e.g., missense, frameshift, stop gained) to focus on functional variants.

### Step 2: Review and flag

Scroll through the filtered variants and flag those requiring attention:

1. Review each variant's annotation columns (Gene, Consequence, SIFT, PolyPhen, ClinVar).
2. Flag variants using the appropriate category (Pathogenic, VUS, etc.).
3. Add comments to document your initial impressions.

### Step 3: AI-assisted deep dive

For each flagged variant, use AIVA to gather additional evidence:

1. Ask AIVA to look up ClinVar and gnomAD data for the variant.
2. Request a literature search for the gene and associated conditions.
3. Query the knowledge graph for drug-target interactions if relevant.
4. Check for related clinical trials.

### Step 4: Formal classification

For variants requiring a formal assessment, open the [ACMG classifier](acmg-classification.md) and apply criteria based on the evidence gathered.

### Step 5: Export

Export your flagged and classified variants with [comments](../collaboration/exporting-flags-comments.md) for inclusion in clinical reports or team review.

---

## Tips

- **Filter aggressively first**: Reduce the variant list to a manageable size before starting detailed review. Most samples contain thousands of variants, but only a fraction are clinically relevant.
- **Use AIVA for repetitive lookups**: Instead of manually checking ClinVar or gnomAD for each variant, ask AIVA to batch-query or look up individual variants as you encounter them.
- **Document as you go**: Add comments and flags during review rather than after. This creates a real-time record of your interpretation process.
