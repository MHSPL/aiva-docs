---
title: Compliance
description: AIVA's compliance features including HIPAA-aligned PHI detection, data encryption, access controls, and secure data handling practices.
---

# Compliance

AIVA provides features aligned with HIPAA (Health Insurance Portability and Accountability Act) requirements for protecting electronic Protected Health Information (ePHI). This page describes the platform's data protection capabilities and how they support HIPAA compliance.

---

## PHI Detection

AIVA includes a PHI detection system that identifies potential Protected Health Information in the **clinical notes** section of sample metadata. When entering or editing clinical notes, detected PHI entities are highlighted in real time so you can review them before saving.

### Detected Entity Types

The system detects 40+ PHI entity types, including:

| Category | Entity Types |
|----------|-------------|
| **Patient Identifiers** | Names, dates of birth, Social Security numbers, medical record numbers, health plan numbers |
| **Contact Information** | Addresses, phone numbers, fax numbers, email addresses |
| **Digital Identifiers** | IP addresses, device identifiers, URLs, biometric identifiers |
| **Clinical Staff** | Healthcare worker names, doctor names, staff identifiers |
| **Organizations** | Hospital names, vendor names |
| **Genomic Identifiers** | Sample IDs, specimen IDs, accession numbers, family IDs, subject IDs, NCBI/GenBank accessions, dbGaP IDs |
| **Dates** | Admission dates, discharge dates, dates of service, ages (elements more specific than year) |
| **Location** | Street addresses, cities, states, ZIP codes, geographic identifiers |
| **Other** | Account numbers, certificate/license numbers, vehicle identifiers, photographs |

### How PHI Detection Works

1. **Clinical notes input**: When you enter or edit clinical notes for a sample, the text is analyzed for PHI entities.
2. **Real-time highlighting**: Detected entities are highlighted inline with their entity type so you can review flagged content before saving.
3. **Hybrid detection**: The system uses a Stanford de-identification model (neural network) for entity recognition, supplemented by regex pattern matching for structured identifiers like SSNs, emails, and genomic accessions.

!!! warning "Detection limitations"
    Automated PHI detection may not catch all instances of PHI, especially in unusual formats or contexts. Do not rely solely on automated detection. Review clinical notes before saving and follow your organization's PHI handling policies.

---

## Data Encryption

### At Rest

- Sensitive credentials are encrypted using symmetric encryption before storage.

### In Transit

- HTTPS is enforced for all API and web traffic.

---

## Access Controls

### Authentication

- Email and password authentication

### Authorization

Access to data is controlled at multiple levels:

| Level | Control |
|-------|---------|
| **User** | Each user can only access their own uploaded samples by default. |
| **Project** | Samples shared through projects are accessible to project members based on their role. |
| **Role** | Project roles (Owner, Admin, Editor, Viewer) define what actions a user can perform. |
| **API** | [API keys](../api/index.md) inherit the permissions of the creating user. |
| **AI Tools** | The Genomic Data Query tool is scoped to the user's accessible data. AIVA cannot query other users' data. |

### Session Management

- Token-based authentication with automatic expiry.
- API keys support configurable expiration (1 to 365 days).
- API key usage is tracked with last-used timestamps.

---

## Data Handling

### Data Retention

- Uploaded sample data is retained as long as the user's account is active.
- Deleted samples are purged from the database and storage.
- Conversation history can be deleted by the user.

### Data Isolation

- Each user's data is logically isolated in the database.
- Cross-user data access is prevented at the application and database layers.
- Project-based sharing creates controlled access pathways with explicit permissions.

### Data Export and Portability

- Users can export all their data at any time.
- Exported data includes variants, flags, comments, and classifications.
- Account deletion removes all associated data from the platform.

---

## AI Model Provider Agreements

AIVA maintains Business Associate Agreements (BAAs) with all AI model providers used by the platform:

- **Anthropic** (Claude)
- **OpenAI** (GPT)
- **Google** (Gemini)

Under these agreements:

- Your data is **not stored** on provider servers beyond the duration of a request.
- Your data is **not used** for model training or improvement.
- All API communication is encrypted in transit.

---

## Compliance Responsibilities

!!! note "Shared responsibility"
    AIVA provides the tools and infrastructure for compliance, but effective compliance requires appropriate use by the organization. Users and administrators are responsible for:

    - Configuring access controls appropriately.
    - Training users on data handling procedures.
    - Establishing organizational policies for PHI management.
    - Executing Business Associate Agreements (BAAs) where required.
