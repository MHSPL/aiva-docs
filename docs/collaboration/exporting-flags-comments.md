---
title: Exporting Flags and Comments
description: Export flagged variants and comment threads from AIVA as CSV files for clinical reports, audit trails, and downstream analysis.
---

# Exporting Flags and Comments

AIVA allows you to export your variant flags and comment threads as structured CSV files. This is useful for clinical reporting, audit documentation, team handoffs, and downstream analysis in external tools.

---

## What Gets Exported

The export includes two categories of data:

### Flagged Variants

Each flagged variant is exported with:

| Field | Description |
|-------|-------------|
| **Variant identifiers** | CHROM, POS, REF, ALT, and any other key columns (Gene, rsID) for the variant. |
| **Flag category** | The assigned classification (Pathogenic, Likely Pathogenic, VUS, Likely Benign, Benign, or custom). |
| **Flagged by** | The user who applied the flag. |
| **Flag timestamp** | When the flag was applied or last updated. |

### Comments

Each comment is exported with:

| Field | Description |
|-------|-------------|
| **Variant identifiers** | CHROM, POS, REF, ALT to link the comment to its variant. |
| **Comment text** | The full text of the comment. |
| **Author** | The user who wrote the comment. |
| **Timestamp** | When the comment was posted. |
| **Thread structure** | Indication of whether the comment is a top-level comment or a reply, preserving the conversation hierarchy. |

---

## How to Export

1. Open the sample or project containing the flagged variants and comments.
2. Click the **Export** button in the toolbar.
3. Select **Export Flags and Comments** from the export options.
4. The CSV file is generated and downloaded to your browser.

!!! info "Scope of the export"
    The export includes all flagged variants and all comments for the current sample. If you are working within a project, the export covers the active sample's flags and comments.

---

## Using Exported Data

### Clinical reports

Attach the exported CSV to clinical reports as supporting documentation. The flag categories, user attributions, and timestamps provide an audit trail showing who classified each variant and when.

### Team handoffs

When transferring a case to another team or institution, the exported flags and comments provide a complete record of the review process, ensuring continuity of interpretation.

### External analysis

Import the CSV into spreadsheet applications (Excel, Google Sheets) or statistical tools (R, Python) for further analysis, visualization, or integration with other data sources.

### Audit and compliance

The timestamped, user-attributed export supports compliance requirements by documenting the variant review process. Each flag and comment is traceable to a specific user and time.

---

## Tips

- **Export periodically**: For long-running projects, export flags and comments at regular intervals to maintain backup records outside of AIVA.
- **Review before exporting**: Check the table view with flag filters applied to confirm that all relevant variants are flagged before generating the export.
- **Combine with table view export**: For a complete picture, export both the [filtered table view](../data-table/exporting-data.md) and the flags/comments. The variant identifiers (CHROM, POS, REF, ALT) can be used to join the two exports in a spreadsheet or analysis tool.
