---
title: MCP Integration
description: Connect custom tool servers to AIVA using the Model Context Protocol (MCP) to extend the AI assistant with proprietary data sources and specialized analysis tools.
---

# MCP Integration

The Model Context Protocol (MCP) integration allows you to connect external tool servers to AIVA, extending its capabilities with your own data sources, APIs, and analysis pipelines. Once configured, MCP tools appear alongside AIVA's built-in tools and can be invoked automatically during conversations.

---

## What Is MCP?

The Model Context Protocol is an open standard for connecting AI assistants to external tools and data sources. An MCP server exposes one or more tools with defined inputs and outputs, and AIVA can invoke them just like its built-in tools.

Common use cases for MCP integration:

- **Internal databases** -- Connect AIVA to institutional variant databases, LIMS, or EHR systems.
- **Custom analysis pipelines** -- Expose bioinformatics pipelines or custom scoring algorithms as tools.
- **Proprietary knowledge bases** -- Make internal curated knowledge (e.g., institutional classification databases) available to AIVA.
- **Third-party APIs** -- Integrate external services not included in AIVA's default tool set.

---

## Configuring MCP Servers

### Step 1: Prepare Your MCP Server

Your MCP server must implement the Model Context Protocol specification. Each tool exposed by the server needs:

- A unique **tool name** and **description** that AIVA uses to decide when to invoke it.
- A defined **input schema** specifying the parameters the tool accepts.
- A defined **output format** for returning results to AIVA.

### Step 2: Add the Server in AIVA

1. Open the AIVA Chat interface.
2. Navigate to the tool configuration panel.
3. Select **MCP Servers** or **Custom Tools**.
4. Provide the server connection details:
    - **Server URL** -- The endpoint where your MCP server is running.
    - **Server name** -- A display name for the server.
    - **Authentication** (if required) -- API key or token for server access.
5. Save the configuration.

### Step 3: Verify the Connection

After adding the server, AIVA fetches the list of available tools from the server. You should see the new tools listed in the tool configuration panel alongside AIVA's built-in tools.

!!! note "Server availability"
    Your MCP server must be accessible from the AIVA backend. If running locally, ensure the server is reachable via the configured URL. For production deployments, the server should be hosted on infrastructure accessible to the AIVA platform.

---

## Using MCP Tools in Chat

Once configured, MCP tools work the same way as built-in tools:

- AIVA automatically selects MCP tools when your question matches the tool's description.
- You can see which MCP tool was invoked in the tool call indicator during the response.
- Results from MCP tools are displayed inline in the conversation.

You can also explicitly request an MCP tool by referencing it in your prompt:

> "Use my institutional database tool to look up the classification for this variant."

---

## Managing MCP Servers

### Enabling and Disabling

Toggle MCP tools on or off from the tool configuration panel, just like built-in tools. Disabling an MCP server prevents AIVA from invoking any of its tools.

### Editing Configuration

Update server URLs, names, or authentication credentials from the MCP Servers section in the tool configuration panel.

### Removing a Server

Delete an MCP server configuration to permanently remove its tools from AIVA. This does not affect the external server itself.

---

## Example: Institutional Variant Database

A common integration pattern is connecting AIVA to an institutional variant classification database:

1. **Build an MCP server** that exposes a `lookup_variant` tool accepting a variant identifier and returning the institution's classification, evidence summary, and last review date.
2. **Configure the server** in AIVA with the appropriate URL and credentials.
3. **Query in chat**: "Look up the institutional classification for BRCA1 c.5266dupC."
4. AIVA invokes the MCP tool and returns the institutional classification alongside its built-in ClinVar lookup.

---

## Security Considerations

!!! warning "Data flow awareness"
    When you configure an MCP server, AIVA sends tool invocation requests (including parameters derived from your conversation) to the external server. Ensure your MCP server is secured appropriately:

    - Use HTTPS for all connections.
    - Implement authentication and authorization.
    - Do not expose sensitive patient data through MCP tool parameters unless the server meets your organization's data handling requirements.
    - Review the tool descriptions and input schemas to understand what data is sent with each invocation.

---

## Troubleshooting

| Issue | Resolution |
|-------|------------|
| Tools not appearing | Verify the server URL is correct and the server is running. Check that the server implements the MCP specification correctly. |
| Connection errors | Ensure the server is accessible from the AIVA backend. Check firewall rules and network configuration. |
| Tool invocation failures | Review the server logs for error details. Verify that the input schema matches what AIVA is sending. |
| Unexpected results | Check the tool's output format. AIVA expects results in the standard MCP response format. |

For additional help, refer to the [API Reference](../api/index.md) or contact support.
