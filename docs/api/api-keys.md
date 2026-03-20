---
title: API Keys
description: Create, manage, and revoke API keys for authenticating with the AIVA API. Verify connectivity with the health check endpoint.
---

# API Keys

API keys authenticate your requests to the AIVA API. Each key is tied to your user account and inherits your permissions and subscription limits.

---

## Creating an API Key

1. Navigate to **Settings** in the AIVA application.
2. Select the **API Keys** section.
3. Click **Create API Key**.
4. Enter a **name** for the key (e.g., "Lab Pipeline," "Research Script").
5. Optionally set an **expiration date**.
6. Click **Create**.
7. **Copy the key immediately**: it is only displayed once.

!!! warning "Store your key securely"
    The full API key is shown only at the time of creation. AIVA does not store the complete key and cannot retrieve it later. If you lose a key, revoke it and create a new one.

---

## Using an API Key

Include the API key in the `Authorization` header of every API request:

```
Authorization: Bearer <AIVA_API_KEY>
```

---

## Health Check

Use the health check endpoint to test your API connection and verify that your key is valid.

### Request

```
GET /health
```

### Examples

=== "cURL"

    ```bash
    curl https://api.aivaportal.com/health \
      -H "Authorization: Bearer <AIVA_API_KEY>"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}
    response = requests.get("https://api.aivaportal.com/health", headers=headers)
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/health", {
      headers: {
        "Authorization": "Bearer <AIVA_API_KEY>"
      }
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

A successful response confirms that your API key is valid and the service is operational:

```json
{
  "status": "ok"
}
```

If the key is invalid or missing, you will receive a `401 Unauthorized` response.

---

## Managing API Keys

### Listing Keys

View all active API keys from the **API Keys** section in Settings. Each key displays:

- **Name**: The label you assigned.
- **Created**: Date the key was created.
- **Last used**: Date and time of the most recent API call with this key.
- **Expires**: Expiration date (if set).
- **Key prefix**: The first few characters of the key for identification.

### Revoking a Key

1. Navigate to **Settings > API Keys**.
2. Find the key you want to revoke.
3. Click **Revoke**.
4. Confirm the revocation.

Revoked keys immediately stop working. Any scripts or integrations using the revoked key will receive `401 Unauthorized` responses.

!!! note "Revocation is permanent"
    A revoked key cannot be reinstated. You must create a new key to replace it.

---

## Key Permissions

API keys inherit the permissions of the user account that created them:

- Keys can access all samples belonging to the user.
- Keys can access samples shared through [projects](../collaboration/projects.md) where the user is a member.
- Keys are subject to the same [subscription tier](../getting-started/subscription-tiers.md) limits as the user account.

---

## Security Best Practices

- **Do not commit keys to version control.** Use environment variables or secret management services.
- **Create separate keys for separate use cases.** This makes it easy to revoke a single key without disrupting other integrations.
- **Set expiration dates** on keys used for temporary or one-time integrations.
- **Rotate keys periodically.** Create a new key, update your integrations, then revoke the old key.
- **Monitor key usage.** The "Last used" indicator helps identify inactive keys that should be revoked.
