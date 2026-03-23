---
title: Variant Classification
description: Classify variants using ACMG/AMP germline or AMP/ASCO/CAP somatic guidelines with manual criteria selection or AI-assisted classification.
---

# Variant Classification

The variant classifier is a default category card on the [Analysis Panel](analysis-panel.md) that appears for all samples. When reviewing a variant in the analysis panel, click **Classify Variant** to open the classifier. AIVA supports both **ACMG/AMP germline** and **AMP/ASCO/CAP somatic** classification frameworks.

For details on the ACMG/AMP framework and how to use the public classifier, see [Using the Variant Classifier](../classification/using-the-classifier.md).

---

## Classification Frameworks

### ACMG/AMP (Germline)

The standard five-tier classification for germline variants:

| Classification | Meaning |
|----------------|---------|
| **Pathogenic** | The variant is disease-causing with strong supporting evidence. |
| **Likely Pathogenic** | The variant is probably disease-causing (>90% certainty). |
| **VUS** | Insufficient evidence to classify definitively. |
| **Likely Benign** | The variant is probably not disease-causing (>90% certainty). |
| **Benign** | The variant is non-pathogenic with strong supporting evidence. |

### AMP/ASCO/CAP (Somatic)

The four-tier classification for somatic variants:

| Tier | Meaning |
|------|---------|
| **Tier I** | Strong clinical significance: FDA-approved therapies or professional guidelines. |
| **Tier II** | Potential clinical significance: investigational therapies or clinical trials. |
| **Tier III** | Unknown clinical significance: no established evidence. |
| **Tier IV** | Benign or likely benign: no known oncogenic role. |

---

## Classification Options

When you click **Classify Variant**, you have two options:

### Manual classification

Select criteria yourself based on your review of the evidence:

1. The classifier displays all applicable criteria organized by category.
2. **Check** the criteria that are met. You can select any combination of pathogenic and benign criteria.
3. For each selected criterion, add a note documenting the specific evidence (e.g., "gnomAD AF = 0.0001, absent in controls").
4. The classification auto-calculates in real time as you add or remove criteria.
5. Review and click **Save**.

### AI classification

Let AIVA classify the variant automatically:

1. Click **AI Classify** to send the variant to an AI sub-agent.
2. The sub-agent analyzes both the patient's **phenotype** and the variant's **annotations** (allele frequency, in silico predictions, ClinVar data, literature) to determine applicable criteria.
3. Results are returned with the suggested classification, selected criteria, and **sources** for each piece of evidence used.
4. Review the AI's reasoning and sources, adjust any criteria if needed, then click **Save**.

!!! tip "AI classification is a starting point"
    Always review the AI's suggested criteria and sources before saving. The AI provides a thorough initial assessment, but clinical judgment should guide the final classification.

---

## Saving and Visibility

1. Review the selected criteria and the auto-calculated classification.
2. Click **Save** to store the classification.
3. The classification is associated with the variant and visible in the table view.

---

## Tips

- **Document your reasoning**: Add notes to each selected criterion explaining the specific evidence.
- **Revisit VUS variants**: Variants classified as VUS should be periodically re-evaluated as new evidence becomes available.
