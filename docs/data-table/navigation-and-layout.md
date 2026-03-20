---
title: Navigation and Layout
description: Customize the data table layout using the column chooser, drag-and-drop reordering, column resizing, and sorting.
---

# Navigation and Layout

AIVA's data table gives you full control over which columns are visible, their order, their width, and how data is sorted. This page covers all layout customization options.

---

## Column Chooser

The column chooser is a panel that lists every available column for the current sample. Use it to control which columns appear in the table and in what order.

### Opening the Column Chooser

1. Open a sample in the data table view.
2. Click the **Columns** button in the table toolbar.
3. The column chooser panel opens, displaying all available columns with checkboxes.

### Showing and Hiding Columns

- **Check** a column name to add it to the table.
- **Uncheck** a column name to remove it from the table.

Changes take effect immediately. Hidden columns are not removed from the dataset; they are simply not displayed.

!!! info "VCF and annotation columns"
    For VCF files, columns include standard fields (CHROM, POS, REF, ALT, QUAL, FILTER) plus any INFO subfields parsed from the file. If Small Variant Annotation was applied, CSQ subfields such as `Gene`, `Consequence`, `IMPACT`, `SIFT`, and `PolyPhen` also appear as individual columns.

### Reordering Columns

Columns can be reordered using drag-and-drop within the column chooser:

1. Open the column chooser.
2. Click and hold on a column name.
3. Drag the column to the desired position in the list.
4. Release to drop the column in its new position.

The table updates immediately to reflect the new column order.

---

## Column Resizing

To adjust the width of any column directly in the table:

1. Hover over the right border of a column header until the resize cursor appears.
2. Click and drag left or right to narrow or widen the column.
3. Release to set the new width.

Column resizing is useful when cell content is truncated or when you want to give more space to columns with long values, such as INFO or consequence fields.

---

## Sorting

Click any column header to sort the table by that column:

1. **First click**: Sorts ascending (A to Z, lowest to highest).
2. **Second click**: Sorts descending (Z to A, highest to lowest).
3. **Third click**: Removes the sort and returns to the default order.

A sort indicator arrow appears in the column header to show the current sort direction.

!!! note "Server-side sorting"
    Sorting is performed server-side against the full dataset, not just the rows currently visible on screen. This ensures accurate results even for datasets with millions of rows.

---

## Pagination Controls

The data table uses server-side pagination to manage large datasets efficiently. Pagination controls are located at the bottom of the table.

- **Page size selector**: Choose how many rows to display per page. Common options include 25, 50, 100, and 250 rows.
- **Page navigation**: Use the previous/next buttons or jump to a specific page number.
- **Row count**: The total number of rows matching the current filters is displayed alongside the pagination controls.

!!! tip "Balancing page size and performance"
    Smaller page sizes load faster. For initial exploration, start with 25 or 50 rows per page. Increase the page size when you need to scan more data at once.

---

## Practical Tips

- **Start with key columns**: For VCF data, a useful starting layout includes CHROM, POS, REF, ALT, Gene, Consequence, SIFT, PolyPhen, and gnomAD allele frequency. Use the column chooser to set this up quickly.
- **Wide columns for INFO fields**: INFO subfields and consequence annotations can contain long values. Resize these columns or hide ones you do not need.
- **Sort to prioritize**: Sort by QUAL descending to see highest-confidence calls first, or by allele frequency ascending to find rare variants.
