---
title: Clinical Data Integration
description: Workflows for cross-referencing clinical metadata with genomic data, including family-based analysis, segregation workflows, and multi-family comparisons.
---

# Clinical data integration

AIVA supports uploading clinical metadata (CSV or TSV) alongside VCF files. If your clinical data is in an Excel spreadsheet, export it as CSV or TSV before uploading. This lets you cross-reference phenotypes, family IDs, affected status, and other clinical information with your variant data within the same conversation.

---

## Uploading clinical data

Upload your clinical data as CSV or TSV as a separate sample with a descriptive name (e.g., "clinical_data"). AIVA parses the headers and makes all columns queryable, including custom columns like PEDID (family ID), affected status, or phenotype terms.

!!! tip "Naming matters"
    Give your clinical data file a clear name like "cohort_clinical_data" so you can easily distinguish it from your VCF samples when using `@samples:` mentions.

---

## Cross-referencing clinical and genomic data

The key workflow is to query your clinical data first, then use that context to query variants. AIVA carries the context forward, so it knows which sample IDs and family IDs you are interested in.

**Step 1: Query the clinical data**

> "@samples:clinical_data I'm interested in families 1 and 2. Can you find info about them?"

This searches for the family IDs, sample IDs, and any other information in those rows.

**Step 2: Query the variant data using that context**

> "@samples:multisample_vcf Can you count rare and high/moderate impact variants in LPL shared between the mentioned families?"

AIVA uses the context from the previous prompt (which families, which sample IDs) to filter the variant data.

!!! info "Linking clinical and genomic data"
    For AIVA to cross-reference clinical and genomic data, the two datasets need a shared identifier. This is typically the sample name or a subject ID column that matches between your clinical file and the sample columns in your VCF. Mention both datasets in the conversation so AIVA can join the information.

---

## Family-based analysis workflows

AIVA supports several family comparison patterns. Here are prompt templates for each.

### Comparing within a single family

> "@samples:clinical_data List all members of family FAM003 and their affected status."

> "@samples:cohort_vcf Find rare variants in LPL where the affected members of FAM003 carry a heterozygous or homozygous alt genotype but the unaffected members are homozygous reference."

### Comparing between two families

> "@samples:clinical_data I'm interested in families FAM001 and FAM003. List the affected members of each."

> "@samples:cohort_vcf Find rare, high-impact variants that are shared between affected members of FAM001 and FAM003 but absent in unaffected members."

### Comparing among a group of families

> "@samples:clinical_data Which families have members affected with seizure phenotypes?"

> "@samples:cohort_vcf For the affected members across those families, count rare variants in epilepsy-associated genes. Break down by family."

---

## Complete worked example

**Scenario**: You have a joint-called VCF with 40 samples from 10 families, and a clinical Excel file with columns for PEDID (family ID), sample ID, affected status, and phenotype terms.

1. "@samples:clinical_data Summarize this file. How many families and individuals are there, and how many are affected?"
2. "@samples:clinical_data List the affected individuals in family FAM003 along with their phenotype terms."
3. "@samples:cohort_vcf Find all variants in SCN1A where the affected members of FAM003 carry a heterozygous or homozygous alt genotype but the unaffected members are homozygous reference. Filter for PASS and read depth above 20."
4. "Classify those segregating variants using ACMG criteria."
5. "Search the biomedical literature for the top candidate variant in the context of the phenotypes listed for this family."

!!! tip "Segregation analysis"
    When asking for variants that segregate with disease status, be explicit about the expected inheritance pattern. For example: "Find variants where all affected members are heterozygous and all unaffected members are homozygous reference, consistent with autosomal dominant inheritance."

---

## Next steps

- [Multi-sample analysis](multi-sample-analysis.md): Querying multi-sample VCFs for per-sample and cohort-wide results
- [Upload strategy](upload-strategy.md): Choosing between single and multiple VCF uploads
- [AI Tools reference](../aiva-chat/ai-tools.md): Full documentation for the Genomic Data Query tool
