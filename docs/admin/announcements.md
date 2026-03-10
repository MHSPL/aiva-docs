---
title: Announcements
description: Create, manage, and publish platform announcements in AIVA's "What's New" system to communicate updates and important notices.
---

# Announcements

The Announcements system allows administrators to communicate platform updates, new features, maintenance notices, and other important information to users through the "What's New" notification system.

---

## How Announcements Work

When an administrator publishes an announcement:

1. A notification indicator appears in the user's navigation bar.
2. Users click the notification to view the announcement.
3. Announcements are displayed in reverse chronological order (newest first).
4. Users can mark announcements as read.

---

## Creating an Announcement

1. Navigate to **Administration > Announcements**.
2. Click **New Announcement**.
3. Fill in the announcement details:

| Field | Description |
|-------|-------------|
| **Title** | A concise title for the announcement (displayed in the notification list). |
| **Body** | The full announcement content. Supports rich text formatting (bold, italic, lists, links, code blocks). |
| **Priority** | Priority level that controls visual prominence. |
| **Publish date** | When the announcement should appear. Set to now for immediate publishing, or schedule a future date. |

4. Click **Preview** to review the announcement as users will see it.
5. Click **Publish** to make it live (or **Save as Draft** to publish later).

---

## Priority Levels

| Priority | Visual Treatment | Use Case |
|----------|-----------------|----------|
| **Critical** | Highlighted banner, persistent notification | Security updates, breaking changes, urgent maintenance |
| **High** | Prominent notification badge | Major new features, important policy changes |
| **Normal** | Standard notification | Feature updates, improvements, minor changes |
| **Low** | Quiet notification | Tips, minor updates, informational notices |

---

## Managing Announcements

### Editing an Announcement

1. Navigate to **Administration > Announcements**.
2. Find the announcement in the list.
3. Click **Edit**.
4. Modify the title, body, priority, or publish date.
5. Click **Update**.

!!! note "Editing published announcements"
    Editing a published announcement updates it in place. Users who have already read it will not receive a new notification unless you change the priority to a higher level.

### Unpublishing an Announcement

To remove an announcement from user visibility:

1. Find the announcement in the list.
2. Click **Unpublish**.
3. The announcement is moved to drafts and no longer visible to users.

### Deleting an Announcement

1. Find the announcement in the list.
2. Click **Delete**.
3. Confirm the deletion.

Deleted announcements are permanently removed.

---

## Drafts

Save announcements as drafts to prepare content before publishing:

- Drafts are visible only to administrators.
- Edit drafts at any time before publishing.
- Schedule drafts for future publication by setting a publish date.

---

## Announcement Best Practices

- **Keep titles concise** -- Users scan notification lists quickly. A clear title helps them decide which announcements to read.
- **Use priority levels appropriately** -- Reserve Critical and High for truly important updates. Overusing high priority reduces its effectiveness.
- **Include actionable information** -- Tell users what changed and what they need to do (if anything).
- **Link to documentation** -- Reference relevant documentation pages for detailed information about new features.
- **Announce on a regular cadence** -- Regular update announcements build user trust and engagement. Use the [Changelog](../changelog.md) for comprehensive release notes.

---

## Example Announcements

### New Feature Announcement

> **Title**: Knowledge Graph now includes drug interaction data
>
> **Body**: The AIVA Knowledge Graph has been expanded with drug-protein interaction data from DrugBank. You can now ask AIVA questions like "What drugs target the EGFR protein?" and receive results from the updated knowledge graph. See the [Knowledge Graph documentation](../aiva-chat/knowledge-graph.md) for details.
>
> **Priority**: Normal

### Maintenance Notice

> **Title**: Scheduled maintenance -- March 15, 2026
>
> **Body**: AIVA will undergo scheduled maintenance on March 15, 2026, from 2:00 AM to 4:00 AM UTC. During this time, the platform will be unavailable. No data will be affected. Please plan your work accordingly.
>
> **Priority**: High

### Security Update

> **Title**: Important: Update your password
>
> **Body**: We have enhanced our authentication security. All users are required to update their passwords by March 31, 2026. Passwords must now meet the following requirements: minimum 12 characters, at least one uppercase letter, one number, and one special character.
>
> **Priority**: Critical
