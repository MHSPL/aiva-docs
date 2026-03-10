---
title: Variant Annotation Tool
description: Real-time variant lookups against ClinVar, gnomAD, CADD, SIFT, and PolyPhen-2 databases directly within AIVA Chat.
---

# Variant Annotation Tool

The Variant Annotation tool performs real-time lookups for individual variants against multiple curated genomic databases. Unlike batch annotation during upload (Variant Effect Prediction), this tool is used interactively during a conversation to retrieve detailed information about specific variants on demand.

---

## Databases Queried

| Database | Information Provided |
|----------|---------------------|
| **ClinVar** | Clinical significance classifications (Pathogenic, Likely Pathogenic, VUS, Likely Benign, Benign), review status, condition associations, submitter details |
| **gnomAD** | Population allele frequencies across global populations and subpopulations (African, East Asian, European, Latino, South Asian, and others) |
| **CADD** | Combined Annotation Dependent Depletion scores measuring variant deleteriousness on a Phred-like scale |
| **SIFT** | Prediction of whether an amino acid substitution affects protein function (Tolerated or Deleterious) with confidence scores |
| **PolyPhen-2** | Prediction of amino acid substitution impact on protein structure and function (Benign, Possibly Damaging, or Probably Damaging) |

---

## Query Formats

You can query variants using several identifier formats:

- **Gene and HGVS notation** -- `BRCA1 c.5266dupC`
- **Genomic coordinates** -- `chr17:41245466 G>A`
- **rsID** -- `rs80357906`
- **Gene name** (for general information) -- `TP53`

AIVA interprets the identifier and routes it to the appropriate databases.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Clinical significance | "What is the ClinVar classification for BRCA1 c.5266dupC?" |
| Population frequency | "Look up the gnomAD allele frequency for chr17:41245466 G>A." |
| Deleteriousness scores | "Get CADD, SIFT, and PolyPhen scores for chr7:117559590 T>G." |
| Comprehensive lookup | "Give me the full annotation for rs80357906 including ClinVar, gnomAD, and in silico predictions." |
| Multiple variants | "Look up ClinVar classifications for BRCA1 c.68_69delAG and BRCA2 c.5946delT." |

---

## Understanding the Results

### ClinVar Classification

ClinVar assigns one of five clinical significance tiers:

1. **Pathogenic** -- Strong evidence that the variant causes disease.
2. **Likely Pathogenic** -- Sufficient evidence to support a disease-causing role.
3. **Uncertain Significance (VUS)** -- Insufficient evidence to classify.
4. **Likely Benign** -- Evidence suggests the variant does not cause disease.
5. **Benign** -- Strong evidence that the variant is not disease-causing.

The review status (number of stars) indicates the level of evidence supporting the classification.

### gnomAD Frequencies

Population allele frequencies help assess variant rarity. Generally:

- Frequencies above 1% (0.01) suggest a common polymorphism.
- Frequencies below 0.01% (0.0001) are consistent with rare disease-causing variants.
- Absence from gnomAD does not confirm pathogenicity but supports rarity.

### In Silico Predictions (CADD, SIFT, PolyPhen)

These scores provide computational predictions of variant impact:

- **CADD >= 20** suggests the variant is in the top 1% most deleterious substitutions.
- **SIFT < 0.05** predicts a deleterious effect on protein function.
- **PolyPhen >= 0.85** predicts the variant is "Probably Damaging."

!!! warning "In silico predictions are supportive evidence only"
    Computational predictions should not be used as the sole basis for clinical classification. Always consider them alongside clinical data, population frequencies, and functional studies per [ACMG/AMP guidelines](../classification/using-the-classifier.md).

---

## Batch vs. Real-Time Annotation

| Feature | Variant Annotation Tool (Chat) | Variant Effect Prediction (Upload) |
|---------|-------------------------------|------------------------|
| **Scope** | Individual variants, on demand | Entire VCF file |
| **Speed** | Seconds per variant | Minutes to hours for large files |
| **Databases** | ClinVar, gnomAD, CADD, SIFT, PolyPhen | Ensembl VEP (consequence, gene, transcript, plus plugins) |
| **Availability** | All subscription tiers | Plus, Pro, and Trial tiers |
| **Use case** | Focused investigation of specific variants | Comprehensive annotation of all variants in a sample |

For batch annotation, see [Variant Effect Prediction](../samples/vep-annotation.md).

---

## Combining with Other Tools

The Variant Annotation tool is frequently used alongside:

- **Genomic Data Query** -- Query your data to identify variants of interest, then annotate them individually.
- **Biomedical Literature** -- After retrieving ClinVar data, search for supporting literature.
- **Knowledge Graph** -- Explore the gene-protein-drug network for the gene harboring the variant.
- **Clinical Trials** -- Find trials relevant to the variant's associated condition.

See [Example Workflows](example-workflows.md) for multi-tool analysis patterns.
