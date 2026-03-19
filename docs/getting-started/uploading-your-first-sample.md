---
title: Uploading Your First Sample
description: Step-by-step guide to uploading a VCF, CSV, or TSV file into AIVA and viewing the results in the data table.
---

# Uploading Your First Sample

This walkthrough takes you from file selection to viewing your data in the interactive table. The entire process typically takes a few seconds for small files and a few minutes for larger datasets or files that require annotation.

---

## Prerequisites

- A [verified AIVA account](account-setup.md).
- A genomic data file in one of the supported formats: **VCF**, **CSV**, or **TSV**.
- An active internet connection.

!!! info "File size limits"
    Upload limits depend on your [subscription tier](subscription-tiers.md). Free accounts have restricted upload counts and file sizes. Plus and Pro tiers support larger files and more uploads.

---

## Step 1: Navigate to Samples

Click the **Samples** tab in the header navigation bar. This opens the Samples page where you can manage projects and upload files.

---

## Step 2: Start a New Upload

Click the **Upload** button or use the drag-and-drop zone on the page. You can also create a new project first and upload into it, or upload directly to your personal sample library.

---

## Step 3: Choose Your File

You have two options:

=== "Drag and Drop"

    Drag your file from your file manager and drop it onto the upload zone. The zone highlights when a valid file is detected.

=== "Browse"

    Click the upload zone or the **Browse** button to open your system file picker. Navigate to your file and select it.

Supported file types:

| Format | Extensions | Notes |
|--------|-----------|-------|
| VCF | `.vcf`, `.vcf.gz` | Variant Call Format. Supports both uncompressed and gzip-compressed files. |
| CSV | `.csv` | Comma-separated values. First row must contain column headers. |
| TSV | `.tsv`, `.txt` | Tab-separated values. First row must contain column headers. |

---

## Step 4: Configure Upload Options

After selecting your file, a configuration panel appears. Depending on the file type and your subscription tier, you may see the following options:

### VCF-Specific Options

- **Small Variant Annotation** -- Check this box to run small variant annotation on your VCF file during processing. This adds consequence predictions, gene symbols, transcript information, and more. This option is available on <span class="tier-badge tier-plus">Plus</span> and <span class="tier-badge tier-pro">Pro</span> tiers.

- **Structural Variant Annotation** -- Check this box to run structural variant annotation on your VCF file. Also restricted to <span class="tier-badge tier-plus">Plus</span> and <span class="tier-badge tier-pro">Pro</span> tiers.

!!! tip "Not sure about annotation?"
    You can always upload without annotation first and examine your raw data. Annotation can add significant processing time depending on file size, but it enriches your dataset with clinically relevant information that the AI assistant can then use for analysis.

### General Options

- **Sample Name** -- Optionally provide a human-readable name for the sample. If left blank, the filename is used.
- **Project** -- Optionally assign the upload to an existing project for organization and collaboration.

---

## Step 5: Submit the Upload

Click the **Upload** or **Submit** button to start the process. AIVA handles the rest in the background:

1. The file is uploaded to the server.
2. If Small Variant Annotation or Structural Variant Annotation was selected, the annotation job runs first.
3. The file is parsed and loaded into the database using optimized bulk operations.

---

## Step 6: Monitor Job Progress

After submission, the upload enters the job processing pipeline. You can monitor progress in two ways:

### Job Manager

Click the **Job Manager** icon in the header to open the jobs panel. Here you will see:

- **Job status** -- Queued, Processing, Completed, or Failed.
- **Progress details** -- The current stage of processing (downloading, annotating, parsing).
- **Estimated time** -- For longer jobs, a rough estimate of remaining time.

### Real-Time Updates

AIVA uses server-sent events (SSE) to push job status updates to your browser in real time. You do not need to refresh the page -- the status updates automatically.

!!! warning "Do not close your browser tab"
    While the job runs on the server and will complete even if you navigate away, keeping the tab open ensures you receive real-time status updates and are notified immediately when the job finishes.

---

## Step 7: View Your Data

Once the job completes successfully:

1. Navigate to the **Samples** tab if you are not already there.
2. Find your sample in the list. Newly completed samples appear at the top.
3. Click on the sample to open it in the interactive data table.

The data table provides:

- **Virtualized scrolling** -- Smoothly browse datasets with millions of rows without performance degradation.
- **Column sorting and filtering** -- Click column headers to sort, or use the filter controls to narrow down to variants of interest.
- **Server-side pagination** -- Data is fetched in pages from the server, keeping the interface responsive regardless of dataset size.

From the data table, you can:

- **Flag variants** for follow-up review.
- **Add comments** to individual rows with threaded discussions.
- **Classify variants** using the ACMG framework.
- **Open in Chat** to ask AIVA questions about the data.
- **Launch Analysis** to enter the tertiary analysis workspace.

For full details on the data table, see [Data Table](../data-table/index.md).

---

## Troubleshooting

??? question "My upload failed. What should I do?"
    Open the Job Manager and check the error message on the failed job. Common causes include:

    - **Unsupported file format** -- Ensure the file extension matches one of the supported types and the content is valid.
    - **File too large** -- Your subscription tier may have a file size limit. See [Subscription Tiers](subscription-tiers.md).
    - **Upload limit reached** -- Free accounts have a limited number of uploads. Upgrade your tier to continue.
    - **Malformed VCF** -- The file must include a valid VCF header. Check that the `#CHROM` header line is present.

??? question "My Small Variant Annotation is taking a long time."
    Small Variant Annotation involves running each variant through the annotation pipeline. For whole-genome VCF files with millions of variants, this can take several minutes. The job will complete in the background -- you can continue using other features while it processes.

??? question "I uploaded a CSV but the columns look wrong."
    Ensure your CSV file uses commas as delimiters and that the first row contains column headers. If your file uses a different delimiter, rename it with the appropriate extension (`.tsv` for tab-separated).

---

## Next Steps

Now that you have data in AIVA, explore what you can do with it:

- [:octicons-arrow-right-24: Ask AIVA about your data](../aiva-chat/index.md)
- [:octicons-arrow-right-24: Explore the data table](../data-table/index.md)
- [:octicons-arrow-right-24: Set up a project for collaboration](../collaboration/projects.md)
- [:octicons-arrow-right-24: Review subscription tiers](subscription-tiers.md)
