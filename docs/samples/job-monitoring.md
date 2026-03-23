---
title: Job Monitoring
description: Track upload, annotation, and parsing jobs in real time using the AIVA Job Manager.
---

# Job Monitoring

Every file upload in AIVA is processed as a background job. The **Jobs** panel gives you real-time visibility into the status of all your active and completed jobs, so you always know where things stand.

---

## Opening the Job Manager

Click the **Jobs** icon in the header navigation bar. The Job Manager panel opens and displays all jobs associated with your account, ordered by most recent first.

!!! tip "Jobs run in the background"
    You do not need to keep the Job Manager open for jobs to progress. Processing continues on the server regardless of what you are doing in the interface. The Job Manager is simply a window into the pipeline.

---

## Job States

Each job moves through a series of states as it progresses through the processing pipeline. The current state is displayed alongside each job entry.

| State | Description |
|-------|-------------|
| **Queued** | The job has been created and is waiting for an available processing slot. Jobs are claimed atomically when resources become available. |
| **Downloading** | The file is being retrieved from a cloud URL (GCS, S3, Azure, or HTTPS). This state applies only to cloud URL imports; local uploads skip this stage. |
| **Processing** | The file is being processed (either parabricks or PGx calling). |
| **Annotating** | Small Variant Annotation or Structural Variant Annotation is running against the file. This stage appears only when annotation was selected during upload. |
| **Parsing** | The file is being parsed and loaded into the database for analysis. |
| **Completed** | The job finished successfully. The sample is ready to view in the table view. |
| **Failed** | An error occurred during processing. See the error details on the job entry for diagnostic information. |

!!! note "Browser tab behavior"
    SSE connections are maintained as long as your browser tab is active. If you close the tab and return later, the Job Manager reconnects automatically and displays the current state of all jobs. No progress is lost.

---

## Handling Failed Jobs

When a job fails, the Job Manager displays the error message alongside the failed entry. Common failure scenarios and their resolutions:

??? question "Malformed VCF header"
    The VCF file is missing required header fields or the `#CHROM` line. Verify that your file was produced by a standard variant caller and contains the required columns. Fix the file and re-upload.

??? question "Annotation timeout"
    Very large files (millions of variants) may exceed annotation time limits. Try uploading the file without annotation, then use the AIVA Chat [Variant Annotation tool](../aiva-chat/ai-tools.md#variant-annotation) to annotate specific variants of interest on demand.

??? question "Parsing error"
    The file content does not match the expected format for its extension. For CSV/TSV files, ensure consistent column counts across all rows and that the header row is present. For VCF files, ensure the data lines match the header column definitions.

??? question "Download failed (cloud URLs)"
    The cloud URL may be inaccessible due to expired credentials, incorrect permissions, or network issues. Verify that the URL is valid, the resource exists, and your credentials (if required) are current. See [VCF Upload](vcf-upload.md#authentication-and-access) for authentication details.

!!! note "Retrying a Failed Job"
    AIVA offers automatic retry functionality for failed jobs. By default, failed jobs will be automatically retried up to 3 times.

---

## Best Practices

- **Check the Jobs panel after submitting uploads** to confirm your jobs have entered the queue.
- **Review error messages promptly** when jobs fail, so you can correct issues and re-upload without delay.
- **Use descriptive sample names** during upload to make it easier to identify jobs in the panel, especially when processing multiple files.

---

## Next Steps

- [:octicons-arrow-right-24: Upload a VCF file](vcf-upload.md)
- [:octicons-arrow-right-24: Run secondary analysis](secondary-analysis.md)
- [:octicons-arrow-right-24: View your data in the table](../analysis/index.md)
- [:octicons-arrow-right-24: Ask AIVA about your data](../aiva-chat/index.md)
