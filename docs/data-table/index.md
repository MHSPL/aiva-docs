---
title: Data Table
description: Overview of AIVA's high-performance data table for exploring, filtering, and exporting genomic variant data at scale.
---

# Data Table

The AIVA data table is the primary interface for exploring your uploaded genomic data. Built on TanStack Table with row virtualization, it handles datasets ranging from a handful of variants to over ten million rows without sacrificing responsiveness.

---

## Key Capabilities

| Capability | Description |
|------------|-------------|
| **Virtualized rendering** | Only visible rows are rendered in the DOM, keeping the interface fast regardless of dataset size. |
| **Column chooser** | Drag-and-drop panel to show, hide, and reorder columns to match your workflow. |
| **Advanced filtering** | Per-column filters with support for text, numeric ranges, date ranges, and multi-select values. |
| **Server-side pagination** | Configurable page sizes with server-side data fetching for large datasets. |
| **Sorting** | Click any column header to sort ascending or descending. |
| **Column resizing** | Drag column borders to adjust widths for readability. |
| **CSV export** | Download the current filtered and sorted view as a CSV file. |

---

## VCF-Specific Columns

When you upload a VCF file, AIVA automatically parses and displays standard VCF fields:

- **CHROM** -- Chromosome identifier
- **POS** -- Genomic position
- **REF** -- Reference allele
- **ALT** -- Alternate allele(s)
- **QUAL** -- Variant quality score
- **FILTER** -- Filter status (PASS, low quality, etc.)
- **INFO subfields** -- Individual INFO fields are broken out into separate, sortable columns

If Small Variant Annotation was applied during upload, additional CSQ (consequence) columns are available, including gene symbol, consequence type, impact, SIFT and PolyPhen predictions, allele frequencies, and more. See [Small Variant Annotation](../samples/small-variant-annotation.md) for details on how these columns are generated.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Navigation and Layout

Use the column chooser to show, hide, and reorder columns. Resize columns and sort data by clicking headers.

[:octicons-arrow-right-24: Navigation and Layout](navigation-and-layout.md)

</div>

<div class="card" markdown>

### Filtering

Apply advanced per-column filters including text search, numeric ranges, date ranges, and multi-select dropdowns.

[:octicons-arrow-right-24: Filtering](filtering.md)

</div>

<div class="card" markdown>

### Exporting Data

Download your filtered and sorted data as a CSV file for use in external tools and reports.

[:octicons-arrow-right-24: Exporting Data](exporting-data.md)

</div>

<div class="card" markdown>

### Virtualization

Learn how AIVA handles datasets with millions of rows using row virtualization and server-side pagination.

[:octicons-arrow-right-24: Virtualization](virtualization.md)

</div>

</div>

---

## Accessing the Data Table

The data table is available in two contexts:

1. **Sample view** -- Select any sample from your sample list to open its data in the table.
2. **Tertiary Analysis** -- The [Analysis](../analysis/tertiary-analysis.md) view displays the data table alongside an integrated AI chat panel for side-by-side exploration.

!!! tip "Customize your default view"
    Use the column chooser to set up a layout that matches your analysis workflow, then rely on per-column filters to zero in on variants of interest. The table remembers your column selections within a session.
