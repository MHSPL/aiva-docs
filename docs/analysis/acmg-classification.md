---
title: ACMG Classification
description: Apply ACMG/AMP variant classification criteria interactively in AIVA with auto-calculated pathogenicity from Pathogenic to Benign.
---

# ACMG Classification

AIVA includes an interactive ACMG/AMP variant classifier that lets you apply evidence-based criteria to individual variants. The classifier automatically calculates the five-tier pathogenicity classification based on the criteria you select.

---

## Overview

The American College of Medical Genetics and Genomics (ACMG) and the Association for Molecular Pathology (AMP) published guidelines for interpreting sequence variants. These guidelines define 28 criteria across categories of evidence strength, which combine to produce a classification:

| Classification | Description |
|----------------|-------------|
| **Pathogenic** | The variant is disease-causing with strong supporting evidence. |
| **Likely Pathogenic** | The variant is probably disease-causing (>90% certainty). |
| **Uncertain Significance (VUS)** | There is insufficient evidence to classify the variant definitively. |
| **Likely Benign** | The variant is probably not disease-causing (>90% certainty). |
| **Benign** | The variant is non-pathogenic with strong supporting evidence. |

---

## ACMG Criteria Reference

The classifier organizes criteria by evidence type and strength:

### Pathogenic Criteria

| Strength | Criteria | Description |
|----------|----------|-------------|
| **Very Strong** | PVS1 | Null variant (nonsense, frameshift, canonical splice site, initiation codon, single/multi-exon deletion) in a gene where loss of function is a known mechanism of disease. |
| **Strong** | PS1 | Same amino acid change as a previously established pathogenic variant, regardless of nucleotide change. |
| | PS2 | De novo (both maternity and paternity confirmed) in a patient with the disease and no family history. |
| | PS3 | Well-established functional studies show a deleterious effect on the gene product. |
| | PS4 | Prevalence of the variant in affected individuals is significantly increased compared to controls. |
| **Moderate** | PM1 | Located in a mutational hot spot and/or critical, well-established functional domain without benign variation. |
| | PM2 | Absent from controls (or at extremely low frequency) in population databases (gnomAD, ExAC, 1000 Genomes). |
| | PM3 | Detected in trans with a pathogenic variant for recessive disorders. |
| | PM4 | Protein length changes due to in-frame deletions/insertions in a non-repeat region, or stop-loss variants. |
| | PM5 | Novel missense change at an amino acid residue where a different missense change has been determined to be pathogenic. |
| | PM6 | Assumed de novo, but without confirmation of paternity and maternity. |
| **Supporting** | PP1 | Co-segregation with disease in multiple affected family members in a gene known to cause the disease. |
| | PP2 | Missense variant in a gene with a low rate of benign missense variation and where missense variants are a common mechanism of disease. |
| | PP3 | Multiple lines of computational evidence support a deleterious effect (conservation, evolutionary, splicing impact, etc.). |
| | PP4 | Patient's phenotype or family history is highly specific for a disease with a single genetic etiology. |
| | PP5 | Reputable source recently reports variant as pathogenic, but evidence is not available for independent evaluation. |

### Benign Criteria

| Strength | Criteria | Description |
|----------|----------|-------------|
| **Stand-alone** | BA1 | Allele frequency is >5% in population databases (gnomAD, ExAC, 1000 Genomes). |
| **Strong** | BS1 | Allele frequency is greater than expected for the disorder. |
| | BS2 | Observed in a healthy adult individual for a recessive (homozygous), dominant (heterozygous), or X-linked (hemizygous) disorder with full penetrance expected at an early age. |
| | BS3 | Well-established functional studies show no deleterious effect on protein function or splicing. |
| | BS4 | Lack of segregation in affected members of a family. |
| **Supporting** | BP1 | Missense variant in a gene for which primarily truncating variants are known to cause disease. |
| | BP2 | Observed in trans with a pathogenic variant for a fully penetrant dominant gene/disorder, or observed in cis with a pathogenic variant in any inheritance pattern. |
| | BP3 | In-frame deletions/insertions in a repetitive region without a known function. |
| | BP4 | Multiple lines of computational evidence suggest no impact on gene or gene product. |
| | BP5 | Variant found in a case with an alternate molecular basis for disease. |
| | BP6 | Reputable source recently reports variant as benign, but evidence is not available for independent evaluation. |
| | BP7 | A synonymous variant for which splicing prediction algorithms predict no impact, and the nucleotide is not highly conserved. |

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
3. For each selected criterion, you may add a note documenting the specific evidence (e.g., "gnomAD AF = 0.0001, absent in controls -- PM2 met").

### Step 3: Review the auto-calculated classification

As you select criteria, the classifier automatically calculates the resulting classification based on the ACMG/AMP combining rules:

- **Pathogenic**: Requires one of the following combinations:
    - 1 Very Strong AND 1+ Strong
    - 1 Very Strong AND 2+ Moderate
    - 1 Very Strong AND 1 Moderate AND 1 Supporting
    - 1 Very Strong AND 2+ Supporting
    - 2+ Strong
    - 1 Strong AND 3+ Moderate
    - 1 Strong AND 2 Moderate AND 2+ Supporting
    - 1 Strong AND 1 Moderate AND 4+ Supporting

- **Likely Pathogenic**: Requires one of the following:
    - 1 Very Strong AND 1 Moderate
    - 1 Strong AND 1-2 Moderate
    - 1 Strong AND 2+ Supporting
    - 3+ Moderate
    - 2 Moderate AND 2+ Supporting
    - 1 Moderate AND 4+ Supporting

- **Benign**: BA1 alone, OR 2+ Strong benign criteria.

- **Likely Benign**: 1 Strong AND 1 Supporting benign, OR 2+ Supporting benign.

- **VUS**: Criteria do not meet the threshold for any other classification, or there are conflicting pathogenic and benign criteria.

The calculated classification updates in real time as you add or remove criteria.

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

## ACMG Classification in Collaborative Projects

When a sample belongs to a [project](../collaboration/projects.md):

- **Editors and Owners** can create and modify ACMG classifications.
- **Viewers** can view existing classifications but cannot modify them.
- Multiple team members can independently classify the same variant, allowing for comparison and consensus building.
- All classifications are attributed to the user who created them.

---

## Tips

!!! tip "Use AIVA to gather evidence"
    Before classifying a variant, ask AIVA to look up relevant information: "What is the gnomAD allele frequency, ClinVar classification, and SIFT/PolyPhen prediction for chr17:41245466 G>A?" Use the results to inform your criteria selections.

- **Document your reasoning**: Add notes to each selected criterion explaining the specific evidence. This is invaluable for clinical review and auditing.
- **Start with population frequency**: Check gnomAD allele frequency first. If AF > 5%, BA1 applies and the variant is classified as Benign. This eliminates many variants quickly.
- **Use computational predictions for PP3/BP4**: SIFT, PolyPhen, CADD, and conservation scores from Variant Effect Prediction annotations or AIVA lookups directly inform PP3 (deleterious predictions) or BP4 (benign predictions).
- **Revisit VUS variants**: Variants classified as VUS should be periodically re-evaluated as new evidence becomes available in databases and literature.
