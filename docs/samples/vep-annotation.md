---
title: Variant Effect Prediction
description: Enrich VCF files with variant effect predictions (VEP) during upload for consequence predictions, gene symbols, and transcript-level information.
---

# Variant Effect Prediction

AIVA integrates Ensembl's Variant Effect Predictor (VEP) to annotate VCF files during upload. Variant Effect Prediction adds consequence predictions, gene symbols, transcript information, and links to external databases for every variant in your file.

---

## What Variant Effect Prediction Adds

When Variant Effect Prediction is applied, the following information is added to each variant and made available as individual columns in the [Data Table](../data-table/index.md):

| Annotation | Description |
|------------|-------------|
| **Consequence** | The predicted effect of the variant on the transcript (e.g., missense_variant, frameshift_variant, synonymous_variant). |
| **Gene Symbol** | The HGNC gene symbol associated with the variant. |
| **IMPACT** | Severity classification: HIGH, MODERATE, LOW, or MODIFIER. |
| **Transcript** | The Ensembl transcript ID affected by the variant. |
| **Protein Position** | The amino acid position affected in the protein product. |
| **Amino Acid Change** | The reference and alternate amino acids (e.g., R/H). |
| **SIFT** | Prediction of whether the amino acid change affects protein function (Tolerated / Deleterious) with a confidence score. |
| **PolyPhen** | Prediction of the structural and functional impact of the amino acid change (Benign / Possibly Damaging / Probably Damaging) with a score. |
| **Existing Variation** | Known variant identifiers (e.g., rsIDs from dbSNP). |

These fields are parsed from the VEP CSQ (consequence) string and broken out into individual, sortable, filterable columns.

---

## Subscription Requirements

Variant Effect Prediction is available on the following subscription tiers:

| Tier | Available |
|------|-----------|
| Free | No |
| Trial | Yes |
| Plus | Yes |
| Pro | Yes |

See [Subscription Tiers](../getting-started/subscription-tiers.md) for a full comparison of plan features.

---

## How to Enable Variant Effect Prediction

1. Navigate to the **Samples** section and open the upload dialog.
2. Select or drag-and-drop a **VCF file** (`.vcf` or `.vcf.gz`).
3. Check the **Enable Variant Effect Prediction** checkbox.
4. Click **Upload** to submit the file.

The system creates a multi-step background job:

1. **Upload/Download** -- The file is uploaded (or downloaded from a [cloud URL](cloud-urls.md)).
2. **Variant Effect Prediction** -- The VEP engine runs against the VCF file, adding CSQ annotations.
3. **Parsing** -- The annotated file is parsed, and CSQ subfields are extracted into individual columns.
4. **Ready** -- The sample appears in your sample list with all annotation columns available.

Monitor progress in the [Job Manager](job-monitoring.md).

!!! note "VCF files only"
    Variant Effect Prediction is available only for VCF files. CSV and TSV files cannot be annotated, as VEP requires the VCF format to interpret variant calls correctly.

---

## Assembly Support

AIVA supports two reference genome assemblies for Variant Effect Prediction:

- **GRCh38** (hg38) -- The current human reference genome assembly. This is the default.
- **GRCh37** (hg19) -- The previous assembly, still widely used in clinical settings.

The assembly is configured at the server level. Ensure your VCF files are aligned to the same reference assembly configured on your AIVA instance.

---

## Processing Time

Variant Effect Prediction processing time depends on the number of variants in your file:

| File Size | Approximate Time |
|-----------|-----------------|
| < 10,000 variants | Under 1 minute |
| 10,000 -- 100,000 variants | 1 to 5 minutes |
| 100,000 -- 1,000,000 variants | 5 to 30 minutes |
| > 1,000,000 variants | 30 minutes or more |

!!! tip "Continue working while prediction runs"
    Variant Effect Prediction runs as a background job. You can navigate away, upload additional files, chat with AIVA, or work on other samples while the annotation completes. You will receive a notification when the job finishes.

---

## Using Annotation Columns in Analysis

Once annotation is complete and the sample is ready:

- **Data Table**: Annotation columns appear in the column chooser. Add them to your table view to see consequence predictions, gene symbols, SIFT/PolyPhen scores, and more alongside your variant data. See [Navigation and Layout](../data-table/navigation-and-layout.md).
- **Filtering**: Filter on annotation columns like any other column. For example, filter by `Consequence` = `missense_variant` or `IMPACT` = `HIGH`. See [Filtering](../data-table/filtering.md).
- **AI Analysis**: Ask AIVA questions that reference annotations. For example, "Show me all HIGH impact variants with deleterious SIFT predictions." AIVA queries these columns directly.
- **Export**: Annotation columns are included in [CSV exports](../data-table/exporting-data.md) when they are visible in the table.

---

## Server-Side Requirements

!!! info "Administrator note"
    Variant Effect Prediction requires a local VEP cache on the server. The cache is approximately 18 GB in size and must be downloaded separately. See the VEP setup documentation for installation instructions. The feature will not function if the cache is not present.
