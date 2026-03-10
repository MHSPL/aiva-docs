---
title: AI Tools Reference
description: Comprehensive reference for all tools available to the AIVA AI assistant, including capabilities, example prompts, and usage guidance.
---

# AI Tools Reference

AIVA has access to a suite of specialized tools that it invokes automatically based on your questions. You do not need to specify which tool to use -- AIVA selects the appropriate tool (or combination of tools) based on the context of your query.

This page provides a detailed reference for each available tool.

---

## Genomic Data Query

The Genomic Data Query tool allows AIVA to query your uploaded variant data directly using SQL. AIVA translates your natural language questions into SQL queries, executes them against your data, and returns the results.

**Capabilities**:

- Query any column in your uploaded samples, including VCF fields, INFO subfields, and annotation columns.
- Aggregate data with counts, averages, grouping, and statistical summaries.
- Filter and sort results based on any combination of criteria.
- Access-controlled per user -- AIVA can only query data belonging to the current user's samples.
- Read-only -- AIVA cannot modify or delete your data.

**Example prompts**:

- "How many variants are in my sample?"
- "Show me all missense variants on chromosome 17 with gnomAD allele frequency below 0.01."
- "What are the top 10 most frequently mutated genes?"
- "Count the number of pathogenic vs. benign variants grouped by chromosome."

!!! note "Access control"
    AIVA can only access data from samples that belong to you or that have been shared with you through a [project](../collaboration/projects.md). It cannot access other users' data.

---

## Web Search

The Web Search tool uses Firecrawl to search the web and scrape pages for up-to-date genomic information. Use it when you need information beyond what is in your data or in the knowledge graph.

**Capabilities**:

- Search the web for gene summaries, disease associations, treatment guidelines, and recent research.
- Scrape and extract content from specific web pages.
- Retrieve current clinical guidelines and consortium recommendations.

**Example prompts**:

- "What does the latest ACMG guidance say about classifying VUS?"
- "Summarize the role of TP53 in Li-Fraumeni syndrome."
- "Find the most recent NCCN guidelines for hereditary breast cancer."

---

## Variant Annotation

The Variant Annotation tool performs real-time lookups for individual variants against curated genomic databases.

**Databases queried**:

| Database | Information Provided |
|----------|---------------------|
| **ClinVar** | Clinical significance classifications (Pathogenic, Likely Pathogenic, VUS, Likely Benign, Benign), review status, submitter information |
| **gnomAD** | Population allele frequencies across global populations and subpopulations |
| **CADD** | Combined Annotation Dependent Depletion scores for variant deleteriousness |
| **SIFT** | Prediction of whether an amino acid substitution affects protein function (Tolerated / Deleterious) |
| **PolyPhen-2** | Prediction of the impact of amino acid substitutions on protein structure and function (Benign / Possibly Damaging / Probably Damaging) |

**Example prompts**:

- "What is the ClinVar classification for BRCA1 c.5266dupC?"
- "Look up the gnomAD allele frequency for chr17:41245466 G>A."
- "Get CADD, SIFT, and PolyPhen scores for this variant: chr7:117559590 T>G."

!!! tip "Batch vs. real-time annotation"
    The Variant Annotation tool annotates individual variants in real time during a conversation. For batch annotation of entire VCF files, use [Variant Effect Prediction](../samples/vep-annotation.md) during upload instead.

---

## Biomedical Literature

The Biomedical Literature tool searches a biomedical literature database for published research, linking genes, diseases, chemicals, mutations, and species to peer-reviewed articles.

**Capabilities**:

- Search by gene name, disease, chemical compound, or specific mutation.
- Retrieve PubMed article titles, abstracts, and publication metadata.
- Identify co-occurring biomedical entities within articles.

**Example prompts**:

- "Find recent publications about BRCA2 and ovarian cancer."
- "What has been published about the drug olaparib in relation to homologous recombination deficiency?"
- "Search for papers mentioning the BRAF V600E mutation in melanoma."

---

## Code Interpreter

The Code Interpreter tool executes Python code in a sandboxed environment with access to common scientific libraries. It is useful for statistical analysis, custom calculations, and generating plots.

**Available libraries**:

- `pandas` -- Data manipulation and analysis
- `numpy` -- Numerical computing
- `scipy` -- Statistical tests and scientific computing
- `matplotlib` -- Chart and plot generation

**Capabilities**:

- Perform statistical tests (t-tests, chi-squared, Fisher's exact, etc.).
- Generate plots and visualizations (histograms, scatter plots, bar charts, box plots).
- Run custom data transformations and calculations.
- Process data fetched by other tools (e.g., query data with Genomic Data Query, then plot it with the Code Interpreter).

**Example prompts**:

- "Plot the allele frequency distribution for all variants in my sample."
- "Run a Fisher's exact test comparing the number of pathogenic variants on chromosome 13 vs. chromosome 17."
- "Create a bar chart showing the top 20 genes by variant count."

!!! info "Plots appear inline"
    Matplotlib charts generated by the Code Interpreter are rendered directly in the chat conversation as images. You can view and download them without leaving the chat.

---

## Knowledge Graph

The Knowledge Graph tool queries a curated graph database of gene-protein-drug interactions, enabling pathway and network analysis.

**Capabilities**:

- Explore gene-to-protein relationships.
- Find drug-target interactions for specific genes or proteins.
- Trace biological pathways and interaction networks.
- Identify potential drug repurposing candidates based on gene/protein targets.

**Example prompts**:

- "What drugs target the EGFR protein?"
- "Show me the interaction network for TP53."
- "Which proteins interact with BRCA1 and are targetable by approved drugs?"
- "Trace the pathway from KRAS to downstream effectors."

---

## Clinical Trials

The Clinical Trials tool searches ClinicalTrials.gov for active, completed, and recruiting trials relevant to your area of interest.

**Capabilities**:

- Search by condition, disease, gene, intervention, or drug name.
- Filter by trial status (recruiting, active, completed).
- Return trial titles, phases, sponsors, and registration numbers.

**Example prompts**:

- "Are there any active clinical trials for TP53-mutated breast cancer?"
- "Find recruiting trials for olaparib in ovarian cancer."
- "What phase 3 trials are studying PARP inhibitors?"

---

## Phenotype-Gene Prioritization

The Phenotype-Gene Prioritization tool maps clinical phenotype terms (HPO terms) to candidate genes, helping prioritize genes based on patient phenotypes.

**Capabilities**:

- Accept Human Phenotype Ontology (HPO) terms as input.
- Return ranked candidate genes with confidence scores.
- Support multiple phenotype terms for combinatorial analysis.

**Example prompts**:

- "Given the phenotypes intellectual disability and seizures, what are the top candidate genes?"
- "Map HPO terms HP:0001250 and HP:0001249 to candidate genes."
- "Which genes are associated with cardiomyopathy and short stature?"

---

## MCP -- Custom Tool Integration

The Model Context Protocol (MCP) integration allows you to connect your own external tools and servers to AIVA. This is an advanced feature for users who want to extend AIVA's capabilities with custom or proprietary data sources.

**Capabilities**:

- Connect to any MCP-compatible server.
- Expose custom tools that AIVA can invoke during conversations.
- Integrate proprietary databases, internal APIs, or specialized analysis pipelines.

!!! info "Configuration required"
    MCP tools must be configured by the user before they appear in AIVA's tool set. See the [API Reference](../api/index.md) for setup instructions.

---

## Task Manager

The Task Manager tool provides lightweight task tracking within a conversation. Use it to track action items, next steps, or analysis checkpoints.

**Capabilities**:

- Create, update, and complete tasks within a conversation.
- List outstanding tasks.
- Organize multi-step analysis workflows.

**Example prompts**:

- "Add a task: review all VUS variants on chromosome 6."
- "What tasks are still pending?"
- "Mark the BRCA1 review task as complete."

---

## Enabling and Disabling Tools

You can control which tools AIVA has access to for a given conversation:

1. Open the tool configuration panel in the chat interface.
2. Toggle individual tools on or off.
3. AIVA will only use the enabled tools when responding to your queries.

This is useful when you want to:

- **Restrict to local data only**: Disable Web Search, Biomedical Literature, and Clinical Trials to keep AIVA focused on your uploaded data.
- **Reduce latency**: Fewer available tools means AIVA spends less time evaluating which tool to use.
- **Focus analysis**: Enable only the specific tools relevant to your current task.

---

## Tool Combinations

AIVA can chain multiple tools in a single response. For example:

1. **Genomic Data Query** to fetch variant data from your sample.
2. **Variant Annotation** to look up ClinVar classifications for specific variants.
3. **Code Interpreter** to generate a visualization of the results.
4. **Biomedical Literature** to find supporting literature for the findings.

You do not need to prompt each tool separately. A single question like "Show me the rare pathogenic variants in my sample, look up their ClinVar entries, and plot the distribution by gene" can trigger all of these tools in sequence.
