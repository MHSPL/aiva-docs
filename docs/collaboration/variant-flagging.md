---
title: Variant Flagging
description: Flag individual variants with clinical classification categories in AIVA for tracking, review, and export.
---

# Variant Flagging

Variant flagging lets you mark individual variants with clinical significance categories as you review your data. Flags persist across sessions, are visible to all project collaborators, and can be exported for clinical reports.

---

## Flagging a Variant

1. Open a sample in the [Data Table](../data-table/index.md).
2. Locate the variant you want to flag.
3. Click the **Flag** action on the variant row.
4. Select a flag category from the dropdown.
5. The flag is saved immediately and appears as a visual indicator on the row.

---

## Flag Categories

AIVA provides standard clinical variant classification categories:

| Category | Description |
|----------|-------------|
| **Pathogenic** | The variant is disease-causing based on available evidence. |
| **Likely Pathogenic** | There is strong but not definitive evidence that the variant is disease-causing. |
| **VUS** (Variant of Uncertain Significance) | The clinical significance of the variant is uncertain. |
| **Likely Benign** | There is evidence suggesting the variant is not disease-causing. |
| **Benign** | The variant is considered non-pathogenic based on available evidence. |
| **Custom** | User-defined labels for categories not covered by the standard set. |

These categories align with the ACMG/AMP five-tier classification system. For detailed evidence-based classification using ACMG criteria, see [ACMG Classification](../analysis/acmg-classification.md).

!!! info "Flags vs. ACMG Classification"
    Flags are quick labels for triaging and tracking variants during review. ACMG classification is a detailed, criteria-based assessment. You can use both: flag variants during initial review, then apply formal ACMG classification for variants that require evidence-based interpretation.

---

## Viewing Flagged Variants

Flagged variants are indicated in the data table with a visual marker (colored indicator or icon) in the flag column. You can:

- **Sort by flag**: Click the flag column header to group flagged variants together.
- **Filter by flag category**: Use the column filter on the flag column to view only variants flagged with a specific category (e.g., show only Pathogenic and Likely Pathogenic).

---

## Updating and Removing Flags

To change a flag:

1. Click the flag indicator on the variant row.
2. Select a different category, or click **Remove Flag** to unflag the variant.

Flag changes are saved immediately and reflected for all project collaborators.

---

## Flags in Collaborative Projects

When a sample is part of a [project](projects.md):

- **Editors and Owners** can add, change, and remove flags.
- **Viewers** can see flags but cannot modify them.
- Flags include **user attribution** -- you can see who flagged each variant.
- All flag actions are timestamped for audit purposes.

---

## Exporting Flags

Flagged variants can be exported as a CSV file for clinical reports, lab records, or downstream analysis. See [Exporting Flags and Comments](exporting-flags-comments.md) for details.

---

## Tips

- **Flag during initial review**: As you scan through the data table, flag variants that catch your attention. You can refine the flags later.
- **Use VUS liberally**: When uncertain, flag as VUS. This ensures the variant is tracked for follow-up without prematurely classifying it.
- **Combine with comments**: After flagging a variant, add a [threaded comment](threaded-comments.md) to explain your reasoning or note questions for the team.
- **Filter to review flagged variants**: After completing an initial pass, filter the data table to show only flagged variants for focused secondary review.
