---
title: Querying Your Data
description: How to ask AIVA questions about your uploaded genomic data, understand how SQL queries work behind the scenes, and interpret results.
---

# Querying Your Data

One of AIVA's most powerful capabilities is querying your uploaded genomic data using natural language. Instead of writing SQL, you describe what you want in plain English, and AIVA translates your request into a database query, executes it, and presents the results.

---

## How It Works

When you ask a data-related question, AIVA uses the **Genomic Data Query tool** behind the scenes:

1. **You ask a question** in natural language (e.g., "How many variants in my sample have a CADD score above 20?").
2. **AIVA generates a SQL query** based on your question and the schema of your uploaded sample.
3. **The query executes** against the database where your parsed data is stored.
4. **Results are returned** and rendered as a formatted table, a summary, or a chart, depending on what best fits the answer.

!!! info "Schema awareness"
    AIVA knows the column names and data types of your uploaded samples. When you ask about "pathogenic variants" or "allele frequency," it maps your natural language terms to the correct database columns. For samples with Small Variant Annotation applied, this includes all annotation fields such as `Consequence`, `SYMBOL`, `SIFT`, `PolyPhen`, and `CADD_PHRED`.

---

## Example Queries

Here are practical examples grouped by common analysis tasks. Use these as starting points and adapt them to your specific data.

### Counting and Summarizing

| What You Ask | What AIVA Does |
|-------------|----------------|
| "How many variants are in my sample?" | Counts all rows in your sample table. |
| "How many variants are on chromosome 17?" | Filters by the CHROM column and counts matches. |
| "What is the breakdown of variant consequences?" | Groups variants by the Consequence column and returns counts for each category (missense, synonymous, frameshift, etc.). |
| "How many samples do I have uploaded?" | Queries the sample metadata to list all your uploaded datasets. |

### Filtering and Searching

| What You Ask | What AIVA Does |
|-------------|----------------|
| "Show me all pathogenic variants in BRCA1." | Filters by gene symbol and clinical significance columns. |
| "List variants with allele frequency below 0.01 in gnomAD." | Filters by the gnomAD allele frequency annotation field. |
| "Find all frameshift variants on chromosome 7." | Combines a consequence filter with a chromosome filter. |
| "Which variants have a CADD score above 25 and are classified as missense?" | Applies multiple filters across annotation columns. |

### Ranking and Prioritization

| What You Ask | What AIVA Does |
|-------------|----------------|
| "What are the top 10 most frequently mutated genes?" | Groups by gene, counts variants per gene, and sorts descending. |
| "Show me the 5 variants with the highest CADD scores." | Sorts by CADD score descending and limits to 5 results. |
| "Which genes have the most pathogenic variants?" | Combines a clinical significance filter with a group-by-gene aggregation. |

### Cross-Sample Analysis

| What You Ask | What AIVA Does |
|-------------|----------------|
| "Compare the variant counts between my two WES samples." | Queries both sample tables and presents a side-by-side comparison. |
| "Are there any variants shared between sample A and sample B?" | Performs a join or intersection query across two sample tables. |

---

## Understanding Results

AIVA presents query results in the format that best fits the data:

### Tables

For queries that return rows of data, AIVA renders an interactive table directly in the chat. You can scroll through the results and review individual records.

### Summary Statistics

For count or aggregation queries, AIVA provides a concise textual summary (e.g., "Your sample contains 42,387 variants, of which 1,204 are classified as pathogenic.").

### Charts and Visualizations

When a visual representation adds value, AIVA may use the **Code Interpreter** to generate charts. For example:

- "Plot the distribution of CADD scores" produces a histogram.
- "Show a bar chart of variants per chromosome" produces a bar plot.
- "Create a pie chart of variant consequences" produces a pie chart.

Charts are rendered inline in the conversation and can be viewed in full resolution.

!!! tip "Request specific visualizations"
    If you want a chart instead of a table (or vice versa), say so explicitly. For example: "Show me a bar chart of variant counts by gene" or "Give me this as a table, not a chart."

---

## Query Transparency

AIVA shows you the tool it used and provides a summary of the operation. This transparency allows you to:

- **Verify the query logic**: Confirm that the SQL query matches your intent.
- **Learn your data schema**: See which columns are available and how they are named.
- **Refine your questions**: If the results are not what you expected, adjust your question using the column names you see in the tool output.

---

## Tips for Effective Queries

### Be Specific About Your Sample

If you have multiple samples, specify which one you are asking about:

- "In the BRCA_panel sample, how many variants are pathogenic?"
- "For my WGS_patient_042 sample, show all stop-gain variants."

### Use Genomic Terminology

AIVA understands standard genomic terms. Use specific language for more precise results:

- "Missense variants" rather than "point mutations that change the amino acid."
- "gnomAD allele frequency" rather than "how common is this variant in the population."
- "CADD score" rather than "deleteriousness score."

### Iterate and Refine

Start with a broad query and narrow down:

1. "How many pathogenic variants are in my sample?": Get the overall count.
2. "Which genes are they in?": See the gene distribution.
3. "Show me the ones in BRCA1 and BRCA2 with their ClinVar annotations.": Drill into specific genes.

### Combine with Other Tools

AIVA can chain multiple tools in a single response. For example:

- "Find all pathogenic BRCA1 variants in my sample and search PubMed for recent publications about them." This uses **Genomic Data Query** for the data query and **Biomedical Literature** for the literature search.
- "Calculate the average CADD score per consequence type and plot it as a bar chart." This uses **Genomic Data Query** for the aggregation and **Code Interpreter** for the chart.

---

## Limitations

!!! note "What AIVA cannot do with data queries"

    - **Modify your data**: AIVA has read-only access to your sample data. It cannot insert, update, or delete rows.
    - **Access other users' data**: Queries are scoped to samples you own or that are shared with you through a [project](../collaboration/projects.md). AIVA cannot access data belonging to other accounts.
    - **Perform real-time variant calling**: AIVA queries pre-processed data. It does not run alignment or variant calling pipelines.

---

## Next Steps

- [:octicons-arrow-right-24: Explore all AI tools](ai-tools.md)
- [:octicons-arrow-right-24: Annotate variants on demand](variant-annotation-tool.md)
- [:octicons-arrow-right-24: Search biomedical literature](biomedical-literature.md)

- [:octicons-arrow-right-24: Run custom Python analysis](code-interpreter.md)
- [:octicons-arrow-right-24: See example workflows](example-workflows.md)
