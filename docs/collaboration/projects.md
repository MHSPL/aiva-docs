---
title: Projects
description: Create and manage projects in AIVA to organize samples, collaborate with team members, and structure your analysis workflow.
---

# Projects

Projects are the organizational unit for collaboration in AIVA. A project groups related samples together and provides a shared workspace for your team.

---

## Creating a Project

1. Navigate to the **Projects** section from the main navigation.
2. Click **Create Project**.
3. Enter a **project name** that identifies the purpose or scope (e.g., "Familial Breast Cancer Cohort" or "Patient 2024-0312").
4. Add an optional **description** to provide context for collaborators.
5. Click **Create**.

The project is created and you are automatically assigned as the **Owner**.

---

## Project Details

Each project displays the following information:

| Field | Description |
|-------|-------------|
| **Name** | The project name. |
| **Description** | An optional free-text description of the project's purpose, cohort, or study design. |
| **Samples** | The number of samples assigned to the project. |
| **Collaborators** | The number of team members with access to the project. |
| **Created date** | When the project was created. |
| **Owner** | The user who created the project. |

---

## Adding Samples to a Project

To add samples to a project:

1. Navigate to the **Samples** section.
2. Locate the sample you want to assign.
3. Use the **Assign to Project** action and select the target project.

Alternatively, from within the project view:

1. Open the project.
2. Click **Add Sample**.
3. Select from your available samples.

Once assigned, the sample and all its data are accessible to every collaborator on the project, subject to their [role permissions](sharing-and-roles.md).

See [Managing Samples](../samples/managing-samples.md) for more details on sample assignment.

---

## Browsing Samples Within a Project

The project view includes a **sample browser** that lists all samples assigned to the project:

- Click a sample name to open it in the [Data Table](../data-table/index.md).
- View sample metadata (file type, row count, annotation status) at a glance.
- Collaborators see the same sample list according to their role.

---

## Editing a Project

Project Owners and Editors can update the project:

- **Rename**: Click the project name to edit it.
- **Update description**: Modify the description to reflect changes in scope or methodology.

---

## Deleting a Project

Only the project **Owner** can delete a project:

1. Open the project settings.
2. Click **Delete Project**.
3. Confirm the deletion.

!!! warning "Deleting a project does not delete samples"
    Removing a project unlinks its samples but does not delete the sample data itself. Samples remain in your sample list and can be reassigned to other projects. However, any [flags](variant-flagging.md) and [comments](threaded-comments.md) created within the project context will be removed.

---

## Tips

- **One project per study or case**: Create separate projects for distinct clinical cases, research studies, or analysis batches to keep data and annotations organized.
- **Use descriptions**: Add enough detail to the project description so collaborators understand the context without needing external documentation.
- **Review collaborator roles**: Periodically check that the roles assigned to collaborators still match their responsibilities. See [Sharing and Roles](sharing-and-roles.md).
