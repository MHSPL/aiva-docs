---
title: Analysis Cards
description: Detailed reference for AIVA's analysis cards including PGx, protein interactions, phenotype associations, and pathway analysis panels.
---

# Analysis Cards

Analysis cards are the building blocks of the [Analysis Hub](analysis-hub.md). Each card provides a focused analysis panel targeting a specific aspect of variant interpretation. Cards can be combined into [categories](categories.md) to create comprehensive analysis workspaces.

---

## Available Analysis Cards

### PGx Card (Pharmacogenomics)

The PGx card displays pharmacogenomic information for variants in drug-metabolizing genes.

**What it shows**:

- Drug-variant interaction summaries
- Metabolizer phenotype predictions (Poor, Intermediate, Normal, Rapid, Ultra-Rapid)
- Affected medications with prescribing implications
- PharmGKB evidence levels and clinical annotations
- CPIC guideline references

**When to use**: When your sample contains variants in pharmacogenes (CYP2D6, CYP2C19, CYP3A4, DPYD, TPMT, UGT1A1, and others) and you need to assess prescribing implications.

See [Pharmacogenomics](pharmacogenomics.md) for detailed documentation.

---

### Protein Interactions Card

The Protein Interactions card visualizes protein-protein interaction networks for genes of interest.

**What it shows**:

- Direct protein interaction partners
- Interaction confidence scores
- Known functional relationships (activation, inhibition, binding)
- Links to drug targets within the interaction network

**When to use**: When you want to understand the broader molecular context of a variant, including which proteins the affected gene product interacts with and whether those interactions have therapeutic relevance.

**How to use**:

1. Enter a gene symbol or select a gene from your variant data.
2. The card displays the interaction network with the query gene at the center.
3. Click on interacting proteins to see details.
4. Expand the network to include second-degree interactions if needed.

---

### Phenotype Associations Card

The Phenotype Associations card links genes to known clinical phenotypes using HPO terms and disease databases.

**What it shows**:

- HPO terms associated with the gene
- OMIM disease entries
- Inheritance patterns (autosomal dominant, autosomal recessive, X-linked, etc.)
- Phenotype-gene association evidence strength

**When to use**: When you want to determine whether a gene's known phenotypic associations match the patient's clinical presentation.

**How to use**:

1. Enter a gene symbol or select from your variant data.
2. Review the listed phenotypes and disease associations.
3. Compare against the patient's phenotype for concordance.
4. Use this information as supporting evidence for variant classification.

---

### Pathway Analysis Card

The Pathway Analysis card maps genes to known biological pathways and signaling cascades.

**What it shows**:

- Pathway memberships (e.g., MAPK signaling, DNA repair, cell cycle regulation)
- Other genes in the same pathway
- Pathway-level drug targets
- Downstream effectors and upstream regulators

**When to use**: When you want to understand the biological pathway context of a variant, identify other genes in the same pathway that may be affected, or find pathway-targeted therapies.

**How to use**:

1. Enter a gene symbol.
2. View the pathways the gene participates in.
3. Explore other genes in each pathway.
4. Check for pathway-targeted drugs.

---

### Conservation Analysis Card

The Conservation Analysis card shows evolutionary conservation data for variant positions.

**What it shows**:

- Cross-species conservation scores (PhyloP, PhastCons)
- Multiple sequence alignment at the variant position
- Conservation across vertebrates, mammals, and primates

**When to use**: When assessing whether a variant position is under evolutionary constraint, which supports functional importance.

---

### Gene Summary Card

The Gene Summary card provides a comprehensive overview of a gene.

**What it shows**:

- Gene function and description
- Genomic location and transcript information
- Associated diseases (OMIM, ClinVar)
- Expression patterns
- Known variants and their classifications

**When to use**: As a starting point when investigating an unfamiliar gene or reviewing a gene's overall clinical relevance.

---

## Working with Cards

### Adding Cards to a Category

1. Open the [category](categories.md) you want to modify.
2. Click **Add Card**.
3. Select the card from the card library.
4. The card appears in the category workspace.

### Configuring a Card

Most cards accept input parameters:

- **Gene symbol**: The primary gene to analyze.
- **Variant**: A specific variant for focused analysis.
- **Filters**: Narrow results by evidence level, data source, or other criteria.

### Interacting with Results

Card results are interactive:

- **Click on genes** to open their summary or navigate to them in the data table.
- **Click on drugs** to see prescribing information and clinical trial links.
- **Click on pathways** to expand pathway membership details.
- **Export** card results as tables or images.

### Linking to Flags and Comments

From any card, you can:

- [Flag a variant](../collaboration/variant-flagging.md) directly from the card's results.
- Add a [comment](../collaboration/threaded-comments.md) documenting your interpretation.
- Apply [ACMG criteria](acmg-classification.md) based on the evidence shown.

!!! tip "Multi-card analysis"
    Arrange several cards side by side in the [Analysis Hub](analysis-hub.md) to view protein interactions, pathway context, and phenotype associations simultaneously for a single gene.
