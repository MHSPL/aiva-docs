---
title: Structural Variant Annotation
description: Annotate structural variants during upload for clinical interpretation of CNVs, inversions, translocations, and other structural variants.
---

# Structural Variant Annotation

AIVA integrates a structural variant annotation engine to annotate structural variants (SVs) during upload. This feature adds clinical and functional annotations that assist in the interpretation of copy number variants (CNVs), inversions, translocations, insertions, and other structural rearrangements.

---

## What Structural Variant Annotation Adds

Structural Variant Annotation provides annotations across multiple categories:

| Category | Examples |
|----------|---------|
| **Gene annotations** | Overlapping genes, gene count, haploinsufficiency and triplosensitivity scores |
| **Known SV databases** | Overlap with known pathogenic/benign SVs from ClinVar, ClinGen, DGV, and gnomAD-SV |
| **Regulatory elements** | Overlap with enhancers, promoters, and other regulatory regions |
| **Functional impact** | Predicted effect on coding sequences, exon overlap, breakpoint locations |
| **ACMG classification** | Automated preliminary SV classification based on ACMG/ClinGen technical standards |
| **Population frequency** | SV frequency in population databases to distinguish rare from common variants |

---

## How to Enable Structural Variant Annotation

1. Navigate to the **Samples** section and open the upload dialog.
2. Select or drag-and-drop a **VCF file** containing structural variant calls.
3. Check the **Enable Structural Variant Annotation** checkbox.
4. Click **Upload** to submit the file.

The system creates a background job pipeline:

1. **Upload/Download** -- The file is uploaded or downloaded from a [cloud URL](cloud-urls.md).
2. **Structural Variant Annotation** -- The structural variant annotation engine processes the file, annotating each structural variant.
3. **Parsing** -- The annotated output is parsed and loaded into the database.
4. **Ready** -- The sample appears in your sample list with annotation columns available.

Monitor job progress in the [Job Manager](job-monitoring.md).

---

## Subscription Requirements

Structural Variant Annotation availability follows the same tier structure as Small Variant Annotation:

| Tier | Available |
|------|-----------|
| Free | No |
| Trial | Yes |
| Plus | Yes |
| Pro | Yes |

---

## Using Annotation Columns

After annotation completes, the generated columns are available in the [Data Table](../data-table/index.md):

- Use the [column chooser](../data-table/navigation-and-layout.md#column-chooser) to add annotation columns to your view.
- [Filter](../data-table/filtering.md) on annotation fields to isolate SVs of interest -- for example, filter by ACMG class or by overlap with known pathogenic SVs.
- Ask [AIVA](../aiva-chat/index.md) to query these annotations. For example: "Which structural variants overlap known pathogenic CNVs in ClinGen?"

---

## Structural Variant Annotation vs. Small Variant Annotation

| Feature | Small Variant Annotation | Structural Variant Annotation |
|---------|--------------------------------|----------------------------------------|
| **Target** | SNVs and small indels | Structural variants (CNVs, inversions, translocations) |
| **Annotations** | Consequence, gene, transcript, SIFT, PolyPhen | Gene overlap, population SV frequency, regulatory impact, ACMG SV class |
| **Input** | VCF with SNV/indel calls | VCF with SV calls |

You can enable Small Variant Annotation and Structural Variant Annotation independently depending on the variant types in your file. For files containing both SNVs and SVs, you may use both annotation pipelines.

!!! tip "Choose the right annotation"
    If your VCF contains only short variants (SNVs and small insertions/deletions), use [Small Variant Annotation](small-variant-annotation.md). If it contains structural variants, use Structural Variant Annotation. Check your VCF's SVTYPE or ALT field to determine which variant types are present.
