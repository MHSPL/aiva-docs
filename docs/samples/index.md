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

### VCF Upload

Upload VCF, CSV, and TSV files from your local machine or cloud storage. Configure annotation options and submit for processing.

[:octicons-arrow-right-24: VCF Upload](vcf-upload.md)

</div>

<div class="card" markdown>

### Secondary Analysis

Upload FASTQ files for GPU-accelerated variant calling, BAM generation, and pharmacogenomic analysis via the Parabricks pipeline.

[:octicons-arrow-right-24: Secondary Analysis](secondary-analysis.md)

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

1. **Upload**: Submit a local file or provide a cloud URL.
2. **Annotate** (optional): Small Variant Annotation or Structural Variant Annotation runs in the background if selected.
3. **Parse**: The file is parsed and loaded into the database for analysis.
4. **Explore**: Explore your sample in the interactive table view or via chat using natural language.
5. **Delete**: Remove samples you no longer need to free up quota limits for new samples. Once deleted, the sample cannot be recovered.

Each step is handled as a background job, so you can continue working while processing completes. Real-time status updates are pushed to your browser automatically.

!!! tip "First time uploading?"
    If you are new to AIVA, start with the [Uploading Your First Sample](../getting-started/uploading-your-first-sample.md) walkthrough in the Getting Started section for a guided end-to-end experience.
