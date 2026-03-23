---
title: Using AIVA MCP with Other Agents
description: Connect AIVA's genomic analysis tools to Claude Desktop, OpenAI Codex, Claude Code, Cursor, and other MCP-compatible AI agents.
---

# Using AIVA MCP with Other Agents

AIVA exposes a Model Context Protocol (MCP) server that allows MCP-compatible AI agents to access AIVA's genomic analysis tools directly. This means you can use AIVA's variant annotation, literature search, knowledge graph, and other tools from within your preferred AI assistant.

---

## MCP Endpoint

```
https://api.aivaportal.com/mcp/sse
```

The MCP server uses Server-Sent Events (SSE) transport for real-time communication. All requests require authentication with an AIVA API key. See [API Reference](../../api/index.md) for instructions on creating a key.

---

## Available Tools

Once connected, the following AIVA tools become available in your MCP client:

| Tool | Description |
|------|-------------|
| [Genomic Data Query](../ai-tools.md#genomic-data-query) | Query your uploaded variant data using SQL |
| [Web Search](../ai-tools.md#web-search) | Search the web for genomic and biomedical information |
| [Variant Annotation](../ai-tools.md#variant-annotation) | Annotate variants with ClinVar, gnomAD, SIFT, etc. |
| [Biomedical Literature](../ai-tools.md#biomedical-literature) | Search biomedical literature databases |
| [Code Interpreter](../ai-tools.md#code-interpreter) | Execute Python code for data analysis and visualization |
| [Knowledge Graph](../ai-tools.md#knowledge-graph) | Query the gene-protein-drug interaction network |
| [Clinical Trials](../ai-tools.md#clinical-trials) | Search clinical trials databases |
| [Phenotype-Gene Prioritization](../ai-tools.md#phenotype-gene-prioritization) | Phenotype-to-gene prioritization |

---

## Claude Desktop

Add the AIVA MCP server to your Claude Desktop configuration to use AIVA's tools directly in Claude conversations.

### Video walkthrough

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/yh-6yhTL8Yg?controls=1" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;" allowfullscreen title="Setting up AIVA MCP in Claude Desktop"></iframe>
</div>

### Configuration

Add the AIVA MCP server to the `mcpServers` section of your Claude Desktop configuration file:

| Platform | Path |
|----------|------|
| macOS | `~/Library/Application Support/Claude/claude_desktop_config.json` |
| Windows | `%APPDATA%\Claude\claude_desktop_config.json` |

```json
{
  "mcpServers": {
    "aiva": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://api.aivaportal.com/mcp/sse",
        "--header",
        "Authorization: Bearer <AIVA_API_KEY>"
      ]
    }
  }
}
```

Replace `<AIVA_API_KEY>` with your actual API key. Restart Claude Desktop after updating the configuration.

---

## OpenAI Codex

Connect AIVA's tools to OpenAI Codex for AI-assisted genomic analysis within your coding workflow.

### Video walkthrough

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/02f-t87MucY?controls=1" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;" allowfullscreen title="Setting up AIVA MCP in OpenAI Codex"></iframe>
</div>

---

## Other MCP-Compatible Clients

The AIVA MCP server works with any client that supports the MCP specification with SSE transport. Below are configuration patterns for popular tools.

### Claude Code

Add AIVA as an MCP server in your Claude Code configuration by typing `/mcp` and selecting "Add MCP Server".

### Cursor

In Cursor, navigate to **Settings > MCP** and add a new server with the AIVA endpoint URL and your API key.

### Windsurf

In Windsurf, add the AIVA MCP server through the MCP configuration panel using the same endpoint URL and authentication header.

---

## Troubleshooting

| Issue | Resolution |
|-------|------------|
| Connection fails | Verify your API key is valid. See [API Reference](../../api/index.md) for details. |
| Invalid JSON | Ensure the configuration JSON is valid (no trailing commas, correct quoting). |
| Tools not loading | Restart your AI agent after making configuration changes. |
| Authentication errors | API keys are case-sensitive. Copy the key exactly as shown at creation time. If expired or revoked, create a new one from **Settings > API Keys** in AIVA. |
