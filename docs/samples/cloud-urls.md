---
title: Cloud URL Imports
description: Import genomic data files directly from Google Cloud Storage, Amazon S3, Azure Blob Storage, or public HTTPS URLs.
---

# Cloud URL Imports

AIVA can import files directly from cloud storage services and public URLs. Instead of downloading a file to your local machine and re-uploading it, you paste the URL and AIVA handles the download and processing server-side.

---

## Supported URL Schemes

| Scheme | Service | Example |
|--------|---------|---------|
| `gs://` | Google Cloud Storage | `gs://my-bucket/samples/patient-001.vcf.gz` |
| `s3://` | Amazon S3 | `s3://lab-data/exome/sample-42.vcf` |
| `az://` | Azure Blob Storage | `az://container/path/to/variants.vcf` |
| `https://` | Public HTTPS URL | `https://example.com/data/variants.csv` |

---

## How to Import from a Cloud URL

1. Navigate to the **Samples** section.
2. Click **Upload** or open the upload dialog.
3. Select the **Cloud URL** import option.
4. Paste the full URL of the file you want to import.
5. (Optional) Enable [Small Variant Annotation](small-variant-annotation.md) or [Structural Variant Annotation](structural-variant-annotation.md) if the file is a VCF and you want annotation applied.
6. Click **Submit**.

AIVA creates a background job that:

1. **Downloads** the file from the provided URL to the server.
2. **Annotates** the file (if Small Variant Annotation or Structural Variant Annotation was selected).
3. **Parses** the file and loads it into the database.

You can monitor progress in the [Job Manager](job-monitoring.md).

---

## Authentication and Access

!!! warning "Ensure the file is accessible"
    AIVA's server must be able to reach and download the file at the provided URL. For cloud storage URLs, the file must either be publicly accessible or the AIVA server must have appropriate credentials configured.

- **Google Cloud Storage (`gs://`)**: The server uses its configured GCS service account credentials. The file must be readable by that service account.
- **Amazon S3 (`s3://`)**: The server uses configured AWS credentials. The file must be accessible with those credentials.
- **Azure Blob Storage (`az://`)**: The server uses configured Azure credentials.
- **HTTPS URLs**: The URL must be publicly accessible (no authentication required) or return the file without interactive login.

If the download fails due to access permissions, the job will report an error in the Job Manager with details about the failure.

---

## Supported File Formats

Cloud URL imports support the same file formats as local uploads:

- **VCF** (`.vcf`, `.vcf.gz`): Variant Call Format files, optionally gzipped.
- **CSV** (`.csv`): Comma-separated values.
- **TSV** (`.tsv`, `.txt`): Tab-separated values.

---

## Job Pipeline

Cloud URL imports follow a multi-step job pipeline:

```
Download --> Annotate (optional) --> Parse --> Ready
```

1. **Download**: The file is downloaded from the cloud URL to temporary server storage. Progress is reported as the download proceeds.
2. **Annotate**: If Small Variant Annotation or Structural Variant Annotation was requested, annotation runs against the downloaded file. This step is skipped for non-VCF files or if no annotation was selected.
3. **Parse**: The file (original or annotated) is parsed and loaded into the database using bulk operations.
4. **Ready**: The sample appears in your sample list and is available for exploration in the [Data Table](../data-table/index.md).

!!! info "Download times vary"
    Download time depends on the file size and the speed of the cloud storage service. Large files (multiple gigabytes) may take several minutes to download. You can continue working in AIVA while the download runs in the background.

---

## Tips

- **Use compressed files when possible**: Uploading `.vcf.gz` files reduces download time and storage compared to uncompressed `.vcf` files.
- **Verify URLs before submitting**: Paste the URL in a browser or use `curl` to confirm the file is accessible before submitting to AIVA.
- **Check job status**: If a cloud import seems stuck, check the [Job Manager](job-monitoring.md) for error messages. Common issues include expired URLs, permission errors, and network timeouts.
