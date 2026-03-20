---
title: Biomedical Literature
description: Search NCBI biomedical literature through AIVA Chat for gene, disease, chemical, and mutation-specific publication lookups.
---

# Biomedical Literature

The Biomedical Literature tool searches NCBI's biomedical literature database, a resource that provides entity-annotated access to PubMed articles. Use it to find publications related to specific genes, diseases, chemicals, mutations, or species.

---

## What It Does

The Biomedical Literature tool uses NCBI's entity annotation service, which automatically annotates PubMed abstracts and full-text articles with biomedical entities:

- **Genes**: Gene symbols and identifiers
- **Diseases**: Disease names and MeSH terms
- **Chemicals**: Drug names, compounds, and chemical identifiers
- **Mutations**: Specific variants and mutation types
- **Species**: Organism names

These annotations enable precise, entity-aware literature searches that go beyond simple keyword matching.

---

## Capabilities

- **Entity-based search**: Search by gene name, disease, chemical, or specific mutation with entity recognition.
- **Article retrieval**: Return PubMed article titles, abstracts, and publication metadata (authors, journal, year).
- **Entity co-occurrence**: Find articles that mention two or more entities together (e.g., a gene AND a disease).
- **Annotated results**: Returned abstracts include highlighted biomedical entities for quick scanning.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Gene-disease literature | "Find recent publications about BRCA2 and ovarian cancer." |
| Drug-mechanism research | "What has been published about olaparib in relation to homologous recombination deficiency?" |
| Mutation-specific papers | "Search for papers mentioning the BRAF V600E mutation in melanoma." |
| Gene function review | "Find review articles about the function of PTEN in cancer." |
| Chemical-gene interaction | "Search for publications linking metformin to AMPK activation." |
| Co-occurring entities | "Find papers that mention both TP53 and MDM2." |

---

## Understanding the Results

Results from the Biomedical Literature tool include:

| Field | Description |
|-------|-------------|
| **Title** | Article title |
| **Authors** | Author list |
| **Journal** | Publication venue |
| **Year** | Publication year |
| **PMID** | PubMed identifier for direct access |
| **Abstract** | Article abstract with annotated entities |
| **Entities** | Genes, diseases, chemicals, mutations, and species mentioned in the article |

AIVA summarizes the most relevant findings and provides PMIDs for further reading.

!!! tip "Access full articles"
    Use the PMID to look up the full article on PubMed: `pubmed.ncbi.nlm.nih.gov/PMID`. Many articles are available in full text through PubMed Central.

---

## Biomedical Literature vs. Web Search

| Feature | Biomedical Literature | Web Search |
|---------|----------------------|------------|
| **Source** | PubMed-indexed literature | Entire web |
| **Entity recognition** | Yes (genes, diseases, chemicals, mutations) | No |
| **Structured metadata** | Yes (PMID, authors, journal) | Limited |
| **Content type** | Peer-reviewed biomedical literature | Any web content |
| **Best for** | Finding published evidence for variant interpretation | Finding guidelines, news, non-journal sources |

Use the Biomedical Literature tool when you need peer-reviewed evidence. Use [Web Search](web-search.md) when you need broader web content.

---

## Common Use Cases

### Supporting Variant Classification

When classifying a variant using ACMG criteria, the Biomedical Literature tool helps find published functional studies and case reports:

> "Search for publications about the clinical significance of BRCA1 c.5266dupC."

### Literature Review for a Gene

Before interpreting variants in an unfamiliar gene, review the existing literature:

> "Find the most cited papers about the role of MLH1 in Lynch syndrome."

### Drug-Gene Evidence

When exploring pharmacogenomic implications, find published evidence for drug-gene interactions:

> "What has been published about CYP2D6 and tamoxifen metabolism?"

---

## Combining with Other Tools

The Biomedical Literature tool pairs naturally with other AIVA tools:

- **Variant Annotation + Biomedical Literature**: Look up a variant's ClinVar classification, then find supporting literature.
- **Knowledge Graph + Biomedical Literature**: Explore a gene's interaction network, then find publications for specific interactions.
- **Genomic Data Query + Biomedical Literature**: Identify genes with the most variants in your sample, then search for literature on each.
- **Clinical Trials + Biomedical Literature**: Find published results from completed clinical trials.

See [Example Workflows](example-workflows.md) for multi-tool analysis patterns.
