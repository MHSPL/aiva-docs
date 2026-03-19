---
title: Compliance
description: Overview of AIVA's compliance features including HIPAA-aligned data protection, PHI detection, encryption, and comprehensive audit trails.
---

# Compliance

AIVA is designed with data security and regulatory compliance at its core. The platform provides multiple layers of protection for sensitive genomic and clinical data, including automated PHI detection, data encryption, access controls, and comprehensive audit logging.

---

## In This Section

<div class="grid-cards" markdown>

<div class="card" markdown>

### HIPAA Compliance

PHI detection, data encryption, access controls, and data handling practices aligned with HIPAA requirements.

[:octicons-arrow-right-24: HIPAA](hipaa.md)

</div>

<div class="card" markdown>

### Audit Trail

Comprehensive activity logging, user action history, IP tracking, and a filterable audit dashboard.

[:octicons-arrow-right-24: Audit Trail](audit-trail.md)

</div>

</div>

---

## Security Overview

AIVA implements security measures across multiple layers:

| Layer | Measures |
|-------|----------|
| **Data at Rest** | AES-256 encryption for stored data, encrypted backups |
| **Data in Transit** | TLS 1.2+ for all connections, HTTPS enforced |
| **Authentication** | Secure authentication with multi-factor authentication support |
| **Authorization** | Role-based access controls, per-sample and per-project permissions |
| **PHI Protection** | Automated detection of 20+ PHI entity types, configurable data handling |
| **Audit** | Comprehensive logging of all user actions with IP tracking |
| **Infrastructure** | Security headers, SQL injection prevention, input validation, sandboxed code execution |

---

## Compliance Responsibilities

!!! note "Shared responsibility"
    AIVA provides the tools and infrastructure for compliance, but effective compliance requires appropriate use by the organization. Users and administrators are responsible for:

    - Configuring access controls appropriately.
    - Reviewing audit logs regularly.
    - Training users on data handling procedures.
    - Establishing organizational policies for PHI management.
    - Executing Business Associate Agreements (BAAs) where required.
