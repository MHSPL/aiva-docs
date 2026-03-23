---
title: Pharmacogenomics
description: Analyze drug-variant interactions, metabolizer phenotypes, and prescribing implications using AIVA's pharmacogenomics features.
---

# Pharmacogenomics

AIVA's pharmacogenomics features help you identify variants in drug-metabolizing genes, assess their impact on drug response, and review prescribing guidelines. These tools connect genomic findings to actionable medication management decisions.

---

## Overview

Pharmacogenomics (PGx) examines how genetic variants influence drug metabolism, efficacy, and adverse reactions. AIVA supports PGx analysis through:

- **PGx Analysis Card**: A dedicated [analysis card](analysis-cards.md) in the Analysis Hub showing drug-variant interactions and metabolizer phenotypes.
- **Knowledge Graph queries**: Explore drug-gene-protein relationships through the [Knowledge Graph](../aiva-chat/ai-tools.md#knowledge-graph).
- **AIVA Chat**: Ask the AI assistant about specific drug-gene interactions, guidelines, and evidence.

---

## Key Pharmacogenes

AIVA's PGx analysis covers established pharmacogenes, including:

| Gene | Drug Examples | Clinical Impact |
|------|--------------|-----------------|
| **CYP2D6** | Codeine, tramadol, tamoxifen, fluoxetine | Metabolizer status affects drug activation and clearance |
| **CYP2C19** | Clopidogrel, omeprazole, voriconazole | Poor metabolizers may have reduced drug efficacy or increased toxicity |
| **CYP2C9** | Warfarin, phenytoin, celecoxib | Dose adjustment may be required based on metabolizer status |
| **CYP3A4/5** | Tacrolimus, cyclosporine, statins | Affects first-pass metabolism and bioavailability |
| **DPYD** | Fluorouracil, capecitabine | Deficiency increases risk of severe/fatal toxicity |
| **TPMT** | Azathioprine, mercaptopurine | Deficiency requires significant dose reduction |
| **UGT1A1** | Irinotecan, atazanavir | Reduced glucuronidation affects drug clearance |
| **VKORC1** | Warfarin | Affects warfarin sensitivity and dosing |
| **SLCO1B1** | Simvastatin, rosuvastatin | Increased risk of myopathy |
| **HLA-B** | Abacavir, carbamazepine, allopurinol | Hypersensitivity reactions |

---

## Using the PGx Card

The PGx card in the [Analysis Hub](analysis-hub.md) provides a structured view of pharmacogenomic findings:

### Step 1: Open the PGx Card

1. Navigate to the Analysis Hub for your sample.
2. Select the **Pharmacogenomics** category (or any category containing the PGx card).
3. The PGx card loads automatically.

### Step 2: Review Drug-Variant Interactions

The card displays:

- **Variants found**: Pharmacogene variants detected in your sample.
- **Metabolizer phenotype**: Predicted metabolizer status based on the variant(s) (e.g., Poor Metabolizer, Normal Metabolizer).
- **Affected medications**: Drugs whose metabolism or efficacy is affected by the detected variants.
- **Clinical action**: Recommended prescribing modifications (dose adjustment, alternative drug, contraindication).

### Step 3: Review Prescribing Guidelines

For each drug-gene interaction, the card provides links to:

- **CPIC guidelines**: Clinical Pharmacogenetics Implementation Consortium recommendations.
- **PharmGKB annotations**: Detailed evidence summaries and clinical annotations.
- **FDA label information**: Pharmacogenomic biomarker information from FDA-approved drug labels.

---

## Metabolizer Phenotypes

AIVA predicts metabolizer phenotypes based on detected variants:

| Phenotype | Description | Clinical Implication |
|-----------|-------------|---------------------|
| **Ultra-Rapid Metabolizer** | Increased enzyme activity | May require higher doses; prodrug activation may be excessive |
| **Rapid Metabolizer** | Above-normal enzyme activity | Similar considerations as ultra-rapid, often less pronounced |
| **Normal Metabolizer** | Typical enzyme activity | Standard dosing expected to be effective |
| **Intermediate Metabolizer** | Reduced enzyme activity | May need dose reduction for some drugs |
| **Poor Metabolizer** | Minimal or absent enzyme activity | Significant dose reduction or alternative drug often required |

!!! warning "Clinical context required"
    Metabolizer phenotype predictions are based on known variant-phenotype associations. Additional factors (drug interactions, organ function, comorbidities) influence actual drug response and should be considered in prescribing decisions.

---

## PGx in AIVA Chat

You can also perform pharmacogenomic analysis through [AIVA Chat](../aiva-chat/index.md):

- "List all variants in pharmacogenes from my sample."
- "What is the CYP2D6 metabolizer status based on the variants in my data?"
- "What drugs should be prescribed with caution given the DPYD variants in this sample?"
- "Search for CPIC guidelines for CYP2C19 and clopidogrel."

AIVA uses the Genomic Data Query, Knowledge Graph, and Web Search tools to compile pharmacogenomic information.

---

## Evidence Levels

PharmGKB classifies drug-gene associations by evidence level:

| Level | Description |
|-------|-------------|
| **1A** | Annotation in a CPIC or other clinical guideline |
| **1B** | Annotation supported by strong clinical evidence |
| **2A** | Known pharmacogene with moderate clinical evidence |
| **2B** | Moderate clinical evidence for the association |
| **3** | Low-level evidence or in vitro data |
| **4** | Case reports or preliminary evidence |

AIVA displays the evidence level alongside each drug-gene interaction so you can assess the strength of the recommendation.

---

## Integrating PGx into Reports

Pharmacogenomic findings can be included in [clinical reports](../reports/index.md):

1. Flag relevant PGx variants using the [flagging system](../collaboration/variant-flagging.md).
2. Add prescribing notes as [comments](../collaboration/threaded-comments.md).
3. Use the **Pharmacogenomic Report** [template](../reports/templates.md) for structured PGx reporting.
4. [Link flagged variants](../reports/sample-linking.md) to the report.
5. Use [AI Auto-Fill](../reports/ai-auto-fill.md) to generate prescribing recommendation summaries.
