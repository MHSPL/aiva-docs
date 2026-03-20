---
title: Phenotype-Gene Prioritization
description: Map clinical phenotypes to candidate genes using HPO terms for rare disease diagnosis and gene prioritization in AIVA Chat.
---

# Phenotype-Gene Prioritization

The Phenotype-Gene Prioritization tool maps clinical phenotype descriptions to ranked candidate genes using a phenotype-gene mapping algorithm. By inputting Human Phenotype Ontology (HPO) terms or plain-language phenotype descriptions, you receive a prioritized list of genes most likely associated with the observed phenotypes, a powerful aid for rare disease diagnosis and gene panel prioritization.

---

## How It Works

This tool uses a knowledge base of gene-phenotype associations derived from HPO, OMIM, and other curated resources to rank genes by their relevance to a set of input phenotypes.

Key properties:

- **Input**: One or more HPO terms or clinical phenotype descriptions.
- **Output**: A ranked list of candidate genes with scores indicating the strength of association.
- **Speed**: Results are returned in seconds, making it suitable for interactive use in AIVA Chat.

---

## Capabilities

- **HPO term input**: Provide specific HPO identifiers (e.g., HP:0001250 for "Seizures").
- **Plain-language input**: Describe phenotypes in natural language; AIVA maps them to HPO terms.
- **Multiple phenotypes**: Combine several phenotype terms for more specific gene ranking.
- **Scored results**: Each candidate gene receives a score reflecting the strength of its phenotype match.
- **Gene details**: Results include gene symbols, scores, and associated conditions.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Single phenotype | "What genes are associated with seizures?" |
| Multiple phenotypes | "Given intellectual disability and seizures, what are the top candidate genes?" |
| HPO term input | "Map HPO terms HP:0001250 and HP:0001249 to candidate genes." |
| Clinical description | "Which genes are associated with cardiomyopathy and short stature?" |
| Rare disease workup | "A patient presents with microcephaly, epilepsy, and developmental delay. What are the candidate genes?" |
| Gene panel design | "I need to design a gene panel for a patient with retinitis pigmentosa and hearing loss. What genes should I include?" |

---

## Understanding the Results

The tool returns a ranked list of candidate genes:

| Field | Description |
|-------|-------------|
| **Rank** | Position in the ranked list (1 = strongest match) |
| **Gene** | Gene symbol |
| **Score** | Numerical score reflecting phenotype-gene association strength |
| **Associated Conditions** | Known diseases or syndromes linked to the gene |

Higher scores indicate stronger phenotype-gene associations. The top-ranked genes are the most likely candidates given the input phenotypes.

!!! tip "More phenotypes improve specificity"
    Providing multiple phenotype terms narrows the candidate gene list and increases the accuracy of the ranking. A single broad phenotype (e.g., "seizures") will return many candidates, while combining it with additional phenotypes (e.g., "seizures + microcephaly + hypotonia") produces a more focused result.

---

## Common Use Cases

### Rare Disease Diagnosis

When a patient presents with a combination of phenotypes, the Phenotype-Gene Prioritization tool helps prioritize which genes to investigate:

> "A 3-year-old presents with global developmental delay, hypotonia, and feeding difficulties. What are the top candidate genes?"

### Filtering Variant Data

After identifying candidate genes, use the Genomic Data Query tool to search your variant data for variants in those genes:

> "Find candidate genes for seizures and intellectual disability, then show me all variants in those genes from my sample."

### Gene Panel Validation

Verify that a gene panel covers the most relevant genes for a phenotype combination:

> "For a patient with hereditary spastic paraplegia and peripheral neuropathy, do the top candidate genes overlap with the genes in standard spastic paraplegia panels?"

---

## Combining with Other Tools

The Phenotype-Gene Prioritization tool is most effective as the starting point in a multi-tool workflow:

- **Phenotype-Gene Prioritization + Genomic Data Query**: Identify candidate genes, then search your variant data for variants in those genes.
- **Phenotype-Gene Prioritization + Variant Annotation**: Prioritize candidate genes, then look up ClinVar classifications for variants found in those genes.
- **Phenotype-Gene Prioritization + Biomedical Literature**: Get candidate genes, then search for supporting literature linking those genes to the patient's phenotype.
- **Phenotype-Gene Prioritization + Knowledge Graph**: Explore the protein interaction network for top candidate genes.

See [Example Workflows](example-workflows.md) for end-to-end analysis patterns.

---

## Limitations

- This tool relies on known gene-phenotype associations. Novel or poorly characterized gene-phenotype relationships may not be represented.
- Results are probabilistic rankings, not diagnostic conclusions. Clinical validation is required.
- The tool works best with specific HPO terms rather than vague descriptions.

!!! warning "Clinical interpretation required"
    Phenotype-Gene Prioritization results are intended to assist in gene prioritization. They do not constitute a diagnosis. All candidate genes should be evaluated in the context of the patient's full clinical picture by a qualified professional.
