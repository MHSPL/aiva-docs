---
title: User Management
description: Manage users, roles, and usage statistics in AIVA's administration panel.
---

# User Management

The User Management section allows administrators to view and manage all user accounts on the AIVA platform, including roles, usage statistics, and account status.

---

## Viewing Users

Navigate to **Administration > Users** to see the user list.

The user table displays:

| Column | Description |
|--------|-------------|
| **Name** | User's display name |
| **Email** | User's email address |
| **Role** | User role (User, Administrator) |
| **Subscription** | Current subscription tier (Free, Plus, Pro, Trial) |
| **Samples** | Number of uploaded samples |
| **Last Active** | Date and time of last login |
| **Created** | Account creation date |
| **Status** | Active, Inactive, or Suspended |

### Searching and Filtering

- **Search** by name or email address.
- **Filter** by role, subscription tier, or status.
- **Sort** by any column.

---

## User Details

Click on a user to view their detailed profile:

### Account Information

- Display name, email, and authentication provider.
- Account creation date and last login.
- Current subscription tier and billing status.

### Usage Statistics

- **Samples uploaded** -- Total count and list of samples.
- **Storage used** -- Total disk space consumed by the user's data.
- **API calls** -- Number of API requests in the current billing period.
- **Chat messages** -- Number of AIVA Chat messages sent.
- **Classifications** -- Number of ACMG classifications created.

### Activity History

A summary of the user's recent actions, pulled from the [audit trail](../compliance/audit-trail.md).

---

## Managing Roles

### Available Roles

| Role | Permissions |
|------|------------|
| **User** | Standard access to all platform features based on subscription tier |
| **Administrator** | Full platform access including administration panel, user management, and system configuration |

### Changing a User's Role

1. Navigate to the user's detail page.
2. Click **Edit Role**.
3. Select the new role.
4. Confirm the change.

!!! warning "Administrator privileges"
    Granting administrator access gives the user full control over the platform, including the ability to view all users' activity, manage accounts, and modify system settings. Assign this role only to trusted personnel.

---

## Account Actions

### Suspending an Account

Suspending an account prevents the user from logging in while preserving their data:

1. Navigate to the user's detail page.
2. Click **Suspend Account**.
3. Confirm the suspension.
4. The user's status changes to "Suspended" and they cannot log in.

To reinstate a suspended account, click **Reactivate Account** on the user's detail page.

### Deleting an Account

!!! danger "Permanent action"
    Deleting a user account permanently removes the user and all associated data (samples, flags, comments, classifications, reports, and conversations). This action cannot be undone.

To delete an account:

1. Navigate to the user's detail page.
2. Click **Delete Account**.
3. Type the user's email to confirm.
4. Click **Delete Permanently**.

---

## Subscription Management

Administrators can view and manage user subscriptions:

- **View current tier** -- See which subscription tier the user is on.
- **View usage against limits** -- Compare the user's usage to their tier's limits.
- **Manage trials** -- Extend or revoke trial access.

For subscription tier details, see [Subscription Tiers](../getting-started/subscription-tiers.md).

---

## Bulk Operations

For managing multiple users:

- **Export user list** -- Download the user list as CSV for external analysis.
- **Bulk role assignment** -- Select multiple users and assign a role.
- **Usage reports** -- Generate aggregate usage reports across all users or filtered groups.
