---
title: Sharing and Roles
description: Invite collaborators to AIVA projects by email and manage access with role-based permissions (Owner, Editor, Viewer).
---

# Sharing and Roles

AIVA uses role-based access control to manage collaboration on projects. You invite collaborators by email and assign a role that determines their permissions within the project.

---

## Inviting Collaborators

1. Open the project you want to share.
2. Navigate to the project's **Sharing** or **Collaborators** settings.
3. Enter the collaborator's **email address**.
4. Select a **role** (Editor or Viewer).
5. Click **Invite**.

The collaborator receives an invitation. Once they accept, the project and its samples appear in their AIVA workspace.

!!! note "Account required"
    Invited collaborators must have a AIVA account. If the email address is not associated with an existing account, the recipient will need to [create an account](../getting-started/account-setup.md) before they can access the project.

---

## Roles and Permissions

AIVA defines three roles for project collaboration:

| Permission | Owner | Editor | Viewer |
|------------|:-----:|:------:|:------:|
| View samples and data | Yes | Yes | Yes |
| Use the data table (filter, sort, export) | Yes | Yes | Yes |
| Query data with AIVA | Yes | Yes | Yes |
| Flag variants | Yes | Yes | No |
| Add and reply to comments | Yes | Yes | No |
| Apply ACMG classifications | Yes | Yes | No |
| Add/remove samples | Yes | Yes | No |
| Invite collaborators | Yes | Yes | No |
| Change collaborator roles | Yes | No | No |
| Remove collaborators | Yes | No | No |
| Edit project name/description | Yes | Yes | No |
| Delete project | Yes | No | No |

### Owner

The user who creates a project is automatically the Owner. There is one Owner per project. The Owner has full control over the project, including managing collaborators, modifying project settings, and deleting the project.

### Editor

Editors can contribute to the analysis: flag variants, add comments, apply ACMG classifications, assign samples, and invite additional collaborators. Editors cannot change other collaborators' roles or delete the project.

### Viewer

Viewers have read-only access. They can view all samples and data, use the data table, and query data with AIVA. They cannot modify flags, comments, classifications, or project settings.

---

## Changing Roles

Only the project Owner can change a collaborator's role:

1. Open the project's **Collaborators** settings.
2. Locate the collaborator.
3. Select the new role from the dropdown.
4. Confirm the change.

Role changes take effect immediately. If a collaborator is downgraded from Editor to Viewer, they lose the ability to add flags, comments, and classifications but retain read access.

---

## Removing Collaborators

The project Owner can remove a collaborator:

1. Open the project's **Collaborators** settings.
2. Locate the collaborator to remove.
3. Click the **Remove** action.
4. Confirm the removal.

!!! info "Removed collaborators' contributions"
    Flags, comments, and ACMG classifications created by a removed collaborator remain in the project. They are attributed to the original author and are not deleted when the collaborator is removed.

---

## Access and Data Isolation

- **Project-scoped access**: Collaborators can only see samples assigned to the shared project. They cannot access the Owner's other samples or projects.
- **AIVA respects project boundaries**: When a collaborator queries data with AIVA, the AI can only access data from samples within projects the collaborator has access to.
- **Audit trail**: All flag, comment, and classification actions are attributed to the user who performed them, with timestamps for accountability.

---

## Tips

- **Use Viewer role for stakeholders**: Give Viewer access to lab directors, referring clinicians, or other stakeholders who need to review results without modifying annotations.
- **Use Editor role for analysts**: Assign Editor to team members actively involved in variant interpretation and annotation.
- **Review access regularly**: Remove collaborators who no longer need access, especially for projects involving sensitive clinical data.
