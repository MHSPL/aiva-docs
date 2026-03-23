---
title: Sample Linking
description: Link flagged variants, comments, and ACMG classifications from your AIVA samples directly into clinical and research reports.
---

# Sample Linking

Sample linking connects your analysis evidence (flagged variants, threaded comments, and ACMG classifications) directly to report sections. This ensures reports are grounded in the specific data and interpretations from your analysis workflow.

---

## What Can Be Linked

| Evidence Type | What It Includes |
|---------------|-----------------|
| **Flagged variants** | Variant position, gene, consequence, flag type (Pathogenic, VUS, Benign, Review, Favorite), and any notes attached to the flag |
| **ACMG classifications** | Selected ACMG/AMP criteria, calculated classification tier (Pathogenic through Benign), and evidence notes |
| **Threaded comments** | All comments in the thread associated with a specific variant, including author and timestamp |
| **Sample metadata** | Sample name, file format, upload date, annotation status, and variant counts |

---

## Linking Variants to a Report

### Step 1: Ensure Variants Are Flagged

Before linking, flag the variants you want to include in the report. Each flag type (Pathogenic, VUS, Benign, Review, Favorite) carries over into the report.

### Step 2: Open the Report Editor

Navigate to the report you want to populate and open it in the editor.

### Step 3: Insert Linked Evidence

1. Place your cursor in the section where you want to add linked evidence.
2. Click the **Link Evidence** or **Insert Variants** button in the section toolbar.
3. A panel shows all flagged variants from the associated sample(s).
4. Select the variants you want to link to this section.
5. Click **Insert**.

The linked variants appear in the report section as structured entries with their associated data.

---

## How Linked Evidence Appears

Linked evidence is rendered in the report as structured blocks:

- **Variant entries** include the variant position, gene, consequence, flag type, and any attached notes or ACMG classification.
- **Comment threads** appear as quoted text with author attribution and timestamps.
- **Classification summaries** show the applied ACMG criteria and the resulting classification tier.

These blocks are live references. If you update a flag, comment, or classification in the analysis view, the linked evidence in the report reflects the update.

!!! note "Snapshots on export"
    When you export a report, linked evidence is rendered as static content at the time of export. Subsequent changes to flags or classifications will not appear in previously exported documents.

---

## Linking Multiple Samples

If your report covers multiple samples (e.g., a family study or cohort analysis):

1. Associate multiple samples with the report during creation or from the report settings.
2. When inserting linked evidence, use the sample filter to select variants from specific samples.
3. Each linked variant includes its source sample name for clarity.

---

## Unlinking Evidence

To remove linked evidence from a report section:

1. Click on the linked evidence block in the editor.
2. Select **Unlink** or **Remove**.
3. The evidence block is removed from the report. The underlying flag, comment, or classification is not affected.

---

## Best Practices

- **Flag and classify before reporting**: Complete your variant interpretation workflow before creating the report. This ensures all relevant evidence is available for linking.
- **Organize by section**: Link pathogenic variants to the "Results" section, VUS variants to a "VUS" section, and pharmacogenomic findings to the appropriate section.
- **Use AI Auto-Fill after linking**: When you run [AI Auto-Fill](ai-auto-fill.md) on a section with linked variants, the AI uses those variants as context to generate more specific and accurate content.
- **Review linked data**: Verify that linked classifications and comments are current before finalizing the report.
