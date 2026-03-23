---
title: Glossary
description: Definitions of genomics, bioinformatics, and platform-specific terminology used throughout the AIVA documentation.
---

# Glossary

This glossary defines key terms used throughout the AIVA documentation. Terms are organized alphabetically.

---

## A

**ACMG (American College of Medical Genetics and Genomics)**
:   A professional organization that publishes standards and guidelines for clinical genetics, including the widely used framework for [variant classification](analysis/acmg-classification.md).

**ACMG/AMP Guidelines**
:   The 2015 joint consensus recommendation by ACMG and AMP providing a standardized framework for interpreting sequence variants. Variants are classified into five tiers: Pathogenic, Likely Pathogenic, Uncertain Significance (VUS), Likely Benign, and Benign.

**Allele**
:   One of two or more versions of a DNA sequence at a given genomic position. In a VCF file, the reference allele (REF) represents the sequence in the reference genome, and the alternate allele (ALT) represents the observed variant.

**Allele Frequency (AF)**
:   The proportion of a specific allele among all alleles at a given position in a population. Used to assess how common or rare a variant is.

**AMP (Association for Molecular Pathology)**
:   A professional organization that, together with ACMG, developed the standards and guidelines for sequence variant interpretation.

---

## B

**BAM (Binary Alignment Map)**
:   A binary format for storing sequence alignment data. Not directly uploaded to AIVA, but VCF files derived from BAM alignments are supported.

**Benign**
:   An ACMG classification indicating strong evidence that a variant does not cause disease.

**Biomedical Literature**
:   AIVA's literature search tool. Searches PubMed-indexed articles with entity-level annotations for genes, diseases, chemicals, mutations, and species. See [Biomedical Literature](aiva-chat/ai-tools.md#biomedical-literature).

---

## C

**ClinVar**
:   An NCBI database of reported relationships between human variants and phenotypes, including clinical significance classifications submitted by clinical laboratories and research groups.

**Code Interpreter**
:   AIVA's sandboxed Python execution tool, providing access to pandas, numpy, scipy, and matplotlib for statistical analysis, custom calculations, and data visualization within chat conversations. See [Code Interpreter](aiva-chat/ai-tools.md#code-interpreter).

**Consequence (Variant Consequence)**
:   The predicted functional effect of a variant on the gene product. Examples include missense_variant, synonymous_variant, frameshift_variant, stop_gained, and splice_donor_variant.

**CPIC (Clinical Pharmacogenetics Implementation Consortium)**
:   An organization that creates guidelines for using pharmacogenomic test results to guide drug prescribing decisions.

**CSV (Comma-Separated Values)**
:   A plain text file format using commas to separate values. AIVA supports [CSV file uploads](samples/vcf-upload.md).

---

## D

**De Novo Variant**
:   A variant present in an individual but not inherited from either parent. De novo status is a strong indicator of pathogenicity for certain disease types.

---

## E

**Exon**
:   A segment of a gene that is retained in the final mRNA after splicing. Variants in exons are more likely to affect protein function.

**Exome**
:   The portion of the genome that encodes proteins (approximately 1-2% of the total genome). Whole exome sequencing (WES) targets this region.

---

## F

**Frameshift Variant**
:   An insertion or deletion of nucleotides that is not a multiple of three, disrupting the reading frame of the gene and typically resulting in a truncated or nonfunctional protein.

---

## G

**Genomic Data Query**
:   AIVA's tool for querying uploaded variant data using natural language. AIVA translates questions into SQL queries and executes them against your sample data. See [AI Tools](aiva-chat/ai-tools.md#genomic-data-query).

**gnomAD (Genome Aggregation Database)**
:   A large-scale database of exome and genome sequencing data from over 140,000 individuals. Used to assess variant population frequencies. Variants common in gnomAD are less likely to cause rare disease.

**GRCh37 / GRCh38**
:   Human reference genome assemblies. GRCh37 (hg19) and GRCh38 (hg38) are the two commonly used versions. AIVA supports both for variant annotation.

---

## H

**HGVS (Human Genome Variation Society) Nomenclature**
:   A standardized system for describing variants in DNA, RNA, and protein sequences. Examples: c.5266dupC (coding DNA), p.Gln1756Profs*74 (protein).

**HPO (Human Phenotype Ontology)**
:   A standardized vocabulary for describing clinical phenotypes (observable characteristics) in human disease. Used by the [Phenotype-Gene Prioritization](aiva-chat/ai-tools.md#phenotype-gene-prioritization) tool for phenotype-to-gene mapping via a phenotype-gene mapping algorithm.

---

## I

**In Silico Prediction**
:   Computational prediction of a variant's functional impact using algorithms such as SIFT, PolyPhen-2, and CADD. In silico evidence is supporting (not standalone) evidence in ACMG classification.

**INFO Field**
:   A field in the VCF format containing additional information about each variant, such as allele frequency, depth of coverage, and annotation data.

---

## K

**Knowledge Graph**
:   AIVA's gene-protein-drug interaction network, built on a curated graph database. Enables pathway exploration, drug-target discovery, and protein interaction analysis. See [Knowledge Graph](aiva-chat/ai-tools.md#knowledge-graph).

---

## L

**Likely Benign**
:   An ACMG classification indicating moderate evidence that a variant does not cause disease.

**Likely Pathogenic**
:   An ACMG classification indicating sufficient evidence to support a disease-causing role for the variant.

**Loss of Function (LoF)**
:   A variant type that is predicted to result in the loss of normal protein function. Examples include nonsense variants, frameshift variants, and canonical splice site variants.

---

## M

**MCP (Model Context Protocol)**
:   An open standard for connecting AI assistants to external tools and data sources. AIVA supports [MCP integration](aiva-chat/mcp/index.md) for custom tool connections.

**Missense Variant**
:   A single nucleotide change that results in a different amino acid in the protein. Missense variants may or may not affect protein function.

---

## N

**Nonsense Variant**
:   A single nucleotide change that introduces a premature stop codon, typically resulting in a truncated and nonfunctional protein.

---

## O

**OMIM (Online Mendelian Inheritance in Man)**
:   A comprehensive database of human genes and genetic disorders, maintained by Johns Hopkins University.

---

## P

**Pathogenic**
:   An ACMG classification indicating strong evidence that a variant causes disease.

**Pharmacogenomics (PGx)**
:   The study of how genetic variants affect an individual's response to drugs.

**PharmGKB (Pharmacogenomics Knowledgebase)**
:   A database of pharmacogenomic information including drug-gene associations, clinical annotations, and prescribing guidelines.

**Phenotype-Gene Prioritization**
:   AIVA's tool for mapping clinical phenotypes (HPO terms) to ranked candidate genes using a phenotype-gene mapping algorithm. Assists in rare disease diagnosis and gene panel design. See [Phenotype-Gene Prioritization](aiva-chat/ai-tools.md#phenotype-gene-prioritization).

**PolyPhen-2 (Polymorphism Phenotyping v2)**
:   A computational tool that predicts the impact of amino acid substitutions on protein structure and function. Results are classified as Benign, Possibly Damaging, or Probably Damaging.

---

## R

**rsID**
:   A reference SNP identifier assigned by dbSNP (e.g., rs80357906). Used to uniquely identify known variants.

---

## S

**SIFT (Sorting Intolerant From Tolerant)**
:   A computational tool that predicts whether an amino acid substitution affects protein function based on sequence conservation. Scores below 0.05 are predicted to be deleterious.

**Small Variant Annotation**
:   AIVA's annotation feature for small variants (SNVs and indels) during file upload. Adds gene symbols, transcript information, SIFT/PolyPhen scores, population frequencies, and more. See [VCF Upload](samples/vcf-upload.md#annotation-options-vcf-only).

**SNV (Single Nucleotide Variant)**
:   A change in a single nucleotide at a specific position in the genome.

**SSE (Server-Sent Events)**
:   A web technology that enables a server to push real-time updates to a client over an HTTP connection. AIVA uses SSE for streaming chat responses and job status updates.

**Structural Variant (SV)**
:   A large-scale genomic alteration including deletions, duplications, inversions, and translocations, typically affecting 50 or more base pairs.

**Structural Variant Annotation**
:   AIVA's annotation feature for structural variants during upload. Adds clinical and functional annotations including gene overlap, population SV frequency, regulatory impact, and ACMG SV classification. See [VCF Upload](samples/vcf-upload.md#annotation-options-vcf-only).

---

## T

**Task Manager**
:   AIVA's in-conversation task tracking tool for managing action items, next steps, and analysis checkpoints. See [AI Tools](aiva-chat/ai-tools.md#task-manager).

**TSV (Tab-Separated Values)**
:   A plain text file format using tabs to separate values. AIVA supports [TSV file uploads](samples/vcf-upload.md).

---

## V

**VCF (Variant Call Format)**
:   The standard file format for storing variant data from genome sequencing. VCF files contain header lines (metadata) and data lines (one per variant) with fields for chromosome, position, reference allele, alternate allele, quality, filter status, and additional information. See [VCF Upload](samples/vcf-upload.md).

**VUS (Variant of Uncertain Significance)**
:   An ACMG classification indicating insufficient evidence to determine whether the variant is pathogenic or benign. VUS variants require additional evidence before clinical action.

---

## W

**WES (Whole Exome Sequencing)**
:   A sequencing approach that targets the protein-coding regions of the genome (the exome).

**WGS (Whole Genome Sequencing)**
:   A sequencing approach that determines the complete DNA sequence of an organism's genome.
