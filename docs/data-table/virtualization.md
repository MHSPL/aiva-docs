---
title: Virtualization and Large Datasets
description: How AIVA uses row virtualization and server-side pagination to handle datasets with millions of rows.
---

# Virtualization and Large Datasets

Genomic datasets can be very large. A whole-genome sequencing VCF file may contain millions of variant calls, and annotated files can have dozens of columns per row. AIVA is built to handle these volumes without degrading browser performance.

---

## Row Virtualization

AIVA uses **row virtualization** (also called windowed rendering) to keep the table view responsive regardless of dataset size. Here is how it works:

- The table only renders the rows currently visible in the viewport, plus a small buffer above and below for smooth scrolling.
- As you scroll, rows entering the viewport are rendered and rows leaving the viewport are removed from the DOM.
- This means the browser never needs to manage millions of DOM nodes at once, keeping memory usage low and interactions snappy.

!!! info "What this means for you"
    You can scroll through a dataset with 10 million or more rows as smoothly as a dataset with 100 rows. There is no need to paginate through results one page at a time if you prefer to scroll. The table handles it.

---

## Server-Side Pagination

In addition to virtualization, the table view uses **server-side pagination** to avoid loading the entire dataset into the browser at once:

- When you navigate to a page or scroll to a new section, the table fetches only the rows needed from the server.
- **Filtering** is performed server-side, so filter operations run against the full dataset in the database rather than in the browser.
- **Sorting** is also server-side, ensuring sort order is correct across all rows, not just the loaded subset.
- **Configurable page sizes** let you balance between data density and load time. Smaller page sizes (25-50 rows) load faster; larger sizes (100-250 rows) reduce the number of fetches during scrolling.

---

## How Data Is Stored

AIVA uses high-speed bulk loading to ingest variant data. This architecture provides several advantages for large datasets:

- **Fast ingestion**: A VCF file with millions of variants is parsed and loaded in minutes, not hours.
- **Indexed queries**: Columns commonly used for filtering (CHROM, POS, Gene, Consequence, allele frequency) are indexed for fast lookups.
- **Efficient aggregation**: Server-side count, sum, and grouping operations run directly in the database, so the AI assistant and table view can summarize large datasets without transferring all rows to the browser.

---

## Performance Considerations

### Browser performance

| Factor | Impact | Recommendation |
|--------|--------|----------------|
| Number of visible columns | More columns increase rendering cost per row | Hide columns you do not need using the [column chooser](navigation-and-layout.md#column-chooser) |
| Page size | Larger pages mean more rows rendered | Start with 50 rows; increase if your hardware handles it well |
| Active filters | Filters reduce the working set | Apply filters to narrow down data before browsing |

### Network performance

- Each page fetch is a single HTTP request. On a stable connection, page transitions are near-instant.
- Slow or unreliable connections may cause brief loading states between pages. Reducing page size helps in these scenarios.

---

## Working with Very Large Datasets

For datasets exceeding one million rows, consider the following workflow:

1. **Filter first**: Apply [filters](filtering.md) on key columns (e.g., chromosome, gene, consequence type, allele frequency) to reduce the visible result set to a manageable size.
2. **Use the AI assistant**: Ask [AIVA](../aiva-chat/index.md) to summarize or count variants matching your criteria. The AI runs SQL queries directly against the full dataset without loading it into the browser.
3. **Export subsets**: Once you have identified the variants of interest, [export](exporting-data.md) the filtered subset as a CSV for external analysis.
4. **Adjust page size**: If you need to browse the full dataset, use a moderate page size (50-100) and rely on the scroll-based virtualization to navigate.

!!! tip "Let AIVA do the heavy lifting"
    For analytical questions like "How many pathogenic variants are on chromosome 17?" or "What is the distribution of consequence types?", asking AIVA is faster than scrolling and filtering manually. AIVA queries the database directly and returns results in seconds.
