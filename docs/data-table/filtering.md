---
title: Filtering
description: Apply advanced per-column filters to narrow down variant data using text, numeric, date range, and multi-select filters.
---

# Filtering

AIVA's table view provides advanced per-column filtering so you can isolate the variants that matter most. Filters are applied server-side against the full dataset, ensuring accurate results even on tables with millions of rows.

---

## Accessing Filters

Each column in the table view has its own filter control:

1. Locate the column you want to filter.
2. Click the filter icon in the column header, or open the filter row beneath the header row.
3. The appropriate filter input appears based on the column's data type.

---

## Filter Types

### Text Filters

Text filters apply to string-based columns such as CHROM, REF, ALT, Gene, and Consequence.

- **Contains**: Matches rows where the cell value contains the entered text.
- **Exact match**: Matches rows where the cell value is exactly equal to the entered text.
- **Starts with / Ends with**: Matches based on the beginning or end of the cell value.

**Example**: Filter the `Consequence` column to `missense_variant` to see only missense mutations.

### Numeric Filters

Numeric filters apply to columns with numerical data such as POS, QUAL, allele frequency, CADD score, and depth.

- **Equals**: Matches a specific number.
- **Greater than / Less than**: Matches values above or below a threshold.
- **Between**: Matches values within a specified range (inclusive).

**Example**: Filter `gnomAD_AF` to values less than `0.01` to find rare variants with a population allele frequency below 1%.

### Date Range Filters

Date range filters apply to date or timestamp columns when present in the dataset.

- Select a **start date** and **end date** to include only rows falling within the range.

### Multi-Select Filters

Multi-select filters apply to columns with a finite set of categorical values, such as FILTER status, Consequence type, or variant classification.

- A dropdown displays all unique values present in the column.
- **Check** one or more values to include rows matching any of the selected values.
- **Uncheck** values to exclude them.

**Example**: In the `FILTER` column, select only `PASS` to exclude filtered-out variants.

---

## Combining Filters

You can apply filters to multiple columns simultaneously. When multiple filters are active, they operate as a logical **AND**, meaning only rows that satisfy all active filters are displayed.

**Example workflow for finding clinically relevant rare variants**:

1. Filter `FILTER` to `PASS`.
2. Filter `gnomAD_AF` to less than `0.01`.
3. Filter `Consequence` to `missense_variant`, `frameshift_variant`, `stop_gained`.
4. Filter `SIFT` to `deleterious`.

The resulting view shows only passing, rare, functionally impactful variants predicted to be deleterious.

---

## Clearing Filters

- **Single column**: Click the clear button (X) next to the active filter input to remove that column's filter.
- **All filters**: Use the **Clear All Filters** button in the table toolbar to reset every filter at once.

---

## Filters and Other Table Features

!!! note "Filters interact with sorting, export, and pagination"
    - **Sorting**: Sorting applies within the filtered result set.
    - **Export**: CSV export downloads the filtered and sorted data, not the entire dataset. See [Exporting Data](exporting-data.md).
    - **Pagination**: Page counts and row totals update to reflect the filtered result set.
    - **Row count**: The total row count displayed at the bottom of the table reflects the number of rows matching all active filters.

---

## Tips for Effective Filtering

!!! tip "Start broad, then narrow"
    Apply one or two filters first to understand the data distribution, then add more filters to refine. This approach helps you avoid overly restrictive filter combinations that return zero results.

- **Use multi-select for consequence types**: Genomic datasets often contain many consequence types. Multi-select lets you pick the specific types relevant to your analysis without typing each one.
- **Combine frequency and prediction filters**: Pair gnomAD allele frequency filters with SIFT or PolyPhen prediction filters to quickly surface rare, potentially damaging variants.
- **Check filter counts**: After applying filters, check the updated row count to confirm you have a reasonable number of results before proceeding with downstream analysis.
