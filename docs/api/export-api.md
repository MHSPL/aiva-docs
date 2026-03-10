---
title: Export API
description: API reference for exporting variant flags and threaded comments from AIVA.
---

# Export API

The Export API provides endpoints for downloading variant flags and threaded comments in CSV format.

---

## Export Flags

Export variant flags for a specific table.

### Request

```
GET /api/variant-flags/export
```

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `table_name` | string | Yes | Name of the table to export flags from |
| `format` | string | No | Export format: `csv`. Default: `csv` |
| `project_id` | string | No | Filter flags by project |
| `include_member_flags` | boolean | No | Include flags from project members (owner only). Default: `false` |

### Examples

=== "cURL"

    ```bash
    curl "https://api.aivaportal.com/api/variant-flags/export?table_name=patient_001_variants&format=csv" \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -o flags.csv
    ```

    **With project and member flags:**

    ```bash
    curl "https://api.aivaportal.com/api/variant-flags/export?table_name=patient_001_variants&format=csv&project_id=proj_abc123&include_member_flags=true" \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -o flags.csv
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    params = {
        "table_name": "patient_001_variants",
        "format": "csv",
    }

    response = requests.get(
        "https://api.aivaportal.com/api/variant-flags/export",
        headers=headers,
        params=params,
    )

    with open("flags.csv", "wb") as f:
        f.write(response.content)

    print("Flags exported to flags.csv")
    ```

    **With project and member flags:**

    ```python
    params = {
        "table_name": "patient_001_variants",
        "format": "csv",
        "project_id": "proj_abc123",
        "include_member_flags": "true",
    }

    response = requests.get(
        "https://api.aivaportal.com/api/variant-flags/export",
        headers=headers,
        params=params,
    )

    with open("flags_with_members.csv", "wb") as f:
        f.write(response.content)
    ```

=== "JavaScript"

    ```javascript
    const params = new URLSearchParams({
      table_name: "patient_001_variants",
      format: "csv",
    });

    const response = await fetch(
      `https://api.aivaportal.com/api/variant-flags/export?${params}`,
      {
        headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      }
    );

    const blob = await response.blob();
    // Save or process the CSV blob
    console.log("Flags exported, size:", blob.size);
    ```

### Response

The response is a downloadable CSV file with `Content-Type: text/csv`.

!!! note "Owner-only feature"
    The `include_member_flags` parameter is only available to the project owner. Non-owners can only export their own flags.

---

## Export Comments

Export threaded comments for a specific table.

### Request

```
GET /api/variant-comments/export
```

### Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `table_name` | string | Yes | Name of the table to export comments from |
| `format` | string | No | Export format: `csv`. Default: `csv` |
| `project_id` | string | No | Filter comments by project |
| `include_member_comments` | boolean | No | Include comments from project members (owner only). Default: `false` |

### Examples

=== "cURL"

    ```bash
    curl "https://api.aivaportal.com/api/variant-comments/export?table_name=patient_001_variants&format=csv" \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -o comments.csv
    ```

    **With project and member comments:**

    ```bash
    curl "https://api.aivaportal.com/api/variant-comments/export?table_name=patient_001_variants&format=csv&project_id=proj_abc123&include_member_comments=true" \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -o comments.csv
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    params = {
        "table_name": "patient_001_variants",
        "format": "csv",
    }

    response = requests.get(
        "https://api.aivaportal.com/api/variant-comments/export",
        headers=headers,
        params=params,
    )

    with open("comments.csv", "wb") as f:
        f.write(response.content)

    print("Comments exported to comments.csv")
    ```

    **With project and member comments:**

    ```python
    params = {
        "table_name": "patient_001_variants",
        "format": "csv",
        "project_id": "proj_abc123",
        "include_member_comments": "true",
    }

    response = requests.get(
        "https://api.aivaportal.com/api/variant-comments/export",
        headers=headers,
        params=params,
    )

    with open("comments_with_members.csv", "wb") as f:
        f.write(response.content)
    ```

=== "JavaScript"

    ```javascript
    const params = new URLSearchParams({
      table_name: "patient_001_variants",
      format: "csv",
    });

    const response = await fetch(
      `https://api.aivaportal.com/api/variant-comments/export?${params}`,
      {
        headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      }
    );

    const blob = await response.blob();
    // Save or process the CSV blob
    console.log("Comments exported, size:", blob.size);
    ```

### Response

The response is a downloadable CSV file with `Content-Type: text/csv`.

!!! note "Owner-only feature"
    The `include_member_comments` parameter is only available to the project owner. Non-owners can only export their own comments.

---

## Related

See [Exporting Annotations](../collaboration/exporting-flags-comments.md) for the UI-based export workflow.
