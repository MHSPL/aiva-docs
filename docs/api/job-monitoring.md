---
title: Job Monitoring
description: API reference for monitoring upload and processing jobs in AIVA via SSE real-time events and polling.
---

# Job Monitoring

After uploading files, monitor the progress of your processing jobs using real-time Server-Sent Events (SSE) or by polling individual job status.

---

## Job States

Jobs progress through the following states:

| State | Description |
|-------|-------------|
| `upload_pending` | File upload is in progress |
| `queued` | Job is queued for processing |
| `processing` | Job is actively being processed |
| `completed` | Job finished successfully |
| `failed` | Job encountered an error |
| `cancelled` | Job was cancelled by the user |

---

## SSE Real-Time Events

Connect to the SSE endpoint to receive real-time job status updates. This is the recommended approach for monitoring jobs.

### Request

```
GET /jobs/events?token=<API_KEY>
```

!!! note "Authentication"
    The SSE endpoint uses a `token` query parameter instead of the `Authorization` header for compatibility with SSE clients.

### Examples

=== "cURL"

    ```bash
    curl -N "https://api.aivaportal.com/jobs/events?token=<AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    response = requests.get(
        "https://api.aivaportal.com/jobs/events",
        params={"token": "<AIVA_API_KEY>"},
        stream=True,
    )

    for line in response.iter_lines():
        if line:
            decoded = line.decode("utf-8")
            print(decoded)
    ```

=== "JavaScript"

    ```javascript
    const eventSource = new EventSource(
      "https://api.aivaportal.com/jobs/events?token=<AIVA_API_KEY>"
    );

    eventSource.onmessage = (event) => {
      const data = JSON.parse(event.data);
      console.log("Job update:", data);
    };

    eventSource.onerror = (error) => {
      console.error("SSE error:", error);
      eventSource.close();
    };
    ```

### SSE Event Format

Events are streamed in standard SSE format:

```
data: {"job_id": "job_abc123", "status": "processing", "progress": 45, "message": "Running variant annotation..."}

data: {"job_id": "job_abc123", "status": "completed", "message": "Job completed successfully."}
```

---

## Poll Job Status

Poll the status of an individual job by its ID.

### Request

```
GET /jobs/{job_id}/status
```

### Examples

=== "cURL"

    ```bash
    curl https://api.aivaportal.com/jobs/job_abc123/status \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    response = requests.get(
        "https://api.aivaportal.com/jobs/job_abc123/status",
        headers=headers,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch(
      "https://api.aivaportal.com/jobs/job_abc123/status",
      {
        headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      }
    );
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_abc123",
  "status": "processing",
  "progress": 65,
  "message": "Running variant annotation...",
  "created_at": "2026-03-09T10:30:00Z",
  "updated_at": "2026-03-09T10:35:00Z"
}
```

---

## List Jobs

Retrieve a list of all your jobs.

### Request

```
GET /jobs
```

### Examples

=== "cURL"

    ```bash
    curl https://api.aivaportal.com/jobs \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}
    response = requests.get("https://api.aivaportal.com/jobs", headers=headers)
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/jobs", {
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
[
  {
    "job_id": "job_abc123",
    "status": "completed",
    "sample_name": "Patient-001",
    "created_at": "2026-03-09T10:30:00Z",
    "completed_at": "2026-03-09T10:45:00Z"
  },
  {
    "job_id": "job_def456",
    "status": "processing",
    "sample_name": "Patient-002",
    "created_at": "2026-03-09T11:00:00Z"
  }
]
```

---

## Cancel a Job

Cancel a job that is in `queued` or `processing` state.

### Request

```
POST /jobs/{job_id}/cancel
```

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/job_abc123/cancel \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    response = requests.post(
        "https://api.aivaportal.com/jobs/job_abc123/cancel",
        headers=headers,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch(
      "https://api.aivaportal.com/jobs/job_abc123/cancel",
      {
        method: "POST",
        headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      }
    );
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_abc123",
  "status": "cancelled",
  "message": "Job cancelled successfully."
}
```

---

## Delete a Job

Delete a job and its associated data. Only completed, failed, or cancelled jobs can be deleted.

### Request

```
DELETE /jobs/{job_id}
```

### Examples

=== "cURL"

    ```bash
    curl -X DELETE https://api.aivaportal.com/jobs/job_abc123 \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    response = requests.delete(
        "https://api.aivaportal.com/jobs/job_abc123",
        headers=headers,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch(
      "https://api.aivaportal.com/jobs/job_abc123",
      {
        method: "DELETE",
        headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      }
    );
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_abc123",
  "deleted": true
}
```

---

## Polling Strategy

If you cannot use SSE, poll the job status endpoint at a reasonable interval:

1. Poll every **5 seconds** while the job is in `queued` or `processing` state.
2. Stop polling when the job reaches `completed`, `failed`, or `cancelled`.
3. Use the `progress` field (when available) to display progress to users.

```python
import requests
import time

headers = {"Authorization": "Bearer <AIVA_API_KEY>"}
job_id = "job_abc123"

while True:
    response = requests.get(
        f"https://api.aivaportal.com/jobs/{job_id}/status",
        headers=headers,
    )
    data = response.json()
    print(f"Status: {data['status']}")

    if data["status"] in ("completed", "failed", "cancelled"):
        break

    time.sleep(5)
```
