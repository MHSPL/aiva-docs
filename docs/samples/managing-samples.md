---
title: Managing Samples
description: View, organize, delete, and assign genomic data samples to projects in AIVA.
---

# Managing Samples

Once your files have been uploaded and processed, they appear in your sample list. This page covers how to view, organize, and manage your samples.

---

## Viewing Your Samples

Navigate to the **Samples** section to see a list of all your samples. Each entry displays:

- **Sample name**: The file name or a custom name you have assigned.
- **File type**: VCF, CSV, or TSV.
- **Row count**: The number of data rows (variants or records) in the sample.
- **Upload date**: When the sample was uploaded.
- **Status**: Processing status (e.g., Ready, Processing, Error).
- **Annotations**: Whether Small Variant Annotation or Structural Variant Annotation annotation was applied.

Click on any sample to open it in the [Data Table](../data-table/index.md) for exploration and analysis.

---

## Sample Metadata

Each sample has associated metadata that you can view:

- **File name**: The original file name as uploaded.
- **File size**: The size of the uploaded file.
- **Format**: VCF, CSV, or TSV.
- **Total variants/rows**: The number of records loaded into the database.
- **Upload timestamp**: The date and time the file was uploaded.
- **Annotation status**: Whether Small Variant Annotation or Structural Variant Annotation was applied, and the annotation job status.
- **Project assignment**: Which [project](../collaboration/projects.md) the sample belongs to, if any.

---

## Deleting Samples

To delete a sample:

1. Navigate to the **Samples** section.
2. Locate the sample you want to delete.
3. Click the **Delete** action (trash icon or delete button) for that sample.
4. Confirm the deletion in the dialog that appears.

!!! warning "Deletion is permanent"
    Deleting a sample removes the sample record and all associated variant data from the database. This action cannot be undone. Any [flags](../collaboration/variant-flagging.md), [comments](../collaboration/threaded-comments.md), or [ACMG classifications](../analysis/acmg-classification.md) associated with variants in the sample will also be removed.

---

## Assigning Samples to Projects

Samples can be organized into [projects](../collaboration/projects.md) for collaboration and grouping:

1. Navigate to the **Samples** section.
2. Locate the sample you want to assign.
3. Select the **Assign to Project** option.
4. Choose an existing project from the dropdown, or create a new project.
5. Confirm the assignment.

Once assigned, the sample is visible to all collaborators on that project according to their [roles](../collaboration/sharing-and-roles.md).

!!! info "Samples in multiple projects"
    A sample can belong to one project at a time. To share the same data with multiple teams, consider creating a project that includes all relevant collaborators.

---

## Sample States

Samples progress through the following states during processing:

| State | Description |
|-------|-------------|
| **Uploading** | The file is being uploaded to the server. |
| **Downloading** | The file is being downloaded from a [cloud URL](cloud-urls.md). |
| **Annotating** | Small Variant Annotation or Structural Variant Annotation annotation is running. |
| **Parsing** | The file is being parsed and loaded into the database. |
| **Ready** | Processing is complete. The sample is available for exploration. |
| **Error** | An error occurred during processing. Check the [Job Manager](job-monitoring.md) for details. |

---

## Tips

- **Name your samples meaningfully**: Use patient IDs, experiment names, or descriptive labels so you can quickly find samples later.
- **Check status before analysis**: Ensure a sample is in the **Ready** state before attempting to open it in the data table or reference it in AIVA queries.
- **Clean up old samples**: Delete samples you no longer need to keep your workspace organized and within your [subscription tier's](../getting-started/subscription-tiers.md) upload limits.
