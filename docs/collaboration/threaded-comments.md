---
title: Threaded Comments
description: Add discussion threads to individual variants in AIVA with reply chains, timestamps, and user attribution for collaborative review.
---

# Threaded Comments

Threaded comments let you attach discussions directly to individual variants. Each comment thread is tied to a specific row in the data table, creating a permanent record of the team's interpretation, questions, and decisions.

---

## Adding a Comment

1. Open a sample in the [Data Table](../data-table/index.md).
2. Locate the variant you want to comment on.
3. Click the **Comment** action on the variant row.
4. Type your comment in the text input.
5. Click **Submit** to post the comment.

The comment is saved immediately and visible to all project collaborators.

---

## Reply Chains

Comments support threaded replies, creating a conversation structure:

1. Open the comment thread on a variant (click the comment indicator on the row).
2. View the existing comments in chronological order.
3. Click **Reply** on any comment to add a response.
4. Type your reply and click **Submit**.

Replies are nested under the parent comment, making it clear which comment is being addressed. This is particularly useful when multiple team members are discussing different aspects of the same variant.

---

## Comment Metadata

Each comment includes:

| Field | Description |
|-------|-------------|
| **Author** | The name and email of the user who posted the comment. |
| **Timestamp** | The date and time the comment was posted. |
| **Content** | The text of the comment. |
| **Thread position** | Whether the comment is a top-level comment or a reply, and its position in the thread. |

---

## Comments in Collaborative Projects

When a sample belongs to a [project](projects.md):

- **Editors and Owners** can add comments and replies.
- **Viewers** can read comments but cannot post or reply.
- Comments from all collaborators appear in the same thread, attributed to their respective authors.
- Comment history is preserved even if a collaborator is later [removed from the project](sharing-and-roles.md#removing-collaborators).

---

## Viewing Comment Indicators

Variants that have comments display a comment indicator (icon or badge) in the data table. The indicator may show the number of comments in the thread.

- Click the indicator to expand the comment thread.
- Variants with no comments show no indicator.

---

## Use Cases

### Clinical variant review

During case review, team members can:

1. Flag a variant as VUS.
2. Add a comment explaining the initial assessment: "gnomAD AF is 0.003, SIFT predicts deleterious, but no ClinVar entry. Needs literature review."
3. Another team member replies with findings: "Found two case reports in PubMed linking this gene to the patient's phenotype."
4. A third team member updates the flag to Likely Pathogenic and comments: "Reclassified based on literature evidence and functional prediction scores."

### Research collaboration

Research teams can use comments to:

- Note variants for follow-up validation in the wet lab.
- Discuss population frequency discrepancies across databases.
- Document why certain variants were included or excluded from downstream analysis.

---

## Exporting Comments

Comment threads can be exported as part of the [flag and comment export](exporting-flags-comments.md). The export includes the full thread with author names, timestamps, and reply structure.

---

## Tips

- **Be specific**: Reference specific evidence (allele frequencies, prediction scores, literature) in your comments to make the discussion actionable.
- **Use replies, not new comments**: When responding to a point, use the reply feature to keep the conversation threaded and organized.
- **Combine with flags**: Flag a variant to categorize it, then add a comment to explain the rationale. This combination is especially valuable for clinical documentation.
- **Check for existing comments**: Before adding a comment, review the existing thread to avoid duplicating observations or questions.
