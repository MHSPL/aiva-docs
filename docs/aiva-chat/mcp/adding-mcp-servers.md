---
title: Adding MCP Servers to AIVA
description: Connect external MCP tool servers to AIVA Chat to extend the AI assistant with custom data sources, APIs, and analysis pipelines.
---

# Adding MCP Servers to AIVA

AIVA allows you to connect external Model Context Protocol (MCP) servers, extending the AI assistant with your own data sources, APIs, and analysis pipelines. Once configured, MCP tools appear alongside AIVA's built-in tools and can be invoked automatically during conversations.

---

## Video Walkthrough

<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden;">
  <iframe src="https://www.youtube.com/embed/ajosJtwLMpc?controls=1" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: 0;" allowfullscreen title="Adding MCP Servers to AIVA"></iframe>
</div>

---

## Common Use Cases

- **Internal databases**: Connect AIVA to institutional variant databases, LIMS, or EHR systems.
- **Custom analysis pipelines**: Expose bioinformatics pipelines or custom scoring algorithms as tools.
- **Proprietary knowledge bases**: Make internal curated knowledge (e.g., institutional classification databases) available to AIVA.
- **Third-party APIs**: Integrate external services not included in AIVA's default tool set (e.g., OpenTargets, OpenCRAVAT).

---

## Configuring MCP Servers

Open the **MCP Server Configuration** dialog from the chat interface. The dialog has two tabs: **JSON Configuration** and **Tool Management**.

### JSON Configuration

The **JSON Configuration** tab is where you add MCP server connections.

**Quick Add presets**: Click a preset button (e.g., **OpenCRAVAT**, **OpenTargets**) to instantly populate the JSON configuration for popular genomic MCP servers.

**Custom servers**: Enter MCP server configuration directly in the JSON editor. The format follows the standard MCP configuration schema:

```json
{
  "mcpServers": {
    "opentargets": {
      "transport": "http",
      "url": "https://mcp.platform.opentargets.org/mcp"
    }
  }
}
```

After entering the configuration:

1. Click **Test Connection** to verify that AIVA can reach the server.
2. A success banner confirms the connection: "Connection tests complete! Click 'Select Tools' below to configure which tools to enable."
3. Click **Select Tools** to switch to the Tool Management tab and choose which tools to activate.

### Tool Management

The **Tool Management** tab lets you select which tools from your MCP servers the AI agent can access.

- **Tool limit**: You can enable up to **10 MCP tools** at a time across all configured servers.
- **Per-server listing**: Tools are grouped by server. Each server shows the number of available tools.
- **Select All / Deselect All**: Quickly enable or disable all tools from a specific server.
- **Individual toggle**: Enable or disable specific tools by clicking their checkboxes.

After selecting your tools, click **Save Selection** to apply the changes.

---

## Using MCP Tools in Chat

Once configured, MCP tools work the same way as built-in tools:

- AIVA automatically selects MCP tools when your question matches the tool's description.
- You can see which MCP tool was invoked in the tool call indicator during the response.
- Results from MCP tools are displayed inline in the conversation.

You can also explicitly request an MCP tool by referencing it in your prompt:

> "Use the OpenTargets tool to search for drug targets for EGFR."

---

## Managing MCP Servers

### Editing configuration

Update server URLs or add new servers from the **JSON Configuration** tab in the MCP Server Configuration dialog.

### Removing a server

Delete a server's entry from the JSON configuration and click **Save Selection**. This removes its tools from AIVA but does not affect the external server.

### Clearing all servers

Click **Clear All** in the MCP Server Configuration dialog to remove all configured servers at once.

---

## Security Considerations

!!! warning "Third-party tool disclaimer"
    MCP servers are third-party tools and may not be HIPAA compliant. Use at your own risk. When you configure an MCP server, AIVA sends tool invocation requests (including parameters derived from your conversation) to the external server.

    - Use HTTPS for all connections.
    - Review the tool descriptions and input schemas to understand what data is sent with each invocation.
    - Do not expose sensitive patient data through MCP tool parameters unless the server meets your organization's data handling requirements.

---

## Troubleshooting

| Issue | Resolution |
|-------|------------|
| Tools not appearing | Verify the server URL is correct and the server is running. Click **Test Connection** to diagnose. |
| Connection test fails | Ensure the MCP server is accessible from your network. Check firewall rules and CORS configuration. |
| Tool invocation failures | Review the server logs for error details. Verify that the input schema matches what AIVA sends. |
| Tool limit reached | You can enable up to 10 MCP tools. Disable unused tools to make room for new ones. |
| Unexpected results | Check the tool's output format. AIVA expects results in the standard MCP response format. |
