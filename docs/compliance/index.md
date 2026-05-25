---
title: Compliance
description: AIVA's compliance features including HIPAA-aligned PHI detection, data encryption, access controls, and secure data handling practices.
---

# Compliance

AIVA provides features aligned with HIPAA (Health Insurance Portability and Accountability Act) requirements for protecting electronic Protected Health Information (ePHI). This page describes the platform's data protection capabilities, intended use, and the shared responsibilities involved in using AIVA within a clinical or research workflow.

---

## Intended Use

AIVA is assistive software for qualified laboratory and research professionals, including:

- Clinical bioinformaticians
- Variant scientists and clinical molecular geneticists
- Molecular pathologists
- Genetic counselors reviewing variant evidence
- CLIA laboratory directors and their designees
- Translational and basic researchers

The platform supports variant annotation, interpretation drafting, evidence aggregation, and report generation. Outputs are intended to **assist** professional review, not to replace it.

### What AIVA is not

- AIVA is **not** a standalone diagnostic device.
- AIVA does **not** issue a medical diagnosis, prescribe treatment, or render clinical advice to patients.
- AIVA has **not** received FDA clearance or approval as an In Vitro Diagnostic (IVD) device and is not CE-IVD marked.
- AI-generated content (classifications, summaries, draft reports) is a starting point for expert review, not a final clinical determination.

### Clinical use within a validated workflow

AIVA may be used to support clinical reporting when it is integrated into a laboratory's own validated workflow under CLIA, CAP, or an equivalent accreditation framework. In this model:

- The laboratory is responsible for validating AIVA's use within its specific assay, sample types, and reporting scope.
- Final interpretation and clinical sign-out remain the responsibility of the laboratory director or their qualified designee, consistent with CLIA §493.1445 (laboratory director responsibilities) and the equivalent CAP Molecular Pathology checklist requirements for report review and authorization.
- Source evidence (ClinVar, gnomAD, OMIM, literature, and other annotations cited by AIVA) should be independently reviewed before sign-out.

!!! warning "Clinical responsibility"
    AIVA does not replace professional judgment. The signing laboratory director, pathologist, or qualified designee is responsible for the accuracy, completeness, and clinical validity of any report issued from AIVA outputs.

---

## Limitations

Users should be aware of the following limitations when relying on AIVA outputs:

- **AI variability.** Large language model outputs may contain errors, omissions, or fabricated references. All AI-generated content requires expert review.
- **Reference data drift.** Annotations draw from external databases (ClinVar, gnomAD, OMIM, literature, and others) that update continuously. A classification valid today may change as evidence evolves.
- **Coverage gaps.** AIVA has not been validated for every variant class, gene, ancestry group, assay chemistry, or clinical indication. Performance in edge cases may vary.
- **Automated PHI detection.** Detection is probabilistic and may miss PHI in unusual formats. See [PHI Detection](#phi-detection) below.
- **Third-party tools.** Outputs from connected MCP servers and external tools are governed by their own terms and accuracy guarantees.

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

- **Paid accounts.** Uploaded sample data is retained for the duration of your active paid subscription.
- **Free tier.** Data uploaded under a Free tier account is automatically and permanently deleted no later than 14 days after the account enters Free tier status. This applies both to new Free tier signups and to accounts that downgrade from a paid plan. Upgrade to a paid plan within the 14-day window to retain access.
- **User-initiated deletion.** Deleting a sample, project, or account removes the associated data from active systems immediately. Once deleted, data cannot be recovered, so export anything you wish to keep first.
- **Post-termination export window.** Upon termination of a paid subscription, a 14-day window is provided to export data before permanent deletion. See [Terms of Service §8](https://mamidi.ai/terms-of-service) for details.
- **AI provider processing.** Data sent to third-party AI providers is subject to zero-day retention at the provider level; see [AI Model Provider Agreements](#ai-model-provider-agreements) below.
- Conversation history can be deleted by the user at any time.

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

AIVA processes data through third-party AI model providers under Business Associate Agreements (BAAs) or equivalent contractual data-protection commitments. Current providers include:

- **Anthropic** (Claude)
- **OpenAI** (GPT)
- **Google** (Gemini)

The specific contractual instrument (BAA, Data Processing Addendum, or enterprise data-protection terms) varies by provider and product tier. Under these agreements (often referred to as **zero-day retention** at the provider level):

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
    - Validating AIVA's use within the laboratory's assay scope and reporting workflow, where AIVA outputs are used to support clinical sign-out.
    - Ensuring that all clinical interpretations and reports are reviewed and signed out by qualified personnel under CLIA, CAP, or equivalent accreditation.

---

## International Users (GDPR)

For users in the European Union and other regions subject to GDPR, Mamidi Health LLC processes personal data on the lawful bases described in the Privacy Policy (consent, contract performance, and legitimate interests). Data subject rights, including access, correction, deletion, restriction, and objection, can be exercised by contacting us at the email below. Data portability under GDPR Article 20 applies where processing is based on consent or contract performance; data export is also offered as a platform feature to all users via the [Data Export and Portability](#data-export-and-portability) controls regardless of legal basis. See the [Privacy Policy](https://mamidi.ai/privacy-policy) for full details.

---

## Legal Terms

Use of AIVA is governed by the [Mamidi Health LLC Terms of Service](https://mamidi.ai/terms-of-service) and [Privacy Policy](https://mamidi.ai/privacy-policy), which include the platform's warranty disclaimers, limitation of liability, and data retention commitments. The guidance on this page describes how the platform supports compliance and clinical workflows; it does not modify or supersede those agreements.

For privacy, data, or compliance inquiries, contact **tarun@mamidi.ai**.
