---
title: Uploading Your First Sample
description: Step-by-step guide to uploading a VCF, CSV, or TSV file into AIVA and viewing the results in the data table.
---

# Uploading Your First Sample

This walkthrough takes you from file selection to viewing your data in the interactive table. The entire process typically takes a few seconds for small files and a few minutes for larger datasets or files that require annotation.

## Prerequisites

- A [verified AIVA account](account-setup.md).
- A sample file in one of the supported formats: **VCF**, **CSV**, or **TSV**.
- An active internet connection, lol.

!!! info "File size limits"
    Upload limits depend on your [subscription tier](subscription-tiers.md).

## Step 1: Navigate to Samples

Click the **Samples** tab in the header navigation bar. This opens the Samples page where you can manage projects and upload files.

## Step 2: Start a New Upload

Click the **Upload** button in the top right corner of the page. The upload dialog has two tabs:

=== "Local Upload"

    Drag your file onto the upload zone, or click to browse your file system. Supported file types:

    | Format | Extensions | Notes |
    |--------|-----------|-------|
    | VCF | `.vcf`, `.vcf.gz` | Variant Call Format. Supports both uncompressed and gzip-compressed files. |
    | CSV | `.csv` | Comma-separated values. First row must contain column headers. |
    | TSV | `.tsv`, `.txt` | Tab-separated values. First row must contain column headers. |

=== "Cloud Import"

    Paste a file URL from a cloud storage bucket to import directly. Supported providers:

    - Google Cloud Storage (`gs://`)
    - Amazon S3 (`s3://`)
    - Azure Blob Storage (`az://`)
    - Public HTTPS URLs

## Step 3: Configure Upload Options

After selecting your file, configuration options appear below:

### Split by sample

For multi-sample VCF files, check **Split by sample** to create separate tables for each sample. Each split sample consumes one credit from your weekly allowance (max 100 samples per file). Leave unchecked to analyze all samples together in a single table.

### Variant Annotation (VCF files)

Choose one of three annotation options:

- **Skip**: Select this if your VCF is already annotated from your own pipeline. AIVA will recognize and display your existing annotations.
- **Small Variants (SNVs/Indels)**: Runs small variant annotation to add consequence predictions, gene symbols, and transcript-level information.
- **Structural Variants (CNVs/SVs)**: Runs structural variant annotation with clinical and functional context.

!!! warning "hg38 only"
    Variant annotation is currently supported only for VCF files aligned to the **hg38** (GRCh38) reference genome build.

## Step 4: Submit the Upload

Click the **Upload** or **Submit** button to start the process. AIVA handles the rest in the background:

1. The file is uploaded to the server.
2. If Small Variant Annotation or Structural Variant Annotation was selected, the annotation job runs first.
3. The file is parsed and loaded into the database.

## Step 5: Monitor Job Progress

After submission, the upload enters the job processing pipeline. You can monitor progress by clicking the **Job Manager** icon in the header to open the jobs panel. Here you will see:

- **Job status**: Queued, Processing, Completed, or Failed.
- **Progress details**: The current stage of processing (downloading, annotating, parsing).

## Step 6: Start exploring your data

Once the job completes, head to the **Chat** tab to start exploring your data. Type `@sample:` followed by your sample name to attach it to the conversation, then ask AIVA questions. For example:

- "Summarize the variants in this sample"
- "Show me all pathogenic variants in BRCA1"
- "What are the most clinically significant findings?"

AIVA can query your data, run analyses, generate visualizations, and help you interpret results, all through conversation. See [AIVA Chat](../aiva-chat/index.md) to learn more.

You can also browse your data directly in the [Data Table](../data-table/index.md) from the **Samples** tab.

## Troubleshooting

??? question "My upload failed. What should I do?"
    Open the Job Manager and check the error message on the failed job. Common causes include:

    - **Unsupported file format**: Ensure the file extension matches one of the supported types and the content is valid.
    - **File too large**: Your subscription tier may have a file size limit. See [Subscription Tiers](subscription-tiers.md).
    - **Upload limit reached**: Free accounts cannot upload. Upgrade to Trial or a paid tier to continue.
    - **Malformed VCF**: The file must include a valid VCF header. Check that the `#CHROM` header line is present.

??? question "My Small Variant Annotation is taking a long time."
    Small Variant Annotation involves running each variant through the annotation pipeline. For whole-genome VCF files with millions of variants, this can take several minutes. The job will complete in the background, and you can continue using other features while it processes.

??? question "I uploaded a CSV but the columns look wrong."
    Ensure your CSV file uses commas as delimiters and that the first row contains column headers. If your file uses a different delimiter, rename it with the appropriate extension (`.tsv` for tab-separated).

## Next Steps

Now that you have data in AIVA, explore what you can do with it:

- [:octicons-arrow-right-24: Ask AIVA about your data](../aiva-chat/index.md)
- [:octicons-arrow-right-24: Explore the data table](../data-table/index.md)
- [:octicons-arrow-right-24: Set up a project for collaboration](../collaboration/projects.md)
- [:octicons-arrow-right-24: Review subscription tiers](subscription-tiers.md)
