---
title: Knowledge Graph
description: Query AIVA's gene-protein-drug interaction network to explore biological pathways, drug targets, and protein interactions.
---

# Knowledge Graph

The Knowledge Graph tool queries a curated network of gene-protein-drug interactions. It enables pathway exploration, drug-target discovery, and protein interaction analysis directly within AIVA Chat.

---

## What Is in the Knowledge Graph?

The knowledge graph contains interconnected entities representing:

- **Genes** -- Human genes with identifiers, symbols, and functional annotations.
- **Proteins** -- Gene products with structural and functional information.
- **Drugs** -- Approved and investigational compounds with target information.
- **Interactions** -- Edges connecting genes to proteins, proteins to other proteins, and drugs to their molecular targets.
- **Pathways** -- Biological pathway memberships linking genes and proteins to known signaling and metabolic pathways.

---

## Capabilities

- **Drug-target lookups** -- Find which drugs target a specific gene or protein.
- **Protein interaction networks** -- Explore which proteins interact with a protein of interest.
- **Pathway analysis** -- Identify which biological pathways a gene or protein participates in.
- **Network traversal** -- Trace multi-hop relationships (e.g., from a gene to its protein product to interacting proteins to drugs targeting those proteins).
- **Drug repurposing candidates** -- Identify approved drugs that target proteins in the same pathway as your gene of interest.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Drug targets | "What drugs target the EGFR protein?" |
| Interaction network | "Show me the interaction network for TP53." |
| Compound queries | "Which proteins interact with BRCA1 and are targetable by approved drugs?" |
| Pathway tracing | "Trace the pathway from KRAS to downstream effectors." |
| Drug repurposing | "Are there any approved drugs that target proteins in the MAPK signaling pathway?" |
| Gene-drug relationships | "What is the relationship between the ALK gene and crizotinib?" |

---

## Understanding the Results

AIVA returns knowledge graph results as structured descriptions of the entities and relationships found. A typical response includes:

- **Entity details** -- Gene symbol, protein name, drug name, and identifiers.
- **Relationship types** -- "targets," "interacts with," "participates in," "encodes."
- **Path descriptions** -- For multi-hop queries, AIVA describes the chain of relationships connecting your query entities.

!!! note "Graph scope"
    The knowledge graph is curated from established databases and may not include every known interaction. For the most current or comprehensive interaction data, consider combining Knowledge Graph queries with [Web Search](web-search.md) or [Biomedical Literature](pubtator.md) lookups.

---

## Common Use Cases

### Identifying Therapeutic Options

When you find a pathogenic variant in a gene, use the Knowledge Graph to determine whether any drugs target that gene's protein product:

> "I found a pathogenic variant in BRAF. What drugs target BRAF, and are any of them FDA-approved?"

### Exploring Pathway Context

Understanding which pathway a gene belongs to can help interpret the functional impact of variants:

> "Which signaling pathways does PIK3CA participate in, and what other genes are in those pathways?"

### Connecting Variants to Drug Targets

For pharmacogenomic analysis, trace the connection between a mutated gene and potential drug interactions:

> "Show me the path from DPYD to fluorouracil metabolism."

---

## Combining with Other Tools

The Knowledge Graph is most powerful when combined with other AIVA tools:

- **Genomic Data Query + Knowledge Graph** -- Query your data for variants in a gene, then explore that gene's interaction network.
- **Knowledge Graph + Clinical Trials** -- Find drugs that target your gene of interest, then search for clinical trials testing those drugs.
- **Knowledge Graph + Biomedical Literature** -- Explore interactions in the graph, then find supporting literature for specific relationships.
- **Knowledge Graph + Code Interpreter** -- Retrieve interaction data, then visualize the network or compute network statistics.

See [Example Workflows](example-workflows.md) for multi-tool analysis patterns.
