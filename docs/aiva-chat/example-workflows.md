---
title: Example Workflows
description: End-to-end analysis recipes showing how to combine multiple AIVA Chat tools for common genomic analysis scenarios.
---

# Example Workflows

This page provides step-by-step workflows demonstrating how to combine AIVA's tools for common genomic analysis tasks. Each workflow shows a sequence of prompts and explains which tools AIVA invokes at each step.

---

## Workflow 1: Variant Interpretation for a Candidate Gene

**Scenario**: You have uploaded a VCF file and want to thoroughly interpret variants in a specific gene.

### Steps

1. **Identify variants in the gene**

    > "Show me all variants in BRCA1 from my sample, including their consequence and allele frequency."

    *Tools used*: Genomic Data Query

2. **Annotate variants of interest**

    > "Look up the ClinVar classification and gnomAD frequency for each pathogenic or VUS variant you found."

    *Tools used*: Variant Annotation

3. **Check in silico predictions**

    > "Get CADD, SIFT, and PolyPhen scores for the VUS variants."

    *Tools used*: Variant Annotation

4. **Search for literature evidence**

    > "Search for publications about each of these BRCA1 variants."

    *Tools used*: Biomedical Literature

5. **Find clinical trials**

    > "Are there any recruiting clinical trials for BRCA1-mutated breast cancer?"

    *Tools used*: Clinical Trials

6. **Summarize findings**

    > "Summarize the evidence for each variant including classification, population frequency, in silico predictions, and literature support."

    *Tools used*: None (synthesis from previous results)

---

## Workflow 2: Rare Disease Gene Prioritization

**Scenario**: A patient presents with a combination of clinical phenotypes, and you want to identify candidate genes and check your variant data.

### Steps

1. **Map phenotypes to candidate genes**

    > "A patient presents with microcephaly, seizures, and global developmental delay. What are the top 20 candidate genes?"

    *Tools used*: Phenotype-Gene Prioritization

2. **Search for variants in candidate genes**

    > "Check my sample for any variants in the top 10 candidate genes from the phenotype-gene prioritization results."

    *Tools used*: Genomic Data Query

3. **Annotate the found variants**

    > "For any variants found, look up their ClinVar classifications and gnomAD frequencies."

    *Tools used*: Variant Annotation

4. **Review the literature**

    > "Search for publications linking the genes with variants to microcephaly and seizures."

    *Tools used*: Biomedical Literature

5. **Visualize the results**

    > "Create a bar chart showing the prioritization scores for the top 10 candidate genes, highlighting which ones had variants in my sample."

    *Tools used*: Code Interpreter

---

## Workflow 3: Pharmacogenomic Analysis

**Scenario**: You want to identify variants with pharmacogenomic implications and explore drug-gene interactions.

### Steps

1. **Identify pharmacogenes in your data**

    > "List all variants in known pharmacogenes (CYP2D6, CYP2C19, CYP3A4, DPYD, TPMT, UGT1A1) from my sample."

    *Tools used*: Genomic Data Query

2. **Explore drug-gene interactions**

    > "For each gene with variants, what drugs are affected? Use the knowledge graph."

    *Tools used*: Knowledge Graph

3. **Check clinical significance**

    > "Look up the ClinVar and PharmGKB annotations for these pharmacogenomic variants."

    *Tools used*: Variant Annotation, Web Search

4. **Find prescribing guidelines**

    > "Search for CPIC guidelines related to CYP2D6 and tamoxifen."

    *Tools used*: Web Search

5. **Summarize actionable findings**

    > "Create a summary table of all actionable pharmacogenomic findings, including the gene, variant, affected drugs, and recommended actions."

    *Tools used*: Code Interpreter

---

## Workflow 4: Sample Overview and Quality Assessment

**Scenario**: You have just uploaded a new sample and want to understand its contents before detailed analysis.

### Steps

1. **Get basic statistics**

    > "How many variants are in my sample? Break them down by chromosome, variant type, and consequence."

    *Tools used*: Genomic Data Query

2. **Visualize the distribution**

    > "Plot the variant count by chromosome as a bar chart, and create a pie chart of variant consequences."

    *Tools used*: Genomic Data Query, Code Interpreter

3. **Assess quality metrics**

    > "What is the distribution of quality scores? Show me a histogram and the summary statistics."

    *Tools used*: Genomic Data Query, Code Interpreter

4. **Identify high-impact variants**

    > "How many variants are classified as high impact? List the top 10 by CADD score."

    *Tools used*: Genomic Data Query

5. **Check known pathogenic variants**

    > "Are there any variants already classified as pathogenic or likely pathogenic in ClinVar?"

    *Tools used*: Genomic Data Query (if Small Variant Annotation was applied) or Variant Annotation

---

## Workflow 5: Gene Network Exploration

**Scenario**: You found a variant in a gene and want to understand its biological context through interaction networks.

### Steps

1. **Explore the gene's network**

    > "Show me the protein interaction network for EGFR."

    *Tools used*: Knowledge Graph

2. **Identify drug targets in the network**

    > "Which proteins in the EGFR network are targetable by approved drugs?"

    *Tools used*: Knowledge Graph

3. **Find pathway context**

    > "What signaling pathways does EGFR participate in?"

    *Tools used*: Knowledge Graph

4. **Search for variants in network genes**

    > "Check my sample for variants in any of the genes from the EGFR interaction network."

    *Tools used*: Genomic Data Query

5. **Find supporting literature**

    > "Search for recent publications about EGFR pathway mutations in lung cancer."

    *Tools used*: Biomedical Literature, Web Search

6. **Find clinical trials**

    > "What recruiting clinical trials are testing EGFR-targeted therapies?"

    *Tools used*: Clinical Trials

---

## Workflow 6: Statistical Comparison Across Samples

**Scenario**: You have multiple samples in a project and want to compare variant profiles.

### Steps

1. **Count variants per sample**

    > "How many variants does each sample in my project have? Show me a comparison table."

    *Tools used*: Genomic Data Query

2. **Compare consequence distributions**

    > "Compare the distribution of variant consequences across all samples in a stacked bar chart."

    *Tools used*: Genomic Data Query, Code Interpreter

3. **Find shared variants**

    > "Which variants appear in all samples? List them with their genes and consequences."

    *Tools used*: Genomic Data Query

4. **Statistical comparison**

    > "Is there a statistically significant difference in the number of missense variants between sample A and sample B? Run a Fisher's exact test."

    *Tools used*: Genomic Data Query, Code Interpreter

---

## Tips for Building Your Own Workflows

- **Start broad, then narrow**: Begin with overview queries, then drill into specific variants or genes.
- **Let AIVA chain tools**: You can ask compound questions and AIVA will use multiple tools in sequence.
- **Save important findings**: [Flag variants](../collaboration/variant-flagging.md) and add [comments](../collaboration/threaded-comments.md) as you go.
- **Use playbooks**: For recurring workflows, create a [Playbook](../playbooks/index.md) that guides AIVA through the steps automatically.
- **Export results**: Use the [export features](../collaboration/exporting-flags-comments.md) to save your analysis for reports or downstream use.
