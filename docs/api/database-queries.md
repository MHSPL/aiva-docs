---
title: Database Queries
description: API reference for managing uploaded variant data tables in AIVA, including listing, retrieving data, and deleting tables.
---

# Database Queries

The Database endpoints allow you to list your uploaded variant data tables, retrieve table data, and delete tables.

---

## List Tables

Retrieve a list of all data tables associated with your account.

### Request

```
GET /tables
```

### Examples

=== "cURL"

    ```bash
    curl https://api.aivaportal.com/tables \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}
    response = requests.get("https://api.aivaportal.com/tables", headers=headers)
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/tables", {
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
[
  {
    "table_name": "patient_001_variants",
    "sample_name": "Patient-001",
    "row_count": 45230,
    "created_at": "2026-03-09T10:00:00Z"
  },
  {
    "table_name": "patient_002_variants",
    "sample_name": "Patient-002",
    "row_count": 38100,
    "created_at": "2026-03-08T14:30:00Z"
  }
]
```

---

## Get Table Data

Retrieve all data from a specific table.

### Request

```
GET /tables/{table_name}/data/all
```

### Examples

=== "cURL"

    ```bash
    curl https://api.aivaportal.com/tables/patient_001_variants/data/all \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    response = requests.get(
        "https://api.aivaportal.com/tables/patient_001_variants/data/all",
        headers=headers,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch(
      "https://api.aivaportal.com/tables/patient_001_variants/data/all",
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
  "table_name": "patient_001_variants",
  "columns": ["chrom", "pos", "ref", "alt", "qual", "filter", "gene", "consequence"],
  "rows": [
    {
      "chrom": "17",
      "pos": 41245466,
      "ref": "G",
      "alt": "A",
      "qual": 99.0,
      "filter": "PASS",
      "gene": "BRCA1",
      "consequence": "missense_variant"
    }
  ],
  "total_rows": 45230
}
```

---

## Delete a Table

Delete a data table and all its associated data.

### Request

```
DELETE /tables/{table_name}
```

### Examples

=== "cURL"

    ```bash
    curl -X DELETE https://api.aivaportal.com/tables/patient_001_variants \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    response = requests.delete(
        "https://api.aivaportal.com/tables/patient_001_variants",
        headers=headers,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch(
      "https://api.aivaportal.com/tables/patient_001_variants",
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
  "table_name": "patient_001_variants",
  "deleted": true
}
```

!!! warning "Irreversible operation"
    Deleting a table permanently removes all variant data associated with it. This action cannot be undone.
