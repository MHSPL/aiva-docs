---
title: Variant Classifier
description: AIVA's public ACMG variant classification tool for evidence-based variant interpretation using ACMG/AMP guidelines.
---

# Variant Classifier

The AIVA Variant Classifier is a public, no-login-required tool for classifying genomic variants according to the ACMG/AMP (American College of Medical Genetics and Genomics / Association for Molecular Pathology) guidelines. It provides an interactive interface for selecting evidence criteria and calculating variant classifications.

---

## Key Features

- **Public access** -- No account or login required. Available to anyone.
- **ACMG/AMP compliant** -- Implements the 2015 ACMG/AMP standards and guidelines for variant interpretation.
- **Interactive criteria selection** -- Select applicable evidence criteria from a comprehensive list.
- **Automatic classification** -- Classification is calculated automatically as criteria are selected.
- **Educational tool** -- Learn how ACMG criteria combine to produce classifications.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Using the Classifier

Step-by-step guide to entering variant information, selecting ACMG criteria, and obtaining a classification.

[:octicons-arrow-right-24: Using the Classifier](using-the-classifier.md)

</div>

<div class="card" markdown>

</div>

</div>

---

## How It Works

1. Enter variant information (gene, variant notation, or genomic coordinates).
2. Review and select applicable ACMG/AMP evidence criteria.
3. The classifier calculates the five-tier classification based on the selected criteria.
4. Review the classification and the evidence summary.

The classification follows the standard ACMG/AMP five-tier system:

| Classification | Criteria Combination |
|---------------|---------------------|
| **Pathogenic** | Strong pathogenic evidence (e.g., 1 Very Strong + 1 Strong, or 2 Strong) |
| **Likely Pathogenic** | Moderate pathogenic evidence (e.g., 1 Strong + 1-2 Supporting) |
| **Uncertain Significance (VUS)** | Insufficient or conflicting evidence |
| **Likely Benign** | Moderate benign evidence (e.g., 1 Strong + 1 Supporting benign) |
| **Benign** | Strong benign evidence (e.g., 1 Stand-Alone or 2 Strong benign) |

---

## Public vs. In-App Classification

| Feature | Public Classifier | In-App ACMG Classification |
|---------|-------------------|---------------------------|
| **Login required** | No | Yes |
| **Sample data access** | No -- manual entry only | Yes -- auto-populated from sample |
| **Save classifications** | No | Yes -- saved to variant |
| **Integration with flags/comments** | No | Yes |
| **Report linking** | No | Yes |

For in-app ACMG classification with full integration, see [ACMG Classification](../analysis/acmg-classification.md).

!!! info "Educational use"
    The public Variant Classifier is an excellent tool for training and education. Use it to practice applying ACMG criteria to example variants, or to demonstrate the classification framework to students and colleagues.
