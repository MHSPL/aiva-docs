---
title: Secondary Analysis
description: Upload FASTQ files to AIVA for GPU-accelerated variant calling, BAM generation, and pharmacogenomic analysis using NVIDIA Parabricks.
---

# Secondary Analysis

Secondary analysis takes raw sequencing reads (FASTQ files) and runs a GPU-accelerated small variant calling pipeline powered by NVIDIA Parabricks. The pipeline calls SNVs and indels, which are automatically loaded into AIVA for analysis, along with BAM files for visual review in IGV.

!!! info "Subscription required"
    Secondary analysis is available on <span class="tier-badge tier-pro">Pro</span> and <span class="tier-badge tier-enterprise">Enterprise</span> tiers. Base pipeline cost is 3 credits (WES) or 4 credits (WGS). Enabling SNV/Indel calling adds 2 (WES) or 3 (WGS) credits. Each optional add-on (PGx, CNV, SV) adds 1 credit. Pipeline outputs (tables and BAMs) count toward your tier's [storage slots](../getting-started/subscription-tiers.md#storage-slots).

---

## What the pipeline produces

| Output | Description |
|--------|-------------|
| **Small variants (VCF)** | SNVs and indels, automatically loaded into AIVA for analysis |
| **BAM** | Aligned reads for visual review via IGV links |
| **PGx star alleles** | Pharmacogenomic star-allele assignments for key pharmacogenes |

!!! note "VCF download not available"
    Called variants are loaded directly into AIVA for analysis. VCF file download is not currently supported.

!!! note "Storage slot usage"
    Each pipeline output counts as a storage slot. A **germline** pipeline uses **2 slots** (1 table + 1 BAM). A **somatic tumor-only** pipeline uses **2 slots** (1 table + 1 BAM). A **somatic paired** pipeline uses **3 slots** (1 table + 2 BAMs). Check your available slots on the [Subscription Tiers](../getting-started/subscription-tiers.md#storage-slots) page.

---

## Pipeline workflow

```mermaid
graph LR
    A[FASTQ Files] --> B[Parabricks Secondary Analysis]
    B --> C[BAM]
    C --> D[VCF]
    C --> E[PGx Analysis]
    D --> F[Annotation]
    F --> G[Parse & Load]
    G --> H[Ready for Analysis]
    E --> I[Star Alleles & Recommendations]
    I --> H
```

1. **Download**: FASTQ files are downloaded from the provided cloud URLs.
2. **Parabricks secondary analysis**: Reads are aligned to the reference genome and small variants (SNVs and indels) are called using GPU-accelerated tools (DeepVariant for germline, DeepSomatic for tumor workflows). Aligned reads are saved as BAM files with IGV links for visual review.
3. **Annotation + PGx analysis** (parallel): Once Parabricks completes, two processes run in parallel:
    - **Annotation**: Small Variant Annotation enriches the output VCF, which is then parsed and loaded into the AIVA database.
    - **PGx analysis**: BAM files are used to assign pharmacogenomic star alleles, predict metabolizer phenotypes, and generate CPIC drug recommendations for 88 pharmacogenes. See [Pharmacogenomics](../analysis/pharmacogenomics.md).

You can monitor each stage in real time using the [Job Manager](job-monitoring.md).

---

## Starting a pipeline run

Navigate to the **Samples** tab, click **Upload**, and select the **Secondary Analysis** tab.

![The secondary analysis upload dialog showing pipeline configuration, sequencer selection, and FASTQ URL fields](../assets/images/screenshots/samples/fastq-upload.png)

### Step 1: Name your sample

Enter a **Sample Name**. This is the name that will appear in your sample list and is used for `@sample:` mentions in AIVA Chat.

### Step 2: Configure the pipeline

| Setting | Options | Description |
|---------|---------|-------------|
| **Analysis Type** | Germline, Somatic Paired, Somatic Tumor-Only | Germline for inherited variant analysis. Somatic for cancer workflows (paired tumor-normal or tumor-only). |
| **Sequencer** | Illumina, PacBio, ONT, Ultima, MGI, Element | Both short-read and long-read sequencing platforms are supported. |
| **Data Type** | WGS (Whole Genome), WES (Whole Exome) | Determines pipeline parameters. WES runs may require an interval file. |
| **Reference** | GRCh38 (hg38) | The reference genome build for alignment. |

Optionally assign the sample to a **Project** for team collaboration.

### Step 3: Provide FASTQ files

Enter the cloud storage URLs for your Read 1 (R1) and Read 2 (R2) FASTQ files. Supported URL schemes:

| Scheme | Provider |
|--------|----------|
| `gs://` | Google Cloud Storage |
| `s3://` | Amazon S3 |
| `az://` | Azure Blob Storage |
| `https://` | Any publicly accessible URL |

For paired-end sequencing, both R1 and R2 URLs are required. Click **+ Add Lane** if your sample was sequenced across multiple flow cell lanes.

!!! warning "Files must be publicly accessible"
    AIVA downloads the FASTQ files from the URLs you provide. The files must be publicly readable so that AIVA's server can access them. Private or authenticated URLs will fail with a download error in the Job Manager.

### Step 4: Optional Interval File

- **Interval File**: Upload a BED file to restrict analysis to targeted regions (recommended for WES data).

### Step 5: Start the pipeline

Click **Start Pipeline** to submit. The pipeline run is queued and processed in the background.

---

## Somatic analysis

### Somatic paired (tumor-normal)

Select **Somatic Paired** as the analysis type for matched tumor-normal samples. You will need to provide FASTQ files for both the tumor and normal samples, each labeled with the appropriate role.

![The somatic paired upload dialog showing tumor and normal sample FASTQ URL fields](../assets/images/screenshots/samples/tumor-normal.png)

### Somatic tumor-only

Select **Somatic Tumor-Only** when a matched normal sample is not available. Only tumor FASTQ files are required.

---

## Supported FASTQ formats

- Standard FASTQ format (`.fastq`, `.fastq.gz`, `.fq.gz`)
- Gzip-compressed files are recommended to reduce download time
- Both single-end and paired-end reads are supported

---

## Troubleshooting

??? question "My pipeline run failed. What should I do?"
    Open the [Job Manager](job-monitoring.md) and check the error message on the failed job. Common causes include:

    - **Inaccessible FASTQ URLs**: Verify the URLs are valid and the files are accessible from the AIVA server.
    - **Corrupted FASTQ files**: Ensure the files are valid FASTQ format and not truncated.
    - **Mismatched R1/R2 files**: For paired-end data, the R1 and R2 files must contain the same number of reads in the same order.

??? question "How long does a pipeline run take?"
    Processing time depends on file size and data type. A typical 30x whole-genome sample takes approximately 2 hours with GPU acceleration. Whole-exome samples are faster due to the smaller target region.

??? question "Can I run multiple pipeline jobs at once?"
    Jobs are queued and processed based on available GPU resources. You can submit multiple jobs, and they will be processed in order.

---

## Next steps

- [:octicons-arrow-right-24: Monitor your pipeline job](job-monitoring.md)
- [:octicons-arrow-right-24: Explore the table view](../analysis/index.md)
- [:octicons-arrow-right-24: Explore your data in AIVA Chat](../aiva-chat/index.md)
- [:octicons-arrow-right-24: Upload a VCF file directly](vcf-upload.md)
