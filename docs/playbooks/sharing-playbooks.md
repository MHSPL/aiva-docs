---
title: Sharing Playbooks
description: Publish playbooks to the AIVA community marketplace or share them privately within your team.
---

# Sharing Playbooks

Playbooks can be shared publicly through the marketplace or privately within your team. Sharing standardized workflows helps ensure consistency across analysts and reduces the time spent setting up recurring analyses.

---

## Sharing Options

### Public (Marketplace)

Publishing a playbook to the marketplace makes it available to all AIVA users.

1. Open the playbook you want to share.
2. Click **Publish to Marketplace**.
3. Select a **category** for the playbook (Clinical Variant Interpretation, Pharmacogenomics, etc.).
4. Add **tags** to help users find it (e.g., "BRCA," "rare disease," "pharmacogenomics").
5. Review the playbook content -- once published, it is visible to all users.
6. Click **Publish**.

Your playbook appears in the [marketplace](browsing-playbooks.md) and can be used or forked by other users.

### Team (Private)

Share a playbook within your team through a [project](../collaboration/projects.md).

1. Open the playbook.
2. Click **Share with Team** or **Share to Project**.
3. Select the project or team to share with.
4. Team members see the playbook in their Playbooks section with a team indicator.

Team-shared playbooks are not visible in the public marketplace.

---

## Managing Shared Playbooks

### Updating a Published Playbook

When you update a published playbook:

1. Edit the playbook content.
2. Publish a new version.
3. Users who have previously used the playbook see an "Update Available" indicator.
4. Users who forked the playbook can choose to merge your updates into their copy.

### Usage Statistics

For published playbooks, you can view:

- **Total uses** -- How many times the playbook has been run.
- **Forks** -- How many users have forked it.
- **Recent activity** -- Usage trends over time.

### Unpublishing

To remove a playbook from the marketplace:

1. Open the playbook.
2. Click **Unpublish**.
3. The playbook is removed from the marketplace but remains in your personal library.

!!! note "Forks persist"
    If other users have forked your playbook, their copies remain even after you unpublish the original. Forks are independent copies.

---

## Forking and Attribution

When a user forks your playbook:

- The fork includes a link back to your original playbook.
- Your name appears as the original author.
- The user can modify their fork freely without affecting your original.
- If you publish updates, fork owners are notified and can choose to merge changes.

---

## Best Practices for Shared Playbooks

- **Write clear descriptions** -- Explain what the playbook does, what type of data it works best with, and any prerequisites (e.g., "Requires VCF with Small Variant Annotation applied").
- **Test thoroughly** -- Run the playbook against several samples to ensure steps work correctly in different scenarios.
- **Use meaningful step titles** -- Step titles help users understand the workflow at a glance.
- **Include a recommended sample type** -- Note whether the playbook is designed for WGS, WES, gene panel, or other data types.
- **Version thoughtfully** -- When updating, include a changelog note explaining what changed and why.
