---
title: HIPAA Compliance
description: AIVA's HIPAA-aligned features including automated PHI detection, data encryption, access controls, and secure data handling practices.
---

# HIPAA Compliance

AIVA provides features aligned with HIPAA (Health Insurance Portability and Accountability Act) requirements for protecting electronic Protected Health Information (ePHI). This page describes the platform's data protection capabilities and how they support HIPAA compliance.

---

## PHI Detection

AIVA includes an automated PHI detection system that identifies potential Protected Health Information in uploaded data and user-generated content.

### Detected Entity Types

The system detects 20+ PHI entity types, including:

| Category | Entity Types |
|----------|-------------|
| **Patient Identifiers** | Names, dates of birth, Social Security numbers, medical record numbers, health plan numbers |
| **Contact Information** | Addresses, phone numbers, fax numbers, email addresses |
| **Digital Identifiers** | IP addresses, device identifiers, URLs, biometric identifiers |
| **Dates** | Admission dates, discharge dates, dates of service (elements more specific than year) |
| **Other** | Account numbers, certificate/license numbers, vehicle identifiers, photographs |

### How PHI Detection Works

1. **On upload**: File contents are scanned for PHI patterns during the parsing stage.
2. **In chat**: User messages and AI responses are monitored for PHI content.
3. **In comments**: Variant comments and annotations are checked for PHI.
4. **Flagged content**: Detected PHI is flagged with the entity type and location.

!!! warning "Detection limitations"
    Automated PHI detection uses pattern matching and natural language processing. It may not catch all instances of PHI, especially in unusual formats or contexts. Do not rely solely on automated detection. Review data before sharing and follow your organization's PHI handling policies.

---

## Data Encryption

### At Rest

- All stored data is encrypted using AES-256 encryption.
- Database fields containing sensitive data use additional column-level encryption.
- Backups are encrypted before storage.
- Encryption keys are managed through a dedicated key management service.

### In Transit

- All connections use TLS 1.2 or higher.
- HTTPS is enforced for all API and web traffic.
- Certificate pinning is available for API integrations.
- Internal service-to-service communication is encrypted.

---

## Access Controls

### Authentication

- **Secure authentication** provides the identity layer with support for:
    - Email and password authentication
    - Multi-factor authentication (MFA)
    - Single sign-on (SSO) integration for enterprise deployments

### Authorization

Access to data is controlled at multiple levels:

| Level | Control |
|-------|---------|
| **User** | Each user can only access their own uploaded samples by default. |
| **Project** | Samples shared through [projects](../collaboration/projects.md) are accessible to project members based on their role. |
| **Role** | Project roles (Owner, Admin, Editor, Viewer) define what actions a user can perform. |
| **API** | [API keys](../api/api-keys.md) inherit the permissions of the creating user. |
| **AI Tools** | The Genomic Data Query tool is scoped to the user's accessible data. AIVA cannot query other users' data. |

### Session Management

- Sessions expire after a configurable inactivity period.
- Concurrent session limits can be enforced.
- Session invalidation on password change.

---

## Data Handling

### Data Retention

- Uploaded sample data is retained as long as the user's account is active.
- Deleted samples are purged from the database and storage.
- Conversation history can be deleted by the user.
- Audit logs are retained according to the organization's configured retention policy.

### Data Isolation

- Each user's data is logically isolated in the database.
- Cross-user data access is prevented at the application and database layers.
- Project-based sharing creates controlled access pathways with explicit permissions.

### Data Export and Portability

- Users can [export](../api/export-api.md) all their data at any time.
- Exported data includes variants, flags, comments, and classifications.
- Account deletion removes all associated data from the platform.

---

## Security Headers

AIVA's backend applies security headers to all HTTP responses:

| Header | Purpose |
|--------|---------|
| `X-Content-Type-Options: nosniff` | Prevents MIME type sniffing |
| `X-Frame-Options: DENY` | Prevents clickjacking |
| `X-XSS-Protection: 1; mode=block` | Enables browser XSS filtering |
| `Strict-Transport-Security` | Enforces HTTPS connections |
| `Content-Security-Policy` | Controls resource loading sources |
| `Referrer-Policy: strict-origin-when-cross-origin` | Limits referrer information |

---

## SQL Injection Prevention

All database queries use parameterized SQL composition (psycopg.sql module) rather than string formatting. This prevents SQL injection attacks at the database layer.

---

## Recommendations for Organizations

1. **Enable MFA** for all user accounts handling PHI.
2. **Configure session timeouts** appropriate for your environment.
3. **Review audit logs** regularly for unusual access patterns (see [Audit Trail](audit-trail.md)).
4. **Limit project membership** to only the users who need access.
5. **Train users** on PHI handling within the platform.
6. **Execute a BAA** with AIVA before processing PHI.
7. **Establish data retention policies** and configure the platform accordingly.
