---
title: ACMG Classification
description: Apply ACMG/AMP variant classification criteria interactively in AIVA with auto-calculated pathogenicity.
---

# ACMG Classification

AIVA includes an interactive ACMG/AMP variant classifier that lets you apply evidence-based criteria to individual variants. The classifier automatically calculates the five-tier pathogenicity classification based on the criteria you select.

For details on the ACMG/AMP framework and criteria definitions, see the [ACMG/AMP Guidelines](../classification/acmg-amp-guidelines.md) reference.

---

## Using the Classifier

### Step 1: Open the classifier

1. Open a sample in the [Data Table](../data-table/index.md) or [Tertiary Analysis](tertiary-analysis.md) view.
2. Locate the variant you want to classify.
3. Click the **ACMG Classification** action on the variant row.
4. The classification panel opens, displaying all 28 criteria organized by category.

### Step 2: Select applicable criteria

1. Review each criterion and determine whether it applies to the variant based on available evidence.
2. **Check** the criteria that are met. You can select any combination of pathogenic and benign criteria.
3. For each selected criterion, you may add a note documenting the specific evidence (e.g., "gnomAD AF = 0.0001, absent in controls").

### Step 3: Review the auto-calculated classification

As you select criteria, the classifier automatically calculates the resulting classification using the ACMG/AMP combining rules. The classification updates in real time as you add or remove criteria.

| Classification | Meaning |
|----------------|---------|
| **Pathogenic** | The variant is disease-causing with strong supporting evidence. |
| **Likely Pathogenic** | The variant is probably disease-causing (>90% certainty). |
| **VUS** | Insufficient evidence to classify definitively. |
| **Likely Benign** | The variant is probably not disease-causing (>90% certainty). |
| **Benign** | The variant is non-pathogenic with strong supporting evidence. |

### Step 4: Save the classification

1. Review the selected criteria and the auto-calculated classification.
2. Click **Save** to store the classification.
3. The classification is associated with the variant and visible in the data table and to all project collaborators.

---

## Evidence Tracking

Each ACMG classification in AIVA includes:

- The selected criteria with any associated notes.
- The auto-calculated classification tier.
- The user who performed the classification.
- The timestamp of the classification.
- A history of changes if the classification is updated over time.

This evidence trail supports clinical documentation and audit requirements.

---

## Collaborative Classification

When a sample belongs to a [project](../collaboration/projects.md):

- **Editors and Owners** can create and modify ACMG classifications.
- **Viewers** can view existing classifications but cannot modify them.
- Multiple team members can independently classify the same variant, allowing for comparison and consensus building.

---

## Tips

!!! tip "Use AIVA to gather evidence"
    Before classifying a variant, ask AIVA to look up relevant information: "What is the gnomAD allele frequency, ClinVar classification, and SIFT/PolyPhen prediction for chr17:41245466 G>A?" Use the results to inform your criteria selections.

- **Document your reasoning**: Add notes to each selected criterion explaining the specific evidence.
- **Start with population frequency**: Check gnomAD allele frequency first. If AF > 5%, the variant is classified as Benign (BA1). This eliminates many variants quickly.
- **Revisit VUS variants**: Variants classified as VUS should be periodically re-evaluated as new evidence becomes available.
