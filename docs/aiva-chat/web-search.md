---
title: Web Search
description: Use AIVA's Web Search tool to find the latest research, clinical guidelines, gene information, and disease associations from across the web.
---

# Web Search

The Web Search tool gives AIVA the ability to search the internet and extract content from web pages in real time. It retrieves up-to-date information that may not be present in your uploaded data or in AIVA's built-in knowledge bases.

---

## When to Use Web Search

Web Search is most valuable when you need:

- **Current guidelines**: ACMG, NCCN, or consortium recommendations that are updated periodically.
- **Gene and disease summaries**: Comprehensive overviews from OMIM, GeneReviews, or UniProt.
- **Recent publications or news**: Findings published after the training cutoff of the underlying language model.
- **Drug and therapy information**: FDA approvals, prescribing information, or mechanism-of-action details.
- **Variant interpretation context**: Published case reports or functional studies for specific variants.

!!! tip "Complement with Biomedical Literature"
    For structured biomedical literature searches (PubMed-indexed articles with entity annotations), use the [Biomedical Literature](biomedical-literature.md) tool. Web Search is better for general web content, guidelines hosted on organization websites, and non-PubMed sources.

---

## Capabilities

- **Full-text web search**: Search the open web for any topic and receive summarized results.
- **Page scraping**: Extract and parse the content of specific URLs, including tables and structured data.
- **Content summarization**: AIVA reads the retrieved content and distills it into a focused answer to your question.
- **Source attribution**: Results include the URLs of the pages consulted, so you can verify the information.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Retrieve clinical guidelines | "What does the latest ACMG guidance say about classifying VUS?" |
| Gene function summary | "Summarize the role of TP53 in Li-Fraumeni syndrome." |
| Treatment protocols | "Find the most recent NCCN guidelines for hereditary breast cancer." |
| Drug information | "What is the mechanism of action of olaparib?" |
| Variant context | "Search for published case reports of the BRCA2 c.5946delT variant." |
| Regulatory updates | "Has the FDA approved any new therapies for EGFR-mutated NSCLC in the last year?" |

---

## How It Works

1. You ask AIVA a question that requires external information.
2. AIVA formulates a search query based on your question.
3. The search engine queries the web and returns relevant pages.
4. AIVA reads and synthesizes the content from those pages.
5. The response includes a summary with source URLs.

---

## Controlling Web Search

You can enable or disable Web Search from the tool configuration panel in the chat interface. Disabling it restricts AIVA to your local data and built-in knowledge bases only.

!!! note "Data privacy"
    Web Search sends search queries to external services. The queries are derived from your question and do not include your uploaded variant data. If you are working with sensitive clinical data and want to ensure no information leaves the platform, disable Web Search.

---

## Combining with Other Tools

Web Search works well in combination with other AIVA tools:

- **Web Search + Genomic Data Query**: Find a gene's known disease associations on the web, then query your data for variants in that gene.
- **Web Search + Variant Annotation**: Look up published functional studies for a variant, then retrieve its ClinVar and gnomAD data.
- **Web Search + Code Interpreter**: Retrieve numerical data from a web source, then plot or analyze it with Python.

See [Example Workflows](example-workflows.md) for end-to-end analysis patterns.
