---
title: Exporting Data
description: Export filtered and sorted variant data from AIVA as CSV files for downstream analysis and reporting.
---

# Exporting Data

AIVA allows you to export data from the data table as a CSV file. The export respects your current filters, sorting, and column selections, giving you a clean extract for downstream use in spreadsheets, statistical tools, or clinical reports.

---

## How to Export

1. Open a sample in the data table.
2. Apply any desired [filters](filtering.md), [sorting](navigation-and-layout.md#sorting), and [column selections](navigation-and-layout.md#column-chooser).
3. Click the **Export CSV** button in the table toolbar.
4. The CSV file is generated and downloaded to your browser's default download location.

---

## What Gets Exported

The exported CSV includes:

| Aspect | Behavior |
|--------|----------|
| **Columns** | Only the columns currently visible in the table are included in the export. Hidden columns are excluded. |
| **Rows** | Only rows matching all active filters are included. If no filters are applied, the entire dataset is exported. |
| **Sort order** | Rows are exported in the current sort order. |
| **Column headers** | The first row of the CSV contains column names as displayed in the table. |

!!! warning "Large exports"
    Exporting a dataset with millions of rows may take time to generate. Consider applying filters to reduce the export size if you only need a subset of the data.

---

## Common Export Scenarios

### Exporting flagged variants

If you have [flagged variants](../collaboration/variant-flagging.md) and want to export only those:

1. Apply a filter on the flag column to include only flagged rows.
2. Click **Export CSV** to download the flagged subset.

Alternatively, use the dedicated [flag and comment export](../collaboration/exporting-flags-comments.md) feature for a structured export that includes flag categories and comment threads.

### Exporting for clinical review

1. Set up columns relevant to clinical review: CHROM, POS, REF, ALT, Gene, Consequence, ClinVar significance, gnomAD allele frequency, SIFT, PolyPhen.
2. Filter to `PASS` variants with allele frequency below your threshold.
3. Sort by clinical significance or gene name.
4. Export to CSV and attach to a clinical report or share with your review team.

### Exporting for external bioinformatics tools

For tools that expect specific column formats, use the column chooser to arrange and limit columns to match the expected input. Export the CSV and use it directly as input to your pipeline.

---

## Tips

!!! tip "Preview before exporting"
    Review the data table after applying filters to confirm the result set looks correct before initiating an export. Check the row count at the bottom of the table to verify the expected number of records.

- The CSV export uses UTF-8 encoding and comma delimiters.
- Columns with commas or special characters in their values are properly quoted.
- Date and timestamp values are exported in ISO 8601 format.
