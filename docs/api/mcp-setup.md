---
title: MCP Setup
description: Connect AIVA as an MCP server to Claude Desktop or other MCP-compatible clients for AI-powered genomic analysis.
---

# MCP Setup

AIVA exposes a Model Context Protocol (MCP) server that allows MCP-compatible clients such as Claude Desktop to access AIVA's genomic analysis tools directly.

---

## MCP Endpoint

```
https://api.aivaportal.com/mcp/sse
```

The MCP server uses Server-Sent Events (SSE) transport for real-time communication.

---

## Claude Desktop Configuration

To connect AIVA to Claude Desktop, add the following configuration to your Claude Desktop settings file.

### Configuration File Location

| Platform | Path |
|----------|------|
| macOS | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Windows | `%APPDATA%\Claude\claude_desktop_config.json` |

### Configuration

Add the AIVA MCP server to the `mcpServers` section of your configuration file:

```json
{
  "mcpServers": {
    "aiva": {
      "url": "https://api.aivaportal.com/mcp/sse",
      "headers": {
        "Authorization": "Bearer <AIVA_API_KEY>"
      }
    }
  }
}
```

Replace `<AIVA_API_KEY>` with your actual API key. See [API Keys](api-keys.md) for instructions on creating a key.

After updating the configuration, restart Claude Desktop for the changes to take effect.

---

## Available Tools

Once connected, the following AIVA tools become available in your MCP client:

| Tool | Description |
|------|-------------|
| `postgresql` | Query your uploaded variant data using SQL |
| `web_search` | Search the web for genomic and biomedical information |
| `variant_annotation` | Annotate variants with ClinVar, gnomAD, CADD, SIFT, PolyPhen |
| `pubtator` | Search biomedical literature databases |
| `python_repl` | Execute Python code for data analysis and visualization |
| `knowledge_graph` | Query the gene-protein-drug interaction network |
| `clinical_trials` | Search clinical trials databases |
| `phen2gene` | Phenotype-to-gene prioritization |

---

## Example Prompts

Once AIVA is connected as an MCP server, you can use prompts like these in Claude Desktop:

**Querying variant data:**

> "Query my patient_001_variants table and find all pathogenic variants in BRCA1 and BRCA2 genes."

**Variant annotation:**

> "Annotate the variant chr17:41245466 G>A and tell me about its clinical significance."

**Literature search:**

> "Search PubMed for recent publications about CFTR variants and cystic fibrosis treatment."

**Data analysis:**

> "Analyze the variant distribution by chromosome in my sample and create a bar chart."

**Knowledge graph:**

> "What drugs target the protein encoded by the EGFR gene?"

**Clinical trials:**

> "Find active clinical trials for BRCA1-positive breast cancer patients."

---

## Troubleshooting

### Connection Issues

- Verify your API key is valid by using the [health check endpoint](api-keys.md#health-check).
- Ensure the configuration JSON is valid (no trailing commas, correct quoting).
- Restart Claude Desktop after making configuration changes.

### Tool Access

- Tools are available based on your [subscription tier](../getting-started/subscription-tiers.md).
- Ensure you have at least one uploaded sample if you want to query variant data.

### Authentication Errors

- API keys are case-sensitive. Copy the key exactly as shown at creation time.
- If a key has expired or been revoked, create a new one from **Settings > API Keys** in the AIVA application.
