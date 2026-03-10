---
title: Code Interpreter
description: Use AIVA's sandboxed Python environment with pandas, numpy, scipy, and matplotlib for statistical analysis, custom calculations, and data visualization.
---

# Code Interpreter

The Code Interpreter gives AIVA access to a sandboxed Python execution environment equipped with scientific computing libraries. It enables statistical analysis, custom calculations, and publication-quality visualizations directly within the chat.

---

## Available Libraries

| Library | Version | Use Cases |
|---------|---------|-----------|
| **pandas** | Latest | Data manipulation, filtering, grouping, aggregation, pivot tables |
| **numpy** | Latest | Numerical computing, array operations, linear algebra |
| **scipy** | Latest | Statistical tests, distributions, scientific computing |
| **matplotlib** | Latest | Charts, plots, histograms, scatter plots, heatmaps |

---

## Capabilities

### Statistical Analysis

- **Hypothesis testing** -- t-tests, chi-squared tests, Fisher's exact test, Mann-Whitney U, Kruskal-Wallis.
- **Descriptive statistics** -- Mean, median, standard deviation, percentiles, distributions.
- **Correlation analysis** -- Pearson, Spearman, and Kendall correlation coefficients.
- **Regression** -- Linear regression, logistic regression, curve fitting.

### Data Visualization

- **Histograms** -- Distribution of allele frequencies, quality scores, or any numeric field.
- **Bar charts** -- Gene counts, variant categories, consequence types.
- **Scatter plots** -- Correlations between numeric fields (e.g., CADD score vs. allele frequency).
- **Box plots** -- Compare distributions across groups (e.g., quality scores by chromosome).
- **Heatmaps** -- Correlation matrices, co-occurrence patterns.
- **Pie charts** -- Proportional breakdowns of categorical data.

### Custom Calculations

- Derive new metrics from your data.
- Apply custom filtering logic beyond what SQL supports.
- Transform and reshape data for specialized analyses.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Distribution plot | "Plot the allele frequency distribution for all variants in my sample." |
| Statistical test | "Run a Fisher's exact test comparing pathogenic variants on chromosome 13 vs. chromosome 17." |
| Bar chart | "Create a bar chart showing the top 20 genes by variant count." |
| Correlation | "Is there a correlation between CADD score and gnomAD allele frequency in my data?" |
| Summary statistics | "Calculate summary statistics for the quality scores in my sample." |
| Custom analysis | "For each gene with more than 5 variants, calculate the ratio of missense to synonymous variants." |

---

## How It Works

1. You ask a question that requires computation or visualization.
2. AIVA writes Python code to perform the analysis.
3. The code executes in a secure, sandboxed environment with resource limits.
4. Results (text output, tables, or plots) are returned directly in the chat.

!!! info "Plots appear inline"
    Matplotlib charts are rendered as images directly in the conversation. You can view them at full resolution and download them without leaving the chat.

---

## Security and Isolation

The Code Interpreter runs in a multi-layer sandbox with the following protections:

- **Environment isolation** -- Code executes in a restricted environment separate from the AIVA backend.
- **Resource limits** -- CPU time, memory usage, and execution duration are capped to prevent abuse.
- **No network access** -- The Python environment cannot make outbound network requests.
- **No filesystem access** -- Code cannot read or write files outside the sandbox.
- **Pre-installed libraries only** -- Only the listed scientific libraries are available; arbitrary packages cannot be installed.

!!! note "Data access"
    The Code Interpreter does not have direct access to your database. To analyze your uploaded data with Python, AIVA first queries the data using the Genomic Data Query tool, then passes the results to the Code Interpreter. This happens automatically when you ask a question that requires both data retrieval and computation.

---

## Multi-Tool Workflows

The Code Interpreter is frequently the final step in a multi-tool pipeline:

1. **Genomic Data Query** fetches variant data from your sample.
2. **Code Interpreter** processes and visualizes the results.

Or:

1. **Variant Annotation** retrieves scores for a set of variants.
2. **Code Interpreter** plots the score distributions.

Or:

1. **Biomedical Literature** retrieves publication counts for genes.
2. **Code Interpreter** creates a bar chart comparing literature coverage.

You do not need to orchestrate these steps manually. A single prompt like "Plot the CADD score distribution for all missense variants in my sample" triggers the full pipeline automatically.

See [Example Workflows](example-workflows.md) for more multi-tool patterns.

---

## Tips for Best Results

- **Be specific about the visualization type** -- "Create a histogram" or "Make a scatter plot" helps AIVA choose the right chart.
- **Specify axes and labels** -- "Plot allele frequency on the x-axis and CADD score on the y-axis" produces clearer charts.
- **Request statistical details** -- "Include the p-value and confidence interval" ensures the output includes the numbers you need.
- **Ask for interpretation** -- "Run the test and explain what the result means" gets you both the computation and the context.
