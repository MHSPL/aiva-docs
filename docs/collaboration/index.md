---
title: Collaboration
description: Overview of AIVA's collaboration features including projects, sharing, variant flagging, threaded comments, and data export.
---

# Collaboration

AIVA is designed for teams. Whether you are a clinical genetics lab reviewing diagnostic cases or a research group analyzing cohort data, the collaboration features let you organize work into projects, share data with colleagues, annotate variants with flags and comments, and export your findings.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Projects

Create projects to group related samples, set descriptions, and organize your analysis workflow.

[:octicons-arrow-right-24: Projects](projects.md)

</div>

<div class="card" markdown>

### Sharing and Roles

Invite collaborators by email and assign roles (Owner, Editor, Viewer) to control access.

[:octicons-arrow-right-24: Sharing and Roles](sharing-and-roles.md)

</div>

<div class="card" markdown>

### Variant Flagging

Flag individual variants with clinical categories (Pathogenic, VUS, Benign, etc.) and custom labels.

[:octicons-arrow-right-24: Variant Flagging](variant-flagging.md)

</div>

<div class="card" markdown>

### Threaded Comments

Add comments to specific variants with reply chains, timestamps, and user attribution.

[:octicons-arrow-right-24: Threaded Comments](threaded-comments.md)

</div>

<div class="card" markdown>

### Exporting Flags and Comments

Download flagged variants and comment threads as CSV for clinical reports and audit trails.

[:octicons-arrow-right-24: Exporting Flags and Comments](exporting-flags-comments.md)

</div>

</div>

---

## How Collaboration Works

The collaboration workflow in AIVA follows a straightforward pattern:

1. **Create a project**: Define a project with a name and description to group related samples.
2. **Add samples**: Assign uploaded samples to the project. See [Managing Samples](../samples/managing-samples.md).
3. **Invite collaborators**: Share the project with team members by email, assigning appropriate roles.
4. **Annotate together**: Team members flag variants, leave comments, and classify variants using ACMG criteria.
5. **Export results**: Download flags and comments for clinical reports, publications, or audit documentation.

!!! info "Role-based access"
    Each collaborator has a role that determines what they can do within the project. See [Sharing and Roles](sharing-and-roles.md) for a breakdown of permissions by role.

---

## Collaboration and AI Analysis

Collaboration features integrate with AIVA and the analysis tools:

- **AIVA queries project data**: When working within a project, AIVA can query data from all samples in the project. Ask questions like "How many pathogenic-flagged variants are across all samples in this project?"
- **Flags visible in the data table**: Flagged variants are highlighted in the [Data Table](../data-table/index.md), so all team members see the same annotations.
- **Comments as discussion threads**: Use [threaded comments](threaded-comments.md) to discuss variant interpretations directly on the variant row, keeping the conversation attached to the data.
- **ACMG classification**: The [ACMG classifier](../analysis/acmg-classification.md) lets team members independently assess variants and compare classifications.
