---
title: ACMG/AMP Guidelines
description: Reference guide for the ACMG/AMP variant classification framework including all evidence criteria and classification rules.
---

# ACMG/AMP Guidelines

This page provides a reference for the ACMG/AMP (American College of Medical Genetics and Genomics / Association for Molecular Pathology) framework for variant classification, as described in the 2015 Standards and Guidelines for the Interpretation of Sequence Variants (Richards et al., 2015).

---

## Overview

The ACMG/AMP framework provides a standardized approach to classifying sequence variants into five tiers based on accumulated evidence:

1. **Pathogenic**
2. **Likely Pathogenic**
3. **Uncertain Significance (VUS)**
4. **Likely Benign**
5. **Benign**

The framework defines 28 criteria (16 pathogenic, 12 benign) organized by evidence strength. Criteria are combined according to defined rules to arrive at a classification.

---

## Pathogenic Evidence Criteria

### Very Strong (PVS)

| Criterion | Description |
|-----------|-------------|
| **PVS1** | Null variant (nonsense, frameshift, canonical splice site, initiation codon, single/multi-exon deletion) in a gene where loss of function is a known mechanism of disease. Caution: consider whether the gene truly has a loss-of-function mechanism, and whether the variant actually results in loss of function (e.g., last exon truncations may escape nonsense-mediated decay). |

### Strong (PS)

| Criterion | Description |
|-----------|-------------|
| **PS1** | Same amino acid change as a previously established pathogenic variant, regardless of nucleotide change. |
| **PS2** | De novo (both maternity and paternity confirmed) in a patient with the disease and no family history. |
| **PS3** | Well-established in vitro or in vivo functional studies supportive of a damaging effect on the gene or gene product. |
| **PS4** | The prevalence of the variant in affected individuals is statistically increased compared with the prevalence in controls. |

### Moderate (PM)

| Criterion | Description |
|-----------|-------------|
| **PM1** | Located in a mutational hot spot and/or critical, well-established functional domain (e.g., active site of an enzyme) without benign variation. |
| **PM2** | Absent from controls (or at extremely low frequency if recessive) in population databases (gnomAD, ExAC). |
| **PM3** | For recessive disorders, detected in trans with a pathogenic variant. |
| **PM4** | Protein length changes due to in-frame deletions/insertions in a non-repeat region or stop-loss variants. |
| **PM5** | Novel missense change at an amino acid residue where a different missense change determined to be pathogenic has been seen before. |
| **PM6** | Assumed de novo, but without confirmation of paternity and maternity. |

### Supporting (PP)

| Criterion | Description |
|-----------|-------------|
| **PP1** | Co-segregation with disease in multiple affected family members in a gene definitively known to cause the disease. |
| **PP2** | Missense variant in a gene that has a low rate of benign missense variation and in which missense variants are a common mechanism of disease. |
| **PP3** | Multiple lines of computational evidence support a deleterious effect on the gene or gene product (CADD, SIFT, PolyPhen, conservation, etc.). |
| **PP4** | Patient's phenotype or family history is highly specific for a disease with a single genetic etiology. |
| **PP5** | Reputable source recently reports variant as pathogenic, but the evidence is not available to the laboratory to perform an independent evaluation. |

---

## Benign Evidence Criteria

### Stand-Alone (BA)

| Criterion | Description |
|-----------|-------------|
| **BA1** | Allele frequency is > 5% in gnomAD, ExAC, 1000 Genomes, or ESP. |

### Strong (BS)

| Criterion | Description |
|-----------|-------------|
| **BS1** | Allele frequency is greater than expected for the disorder. |
| **BS2** | Observed in a healthy adult individual for a recessive (homozygous), dominant (heterozygous), or X-linked (hemizygous) disorder, with full penetrance expected at an early age. |
| **BS3** | Well-established in vitro or in vivo functional studies show no damaging effect on protein function or splicing. |
| **BS4** | Lack of segregation in affected members of a family. |

### Supporting (BP)

| Criterion | Description |
|-----------|-------------|
| **BP1** | Missense variant in a gene for which primarily truncating variants are known to cause disease. |
| **BP2** | Observed in trans with a pathogenic variant for a fully penetrant dominant gene/disorder, or observed in cis with a pathogenic variant in any inheritance pattern. |
| **BP3** | In-frame deletions/insertions in a repetitive region without a known function. |
| **BP4** | Multiple lines of computational evidence suggest no impact on gene or gene product. |
| **BP5** | Variant found in a case with an alternate molecular basis for disease. |
| **BP6** | Reputable source recently reports variant as benign, but the evidence is not available to the laboratory to perform an independent evaluation. |
| **BP7** | A synonymous variant for which splicing prediction algorithms predict no impact to the splice consensus sequence, and the nucleotide is not highly conserved. |

---

## Combining Criteria

### Rules for Pathogenic Classification

| Classification | Required Criteria |
|---------------|-------------------|
| **Pathogenic** | (i) 1 Very Strong AND (>=1 Strong OR >=2 Moderate OR 1 Moderate + 1 Supporting OR >=2 Supporting) |
| | (ii) >=2 Strong |
| | (iii) 1 Strong AND (>=3 Moderate OR 2 Moderate + >=2 Supporting OR 1 Moderate + >=4 Supporting) |
| **Likely Pathogenic** | (i) 1 Very Strong AND 1 Moderate |
| | (ii) 1 Strong AND 1--2 Moderate |
| | (iii) 1 Strong AND >=2 Supporting |
| | (iv) >=3 Moderate |
| | (v) 2 Moderate AND >=2 Supporting |
| | (vi) 1 Moderate AND >=4 Supporting |

### Rules for Benign Classification

| Classification | Required Criteria |
|---------------|-------------------|
| **Benign** | (i) 1 Stand-Alone (BA1) OR (ii) >=2 Strong |
| **Likely Benign** | (i) 1 Strong AND 1 Supporting OR (ii) >=2 Supporting |

### Uncertain Significance

A variant is classified as VUS when:

- The criteria for a benign or pathogenic classification are not met.
- There is conflicting evidence (both pathogenic and benign criteria apply).

---

## Important Considerations

!!! note "Gene-specific guidelines"
    Several genes and gene groups have published modifications to the standard ACMG/AMP criteria (e.g., ACMG/AMP specifications for TP53, RASopathy genes, CDH1, PTEN, and others). When available, gene-specific guidelines should take precedence over the general framework.

!!! note "Criteria weighting"
    Some criteria may be adjusted in strength (e.g., a criterion normally rated as "Strong" may be downgraded to "Moderate" or upgraded based on the quality and quantity of evidence). The AIVA classifier allows standard strength levels; any adjustments should be documented in the interpretation notes.

---

## References

- Richards S, Aziz N, Bale S, et al. "Standards and guidelines for the interpretation of sequence variants: a joint consensus recommendation of the American College of Medical Genetics and Genomics and the Association for Molecular Pathology." *Genet Med*. 2015;17(5):405-424.
- ClinGen Sequence Variant Interpretation Working Group resources at [clinicalgenome.org](https://clinicalgenome.org).
