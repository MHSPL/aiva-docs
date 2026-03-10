---
title: Samples
description: Upload, annotate, monitor, and manage genomic data samples in AIVA.
---

# Samples

The Samples section is where you bring your genomic data into AIVA. Whether you are working with a single VCF file from a clinical sequencing run or batch-importing CSV exports from a research pipeline, every analysis starts here.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Uploading Files

Upload VCF, CSV, and TSV files using drag-and-drop or the file browser. Configure annotation options and submit for processing.

[:octicons-arrow-right-24: Uploading Files](uploading-files.md)

</div>

<div class="card" markdown>

### Cloud URL Imports

Ingest files directly from Google Cloud Storage, Amazon S3, Azure Blob Storage, or public HTTPS URLs without downloading them first.

[:octicons-arrow-right-24: Cloud URLs](cloud-urls.md)

</div>

<div class="card" markdown>

### Variant Effect Prediction

Enrich VCF files with variant effect predictions during upload for consequence predictions, gene symbols, and transcript-level detail.

[:octicons-arrow-right-24: Variant Effect Prediction](vep-annotation.md)

</div>

<div class="card" markdown>

### Structural Variant Annotation

Annotate structural variants during upload to add clinical and functional annotations for CNVs, inversions, and translocations.

[:octicons-arrow-right-24: Structural Variant Annotation](annotsv-annotation.md)

</div>

<div class="card" markdown>

### Job Monitoring

Track the progress of upload, annotation, and parsing jobs in real time using the Job Manager panel.

[:octicons-arrow-right-24: Job Monitoring](job-monitoring.md)

</div>

<div class="card" markdown>

### Managing Samples

View, rename, delete, and organize your samples. Assign samples to projects for collaboration.

[:octicons-arrow-right-24: Managing Samples](managing-samples.md)

</div>

</div>

---

## How It Works

The sample lifecycle in AIVA follows a straightforward pipeline:

1. **Upload** -- Submit a local file or provide a cloud URL.
2. **Annotate** (optional) -- Variant Effect Prediction or Structural Variant Annotation runs in the background if selected.
3. **Parse** -- The file is parsed and loaded into the database using high-speed bulk operations.
4. **Explore** -- Your data appears in the interactive data table, ready for analysis.

Each step is handled as a background job, so you can continue working while processing completes. Real-time status updates are pushed to your browser automatically.

!!! tip "First time uploading?"
    If you are new to AIVA, start with the [Uploading Your First Sample](../getting-started/uploading-your-first-sample.md) walkthrough in the Getting Started section for a guided end-to-end experience.
