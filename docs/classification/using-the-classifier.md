---
title: Using the Classifier
description: Step-by-step guide to using AIVA's public ACMG variant classification tool for evidence-based variant interpretation.
---

# Using the Classifier

This guide walks you through the AIVA Variant Classifier, a public tool for classifying variants according to ACMG/AMP guidelines. No login is required.

---

## Step 1: Access the Classifier

Navigate to the Variant Classifier from the AIVA homepage or public navigation menu. The classifier is accessible without an account.

---

## Step 2: Enter Variant Information

Provide information about the variant you want to classify:

- **Gene** -- The gene symbol (e.g., BRCA1, TP53, MLH1).
- **Variant notation** -- HGVS coding or protein notation (e.g., c.5266dupC, p.Gln1756Profs*74).
- **Genomic coordinates** (optional) -- Chromosome, position, reference allele, and alternate allele.
- **Transcript** (optional) -- The reference transcript identifier (e.g., NM_007294.4).

!!! tip "Variant identifiers"
    You can enter the variant in any commonly used format. The classifier accepts HGVS nomenclature, genomic coordinates (GRCh37 or GRCh38), and rsIDs.

---

## Step 3: Select ACMG/AMP Criteria

The classifier presents the full list of ACMG/AMP evidence criteria organized by type:

### Pathogenic Criteria

| Category | Criteria | Description |
|----------|----------|-------------|
| **Very Strong** | PVS1 | Null variant in a gene where loss of function is a known mechanism of disease |
| **Strong** | PS1--PS4 | Same amino acid change, functional studies, segregation, prevalence in affected |
| **Moderate** | PM1--PM6 | Hot spot, absent from controls, protein length change, novel missense, assumed de novo, in-frame in non-repeat |
| **Supporting** | PP1--PP5 | Co-segregation, computational, phenotype specificity, reputable source, missense in low-rate gene |

### Benign Criteria

| Category | Criteria | Description |
|----------|----------|-------------|
| **Stand-Alone** | BA1 | Allele frequency above 5% in population databases |
| **Strong** | BS1--BS4 | Frequency greater than expected, observed in healthy adults, functional studies, lack of segregation |
| **Supporting** | BP1--BP7 | Missense in truncation gene, observed in trans, in-frame in benign region, computational, synonymous, reputable source |

For each criterion:

1. **Review the criterion description** to determine whether it applies to your variant.
2. **Click the criterion** to select or deselect it.
3. Selected criteria are highlighted and contribute to the classification calculation.

See [ACMG/AMP Guidelines](acmg-amp-guidelines.md) for detailed descriptions of each criterion.

---

## Step 4: Review the Classification

As you select criteria, the classifier automatically calculates the classification:

- The current classification is displayed prominently (Pathogenic, Likely Pathogenic, VUS, Likely Benign, or Benign).
- A summary shows which criteria are selected and how they combine to produce the classification.
- The classification updates in real time as you add or remove criteria.

### Classification Rules

The classifier follows the standard ACMG/AMP combining rules:

**Pathogenic** requires any of:

- 1 Very Strong AND >= 1 Strong
- 1 Very Strong AND >= 2 Moderate
- 1 Very Strong AND 1 Moderate AND 1 Supporting
- 1 Very Strong AND >= 2 Supporting
- >= 2 Strong
- 1 Strong AND >= 3 Moderate
- 1 Strong AND 2 Moderate AND >= 2 Supporting
- 1 Strong AND 1 Moderate AND >= 4 Supporting

**Likely Pathogenic** requires any of:

- 1 Very Strong AND 1 Moderate
- 1 Strong AND 1-2 Moderate
- 1 Strong AND >= 2 Supporting
- >= 3 Moderate
- 2 Moderate AND >= 2 Supporting
- 1 Moderate AND >= 4 Supporting

**Benign** requires any of:

- 1 Stand-Alone
- >= 2 Strong

**Likely Benign** requires:

- 1 Strong AND 1 Supporting

**VUS** is assigned when criteria do not meet the thresholds for any other classification, or when pathogenic and benign criteria conflict.

---

## Step 5: Document Your Reasoning (Optional)

The classifier allows you to add notes for each selected criterion, documenting the evidence that supports your selection. This is optional for the public tool but recommended for thorough variant interpretation.

---

## Tips for Accurate Classification

- **Apply criteria conservatively** -- Only select a criterion when the evidence clearly supports it.
- **Use multiple evidence types** -- A robust classification draws on population data, computational predictions, functional studies, and clinical observations.
- **Consider conflicting evidence** -- If both pathogenic and benign criteria apply, the variant may be classified as VUS pending additional evidence.
- **Consult the guidelines** -- When uncertain about a criterion, refer to the [ACMG/AMP Guidelines](acmg-amp-guidelines.md) for detailed descriptions and examples.

!!! warning "Classification responsibility"
    The Variant Classifier is a decision-support tool. Clinical variant classifications should be performed by qualified professionals in the context of established laboratory protocols and clinical information.
