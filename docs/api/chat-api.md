---
title: Chat API
description: API reference for interacting with the AIVA AI assistant programmatically using streaming Server-Sent Events (SSE).
---

# Chat API

The Chat API provides programmatic access to the AIVA AI assistant. Send messages and receive streaming responses with tool invocations and formatted results.

---

## Send a Message

### Request

```
POST /agents/chat/stream
Content-Type: multipart/form-data
```

The chat endpoint accepts `multipart/form-data` to support optional file attachments alongside message parameters.

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message` | string | Yes | The user message to send to AIVA |
| `conversation_id` | string | No | Continue an existing conversation. Omit to start a new one. |
| `model` | string | No | The LLM model to use. See [Available Models](#available-models). |
| `file` | file | No | File attachment to include with the message |
| `available_tables` | JSON string | No | JSON array of table names the AI can query |
| `selected_tools` | JSON string | No | JSON array of tool names to enable for this request |
| `use_mcp` | boolean | No | Enable MCP tools for this request. Default: `false` |

### Available Models

| Model ID | Provider | Description |
|----------|----------|-------------|
| `openai/gpt-5.2` | OpenAI | GPT-5.2 |
| `google/gemini-3-pro-preview` | Google | Gemini 3 Pro Preview |
| `anthropic/claude-sonnet-4-5` | Anthropic | Claude Sonnet 4.5 |
| `anthropic/claude-opus-4-6` | Anthropic | Claude Opus 4.6 |
| `z-ai/glm-5` | Z-AI | GLM-5 |
| `moonshotai/kimi-k2.5` | Moonshot AI | Kimi K2.5 |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/agents/chat/stream \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "message=How many pathogenic variants are in my sample?" \
      -F "conversation_id=conv_abc123" \
      -F "model=openai/gpt-5.2" \
      -F 'available_tables=["patient_001_variants"]' \
      -F 'selected_tools=["postgresql","variant_annotation"]'
    ```

=== "Python"

    ```python
    import requests
    import json

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    data = {
        "message": "How many pathogenic variants are in my sample?",
        "conversation_id": "conv_abc123",
        "model": "openai/gpt-5.2",
        "available_tables": json.dumps(["patient_001_variants"]),
        "selected_tools": json.dumps(["postgresql", "variant_annotation"]),
    }

    response = requests.post(
        "https://api.aivaportal.com/agents/chat/stream",
        headers=headers,
        data=data,
        stream=True,
    )

    for line in response.iter_lines():
        if line:
            decoded = line.decode("utf-8")
            print(decoded)
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("message", "How many pathogenic variants are in my sample?");
    formData.append("conversation_id", "conv_abc123");
    formData.append("model", "openai/gpt-5.2");
    formData.append("available_tables", JSON.stringify(["patient_001_variants"]));
    formData.append("selected_tools", JSON.stringify(["postgresql", "variant_annotation"]));

    const response = await fetch("https://api.aivaportal.com/agents/chat/stream", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });

    const reader = response.body.getReader();
    const decoder = new TextDecoder();

    while (true) {
      const { done, value } = await reader.read();
      if (done) break;
      console.log(decoder.decode(value));
    }
    ```

---

## SSE Event Types

The response is streamed as Server-Sent Events (`Content-Type: text/event-stream`). Events are delivered as the AI generates its response.

| Event | Description |
|-------|-------------|
| `connection` | Connection established. Confirms the stream is open. |
| `session` | Session information including the conversation ID. |
| `text_delta` | A chunk of text from the AI's response. Concatenate all deltas for the full message. |
| `tool_call` | The AI is invoking a tool. Includes the tool name and input parameters. |
| `tool_result` | The result of a tool invocation. |
| `complete` | The response is complete. |
| `error` | An error occurred during processing. |

### Event Stream Example

```
event: connection
data: {"status": "connected"}

event: session
data: {"conversation_id": "conv_abc123"}

event: text_delta
data: {"delta": "Let me query your "}

event: text_delta
data: {"delta": "sample data to find pathogenic variants..."}

event: tool_call
data: {"tool": "postgresql", "input": "SELECT COUNT(*) FROM patient_001_variants WHERE clinvar_significance = 'Pathogenic'"}

event: tool_result
data: {"tool": "postgresql", "result": {"rows": [{"count": 42}]}}

event: text_delta
data: {"delta": "Your sample contains **42** pathogenic variants."}

event: complete
data: {"status": "done"}
```

---

## Consuming SSE Responses

### Python with Event Parsing

```python
import requests

headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

data = {
    "message": "Summarize the variant distribution by chromosome.",
    "available_tables": '["patient_001_variants"]',
}

response = requests.post(
    "https://api.aivaportal.com/agents/chat/stream",
    headers=headers,
    data=data,
    stream=True,
)

full_text = ""
for line in response.iter_lines():
    if line:
        decoded = line.decode("utf-8")
        if decoded.startswith("event: "):
            event_type = decoded[7:]
        elif decoded.startswith("data: "):
            import json
            payload = json.loads(decoded[6:])

            if event_type == "text_delta":
                full_text += payload.get("delta", "")
            elif event_type == "tool_call":
                print(f"Tool: {payload['tool']}")
            elif event_type == "tool_result":
                print(f"Result: {payload['result']}")
            elif event_type == "complete":
                print(f"\nFull response:\n{full_text}")
```

### JavaScript with EventSource

```javascript
// Note: EventSource only supports GET requests.
// For POST requests, use fetch with ReadableStream as shown in the examples above.

const formData = new FormData();
formData.append("message", "List the top 10 genes with the most variants.");
formData.append("available_tables", JSON.stringify(["patient_001_variants"]));

const response = await fetch("https://api.aivaportal.com/agents/chat/stream", {
  method: "POST",
  headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
  body: formData,
});

const reader = response.body.getReader();
const decoder = new TextDecoder();
let fullText = "";

while (true) {
  const { done, value } = await reader.read();
  if (done) break;

  const chunk = decoder.decode(value, { stream: true });
  const lines = chunk.split("\n");

  for (const line of lines) {
    if (line.startsWith("data: ")) {
      try {
        const payload = JSON.parse(line.slice(6));
        if (payload.delta) {
          fullText += payload.delta;
        }
      } catch (e) {
        // Skip non-JSON lines
      }
    }
  }
}

console.log("Full response:", fullText);
```

---

## File Attachments

You can attach a file to your message for the AI to analyze:

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/agents/chat/stream \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "message=Analyze this VCF file and summarize the findings." \
      -F "file=@sample.vcf" \
      -F "model=anthropic/claude-sonnet-4-5"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    files = {"file": open("sample.vcf", "rb")}
    data = {
        "message": "Analyze this VCF file and summarize the findings.",
        "model": "anthropic/claude-sonnet-4-5",
    }

    response = requests.post(
        "https://api.aivaportal.com/agents/chat/stream",
        headers=headers,
        files=files,
        data=data,
        stream=True,
    )

    for line in response.iter_lines():
        if line:
            print(line.decode("utf-8"))
    ```

---

## Tool Selection

Control which tools AIVA can use for a specific request by specifying the `selected_tools` parameter:

```json
["postgresql", "variant_annotation", "web_search"]
```

**Available tool names:**

| Tool | Description |
|------|-------------|
| `postgresql` | Query your uploaded variant data |
| `web_search` | Search the web for genomic information |
| `variant_annotation` | Annotate variants with ClinVar, gnomAD, CADD, SIFT, PolyPhen |
| `pubtator` | Search biomedical literature databases |
| `python_repl` | Execute Python code for data analysis |
| `knowledge_graph` | Query gene-protein-drug interaction network |
| `clinical_trials` | Search clinical trials databases |
| `phen2gene` | Phenotype-to-gene prioritization |
| `todo` | Task tracking and management |

Omit the `selected_tools` parameter to enable all tools.

!!! note "MCP tools"
    Set `use_mcp=true` to enable MCP tools configured in your account. See [MCP Setup](mcp-setup.md) for configuration details.
