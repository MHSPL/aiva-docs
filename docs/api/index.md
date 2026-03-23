---
title: API Reference
description: Comprehensive reference for the AIVA REST API, covering authentication, file uploads, variant calling, chat, database management, classification, export, and MCP integration.
---

# API Reference

The AIVA API provides programmatic access to the platform's core features. Use it to automate file uploads, run variant calling pipelines, interact with the AI assistant, manage databases, classify variants, export annotations, and integrate with MCP-compatible clients.

---

## Base URL

All API endpoints are relative to:

```
https://api.aivaportal.com
```

---

## Authentication

All API requests require authentication using an API key. Include your API key in the `Authorization` header:

```
Authorization: Bearer <AIVA_API_KEY>
```

See [API Keys](api-keys.md) for instructions on creating and managing API keys.

---

## Endpoint Summary

| Endpoint | Method | Path | Description |
|----------|--------|------|-------------|
| [Health Check](api-keys.md#health-check) | `GET` | `/health` | Test API connection and verify key validity |
| [FASTQ Upload](upload-endpoints.md#fastq-file-upload) | `POST` | `/jobs/upload/parabricks` | Upload FASTQ files for variant calling |
| [FASTQ Cloud Upload](upload-endpoints.md#fastq-cloud-url-upload) | `POST` | `/jobs/upload/parabricks` | Upload FASTQ from cloud URLs |
| [VCF Direct Upload](upload-endpoints.md#vcf-direct-file-upload) | `POST` | `/jobs/upload` | Upload VCF/CSV/TSV files directly |
| [VCF Cloud Upload](upload-endpoints.md#vcf-direct-cloud-upload) | `POST` | `/jobs/upload/from-cloud-url` | Import VCF from cloud URL |
| [VCF Annotated Upload](upload-endpoints.md#vcf-small-variant-annotation-file-upload) | `POST` | `/jobs/upload` | Upload VCF with Small Variant Annotation |
| [VCF Annotated Cloud Upload](upload-endpoints.md#vcf-small-variant-annotation-cloud-upload) | `POST` | `/jobs/upload/from-cloud-url` | Import VCF from cloud with Small Variant Annotation |
| [VCF SV Annotation Upload](upload-endpoints.md#vcf-structural-variant-annotation-file-upload) | `POST` | `/jobs/upload` | Upload VCF with Structural Variant Annotation |
| [VCF SV Annotation Cloud Upload](upload-endpoints.md#vcf-structural-variant-annotation-cloud-upload) | `POST` | `/jobs/upload/from-cloud-url` | Import VCF from cloud with Structural Variant Annotation |
| [Job Events (SSE)](job-monitoring.md#sse-real-time-events) | `GET` | `/jobs/events?token=<API_KEY>` | Real-time job status via SSE |
| [Job Status](job-monitoring.md#poll-job-status) | `GET` | `/jobs/{job_id}/status` | Poll individual job status |
| [List Jobs](job-monitoring.md#list-jobs) | `GET` | `/jobs` | List all jobs |
| [Cancel Job](job-monitoring.md#cancel-a-job) | `POST` | `/jobs/{job_id}/cancel` | Cancel a running job |
| [Delete Job](job-monitoring.md#delete-a-job) | `DELETE` | `/jobs/{job_id}` | Delete a job |
| [AI Chat](chat-api.md) | `POST` | `/agents/chat/stream` | Stream AI chat responses |
| [Classify Variant](classification-api.md) | `POST` | `/api/analyze/classify-variant` | ACMG/AMP variant classification |
| [List Tables](database-queries.md#list-tables) | `GET` | `/tables` | List uploaded data tables |
| [Get Table Data](database-queries.md#get-table-data) | `GET` | `/tables/{table_name}/data/all` | Retrieve table data |
| [Delete Table](database-queries.md#delete-a-table) | `DELETE` | `/tables/{table_name}` | Delete a table |
| [Export Flags](export-api.md#export-flags) | `GET` | `/api/variant-flags/export` | Export variant flags |
| [Export Comments](export-api.md#export-comments) | `GET` | `/api/variant-comments/export` | Export variant comments |
| [MCP SSE](mcp-setup.md) | `GET` | `/mcp/sse` | MCP integration endpoint |

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### API Keys

Create, manage, and revoke API keys. Verify connectivity with the health check endpoint.

[:octicons-arrow-right-24: API Keys](api-keys.md)

</div>

<div class="card" markdown>

### Upload Endpoints

Upload FASTQ, VCF, CSV, and TSV files directly or via cloud URLs, with optional Small Variant Annotation or Structural Variant Annotation.

[:octicons-arrow-right-24: Upload Endpoints](upload-endpoints.md)

</div>

<div class="card" markdown>

### Job Monitoring

Monitor upload and processing jobs via SSE real-time events or polling.

[:octicons-arrow-right-24: Job Monitoring](job-monitoring.md)

</div>

<div class="card" markdown>

### Chat API

Interact with the AIVA AI assistant programmatically with streaming SSE responses.

[:octicons-arrow-right-24: Chat API](chat-api.md)

</div>

<div class="card" markdown>

### Classification API

Classify variants using ACMG or AMP guidelines with AI-powered analysis.

[:octicons-arrow-right-24: Classification API](classification-api.md)

</div>

<div class="card" markdown>

### Database Queries

List, retrieve, and delete your uploaded variant data tables.

[:octicons-arrow-right-24: Database Queries](database-queries.md)

</div>

<div class="card" markdown>

### Export API

Export variant flags and threaded comments in CSV format.

[:octicons-arrow-right-24: Export API](export-api.md)

</div>

<div class="card" markdown>

### MCP Setup

Connect AIVA as an MCP server to Claude Desktop, OpenAI Codex, and other MCP-compatible clients. (Redirects to AIVA Chat section.)

[:octicons-arrow-right-24: MCP Setup](mcp-setup.md)

</div>

</div>

---

## Error Handling

The API uses standard HTTP status codes:

| Code | Meaning |
|------|---------|
| `200` | Success |
| `201` | Resource created |
| `400` | Bad request: check your parameters |
| `401` | Unauthorized: invalid or missing API key |
| `403` | Forbidden: insufficient permissions or subscription tier |
| `404` | Resource not found |
| `429` | Rate limit exceeded |
| `500` | Internal server error |

Error responses include a JSON body:

```json
{
  "detail": "Error message describing the issue."
}
```

---

## Content Types

- File upload requests use `multipart/form-data`.
- JSON body requests use `application/json`.
- Responses are `application/json` unless otherwise noted.
- Streaming endpoints use `text/event-stream` (Server-Sent Events).
