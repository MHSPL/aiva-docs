---
title: Upload Strategy and Model Tips
description: Guidance on choosing between single multi-sample VCFs and individual per-sample VCFs, and selecting the right AI model for your analysis.
---

# Upload strategy and model tips

How you upload your data and which model you choose both affect the quality and speed of your analysis. This page covers the tradeoffs to help you make the right choice.

---

## Single vs. multiple VCF uploads

When working with multiple samples, you can upload a single multi-sample VCF or individual per-sample VCFs. Each approach has tradeoffs.

| Consideration | Single multi-sample VCF | Individual per-sample VCFs |
|---------------|------------------------|---------------------------|
| **Cross-sample queries** | All samples in one table; mention families or sample names and AIVA scans a single table | Must tag each sample separately (`@samples:s1, @samples:s2, ...`) and AIVA joins them; tagging many samples is tedious and joins are slower |
| **Per-sample analysis** | Must specify sample name in genotype filters | Each sample is its own table; simpler per-sample queries |
| **Upload and processing** | One upload, one processing job | Multiple uploads, one per file |
| **Query performance** | Every query scans the full table (10M+ rows for WGS cohorts), even if you only need one sample | Each table is 100K to 5M rows, so per-sample queries are fast; cross-sample queries require joining multiple tables which adds overhead |

!!! tip "Split by sample"
    If you upload a multi-sample VCF and want per-sample tables, use the **Split by sample** checkbox during upload. This creates a separate table for each sample (up to 100 samples). See [VCF Upload](../samples/vcf-upload.md) for details.

### Recommendations

**Use a single multi-sample VCF when:**

- Cross-sample comparison is the primary goal (shared variants, segregation analysis, family-based queries)
- You want the convenience of referencing one table without tagging individual samples
- Your data is WES, where the combined table size is manageable

**Use individual per-sample VCFs when:**

- Each sample needs independent analysis
- You are working with WGS data, where scanning a single sample table (100K to 5M rows) is much faster than scanning a combined multi-sample table (10M+ rows)
- You want faster per-sample queries and are okay with the extra effort of tagging samples for cross-sample comparisons

!!! info "Using individual VCFs with clinical data"
    When uploading samples individually, you can still use a clinical data file to help AIVA find the right tables. Name your VCF files consistently with the IDs in your clinical data. Then ask:

    "@samples:clinical_data I'm interested in families 1 and 2. Can you find info about them along with the variant table names?"

    AIVA will try to match sample IDs from the clinical data to your uploaded VCF table names.

---

## Model selection tips

The default model is **Claude Sonnet 4.6**, which handles most queries well. For complex multi-step analysis, consider switching to a more capable model.

| Scenario | Recommended model |
|----------|-------------------|
| Simple counts, filters, and lookups | Claude Sonnet 4.6 (default, fast) |
| Multi-step prompt chains with many follow-ups | Claude Opus 4.6 or Gemini 3.1 Pro |
| Cross-referencing clinical + genomic data | Claude Opus 4.6 or Gemini 3.1 Pro |
| Large result set analysis | Gemini 3.1 Pro (1M token context window) |
| Exploratory questions | Start with Sonnet, switch to a more capable model when you find something worth investigating |

Claude Opus 4.6 and Gemini 3.1 Pro are thinking models that perform better on complex reasoning tasks. If you feel the default model is not giving you good results on a multi-step analysis, switching to one of these models often helps.

!!! info "Switching models"
    You can switch models at any time during a conversation. Previous messages remain unchanged; only new messages use the selected model. See [Model Selection](../aiva-chat/model-selection.md) for details.

---

## Next steps

- [Multi-sample analysis](multi-sample-analysis.md): Querying multi-sample VCFs for per-sample and cohort-wide results
- [Clinical data integration](clinical-data.md): Cross-reference clinical metadata with variant data
- [VCF Upload](../samples/vcf-upload.md): Upload and configure your variant data
