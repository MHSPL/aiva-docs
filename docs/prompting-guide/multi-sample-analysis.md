---
title: Multi-sample Analysis
description: Prompting workflows for querying multi-sample VCFs, including per-sample breakdowns, gene-specific queries, and cohort-wide analysis.
---

# Multi-sample analysis

Multi-sample VCFs (joint-called cohorts, family trios, large panels) are common in clinical and research settings. AIVA queries these directly using SQL, where each sample's genotype is stored as a separate column. This means you can filter by genotype for any individual sample within a multi-sample file.

---

## Per-sample vs. cohort-wide results

When you query a multi-sample VCF, AIVA queries the combined table by default. You need to specify whether you want per-sample breakdowns or cohort-wide summaries.

| Goal | Prompt |
|------|--------|
| Cohort-wide count | "How many rare variants in LPL are in @samples:family_cohort?" |
| Per-sample breakdown | "For each sample in @samples:family_cohort, how many rare variants are in LPL?" |
| Specific samples | "List rare variants in LPL for samples 1, 10, 11, and 14 in @samples:family_cohort" |
| Shared variants | "Which rare variants in @samples:family_cohort are shared across samples 1, 10, 11, and 14?" |
| Private variants | "Which variants are unique to sample HG003 in @samples:family_cohort?" |

!!! info "Per-sample results"
    When you ask for per-sample breakdowns, AIVA will specify exactly which samples carry each variant. For example, if a rare variant on the LPL gene is present in samples 1, 10, 11, and 14, AIVA will list those sample IDs alongside the variant details. Results are not generalized; they are specific to each sample.

---

## Gene-specific queries on large cohorts

For cohorts with many samples, gene-specific queries are more efficient than genome-wide scans. Start narrow, then broaden if needed.

**Worked example:**

1. "How many variants in @samples:cohort_40 are in the LPL gene with gnomAD AF below 0.001? Make sure to filter for artifacts (PASS filter, read depth above 20)."
2. "Break that down by sample. Which samples carry those variants?"
3. "For the samples that have LPL variants, what are the variant consequences?"
4. "Classify the missense variants using ACMG criteria."

!!! tip "Quality filtering"
    Always ask AIVA to filter for quality when looking for rare variants. Include criteria like PASS filter status and minimum read depth to exclude sequencing artifacts from your results.

---

## Counting variants across samples

When working with a large cohort, it is helpful to start with summary counts before diving into specific variants. This avoids overwhelming output and helps you identify which samples or genes to focus on.

**Example workflow:**

> "How many rare variants are in LDL-related genes in each sample? List samples with counts."

If the counts are manageable, follow up:

> "List the rare variants for the top 5 samples with the highest counts."

!!! tip "Filter for artifacts"
    When asking for counts, include quality filters: "Make sure to filter for artifacts (PASS, read depth, etc.)." This ensures your counts reflect real variants, not sequencing noise.

---

## Comparing genotypes across samples

You can ask AIVA to compare genotypes for specific variants or genes across your cohort.

| Goal | Prompt |
|------|--------|
| Heterozygous carriers | "Which samples are heterozygous for variants in LPL in @samples:cohort_40?" |
| Homozygous alt | "Which samples in @samples:cohort_40 are homozygous alt for any variant in SCN1A?" |
| Genotype summary | "For the top 5 rare variants in BRCA1, show the genotype for each sample." |

---

## Next steps

- [Clinical data integration](clinical-data.md): Cross-reference clinical metadata with your multi-sample variant data
- [Upload strategy](upload-strategy.md): Choose between a single multi-sample VCF and individual per-sample VCFs
- [AI Tools reference](../aiva-chat/ai-tools.md): Full documentation for the Genomic Data Query tool
