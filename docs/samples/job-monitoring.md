---
title: Job Monitoring
description: Track upload, annotation, and parsing jobs in real time using the AIVA Job Manager.
---

# Job Monitoring

Every file upload in AIVA is processed as a background job. The **Job Manager** gives you real-time visibility into the status of all your active and completed jobs, so you always know where things stand.

---

## Opening the Job Manager

Click the **Job Manager** icon in the header navigation bar. The Job Manager panel opens and displays all jobs associated with your account, ordered by most recent first.

!!! tip "Jobs run in the background"
    You do not need to keep the Job Manager open for jobs to progress. Processing continues on the server regardless of what you are doing in the interface. The Job Manager is simply a window into the pipeline.

---

## Job States

Each job moves through a series of states as it progresses through the processing pipeline. The current state is displayed alongside each job entry.

| State | Description |
|-------|-------------|
| **Queued** | The job has been created and is waiting for an available processing slot. Jobs are claimed atomically using database-level locking to prevent conflicts. |
| **Downloading** | The file is being retrieved from a cloud URL (GCS, S3, Azure, or HTTPS). This state applies only to [cloud URL imports](cloud-urls.md); local uploads skip this stage. |
| **Annotating** | Small Variant Annotation or Structural Variant Annotation is running against the file. This stage appears only when annotation was selected during upload. |
| **Parsing** | The file is being parsed and loaded into the database using high-speed bulk insertion. |
| **Completed** | The job finished successfully. The sample is ready to view in the data table. |
| **Failed** | An error occurred during processing. See the error details on the job entry for diagnostic information. |

### Processing Priority

Jobs are processed in priority order to minimize wait times:

1. **Parsing jobs** (highest priority): These are the fastest to complete and unlock data for analysis.
2. **Download jobs**: Cloud URL retrieval runs at the next priority level.
3. **Annotation jobs** (lowest priority): Small Variant Annotation and Structural Variant Annotation are computationally intensive and run at the lowest priority to avoid blocking simpler jobs.

---

## Real-Time Updates

AIVA uses **server-sent events (SSE)** to push job status changes to your browser as they happen. This means:

- You do **not** need to refresh the page to see updates.
- State transitions (e.g., from "Annotating" to "Parsing") appear automatically.
- Completion and failure notifications are delivered instantly.

!!! note "Browser tab behavior"
    SSE connections are maintained as long as your browser tab is active. If you close the tab and return later, the Job Manager reconnects automatically and displays the current state of all jobs. No progress is lost.

---

## Understanding Job Details

Click on any job entry in the Job Manager to expand its details. The detail view includes:

- **File name**: The original name of the uploaded file.
- **Sample name**: The human-readable name you assigned (or the filename if none was provided).
- **Created at**: Timestamp when the job was submitted.
- **Current state**: The active processing stage.
- **Processing stages**: A timeline showing which stages have completed and which remain.
- **Error message** (failed jobs only): A description of what went wrong.

---

## Handling Failed Jobs

When a job fails, the Job Manager displays the error message alongside the failed entry. Common failure scenarios and their resolutions:

??? question "Malformed VCF header"
    The VCF file is missing required header fields or the `#CHROM` line. Verify that your file was produced by a standard variant caller and contains the required columns. Fix the file and re-upload.

??? question "Annotation timeout"
    Very large files (millions of variants) may exceed annotation time limits. Try uploading the file without annotation, then use the AIVA Chat [Variant Annotation tool](../aiva-chat/variant-annotation-tool.md) to annotate specific variants of interest on demand.

??? question "Parsing error"
    The file content does not match the expected format for its extension. For CSV/TSV files, ensure consistent column counts across all rows and that the header row is present. For VCF files, ensure the data lines match the header column definitions.

??? question "Download failed (cloud URLs)"
    The cloud URL may be inaccessible due to expired credentials, incorrect permissions, or network issues. Verify that the URL is valid, the resource exists, and your credentials (if required) are current. See [Cloud URL Imports](cloud-urls.md) for authentication details.

### Retrying a Failed Job

AIVA does not currently offer an automatic retry button for failed jobs. To retry:

1. Review the error message to identify and address the root cause.
2. Fix the file if the issue is with the source data.
3. Upload the file again with the corrected data or configuration.

---

## Job Concurrency

AIVA processes multiple jobs in parallel. The system allocates processing slots by handler type:

- **Parsing**: Up to 10 concurrent jobs.
- **Downloading**: Up to 10 concurrent jobs.
- **Annotation** (Small Variant Annotation / Structural Variant Annotation): Up to 10 concurrent jobs.

If all slots for a given type are occupied, new jobs of that type remain in the **Queued** state until a slot becomes available. Jobs of other types continue processing independently.

!!! info "Job polling interval"
    The job processor checks for new queued jobs every 5 seconds. There may be a brief delay between submission and the start of processing.

---

## Best Practices

- **Check the Job Manager after submitting uploads** to confirm your jobs have entered the queue.
- **Review error messages promptly** when jobs fail, so you can correct issues and re-upload without delay.
- **Use descriptive sample names** during upload to make it easier to identify jobs in the manager, especially when processing multiple files.
- **Keep your browser tab open** during critical uploads to receive real-time SSE notifications the moment processing completes.

---

## Next Steps

- [:octicons-arrow-right-24: Upload a file](uploading-files.md)
- [:octicons-arrow-right-24: Import from cloud storage](cloud-urls.md)
- [:octicons-arrow-right-24: View your data in the table](../data-table/index.md)
- [:octicons-arrow-right-24: Ask AIVA about your data](../aiva-chat/index.md)
