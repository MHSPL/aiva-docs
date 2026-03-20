---
title: Audit Trail
description: AIVA's comprehensive audit trail system for tracking user actions, data access, and system events with a filterable dashboard.
---

# Audit Trail

AIVA maintains a comprehensive audit trail that logs all significant user actions, data access events, and system operations. The audit trail supports compliance requirements, security monitoring, and operational visibility.

---

## What Is Logged

The audit trail captures the following event categories:

### User Actions

| Action | Details Recorded |
|--------|-----------------|
| **Login / Logout** | Timestamp, IP address, authentication method, success/failure |
| **Sample Upload** | File name, file type, sample ID, annotation options selected |
| **Sample Deletion** | Sample ID, timestamp, user |
| **Data Query** | Query text (sanitized), sample accessed, result count |
| **Variant Flag** | Variant identifier, flag type, sample ID |
| **Comment Created** | Variant identifier, comment text, sample ID |
| **Classification** | Variant identifier, criteria selected, resulting classification |
| **Report Created** | Report ID, template used, linked samples |
| **Report Exported** | Report ID, export format |
| **API Key Created** | Key name, expiration date (key value not logged) |
| **API Key Revoked** | Key name, revocation timestamp |

### Data Access Events

| Event | Details Recorded |
|-------|-----------------|
| **Sample Viewed** | Sample ID, user, timestamp |
| **Data Table Accessed** | Sample ID, columns viewed, filters applied |
| **Export Downloaded** | Export type, file format, sample ID |
| **Project Membership Changed** | Project ID, user added/removed, role assigned |
| **Shared Sample Accessed** | Sample ID, accessing user, permission level |

### System Events

| Event | Details Recorded |
|-------|-----------------|
| **Job Processing** | Job ID, stage transitions, completion/failure status |
| **PHI Detection** | Entity type detected, location, action taken |
| **Rate Limit Hit** | User, endpoint, limit value |
| **Authentication Failure** | IP address, attempted account, failure reason |

---

## Viewing the Audit Trail

### Accessing the Dashboard

1. Navigate to **Administration** from the main navigation.
2. Select **Audit Trail** (administrator access required) or navigate to **Settings > Activity Log** for your own activity.

### Filtering Events

The audit dashboard provides filters to narrow the log:

| Filter | Options |
|--------|---------|
| **Date range** | Start and end dates for the time period of interest |
| **User** | Filter by specific user account |
| **Action type** | Filter by category (login, upload, query, flag, comment, etc.) |
| **Sample** | Filter by specific sample ID |
| **IP address** | Filter by source IP address |
| **Status** | Filter by success or failure |

### Searching

Use the search bar to find specific events by keyword, such as a user email, sample name, or variant identifier.

---

## Event Details

Click on any audit log entry to see full details:

- **Timestamp**: Exact date and time (UTC) of the event.
- **User**: The account that performed the action.
- **Action**: The type of action performed.
- **Resource**: The sample, report, or other resource affected.
- **IP Address**: The source IP address of the request.
- **User Agent**: The browser or client that made the request.
- **Details**: Additional context specific to the action type.
- **Status**: Whether the action succeeded or failed.

---

## IP Tracking

Every audit event includes the IP address of the originating request. This enables:

- **Geographic analysis**: Identify access from unexpected locations.
- **Anomaly detection**: Spot logins from new or unusual IP addresses.
- **Investigation support**: Trace specific actions to network locations.

!!! tip "Monitor for anomalies"
    Regularly review login events for your organization's accounts. Logins from unexpected IP addresses or at unusual times may indicate unauthorized access attempts.

---

## Retention and Export

### Retention Period

Audit logs are retained according to the organization's configured retention policy. The default retention period is 365 days. Administrators can adjust this in the platform settings.

### Exporting Audit Logs

To export audit data for external analysis or archival:

1. Open the Audit Trail dashboard.
2. Apply filters to select the events of interest.
3. Click **Export**.
4. Choose the format (CSV, JSON).
5. The export is downloaded to your device.

---

## Access Permissions

| Role | Audit Trail Access |
|------|--------------------|
| **Administrator** | Full access to all audit events for all users in the organization |
| **User** | Access to their own activity log only |
| **Viewer** | No audit trail access |

!!! note "Audit logs are read-only"
    Audit trail entries cannot be modified or deleted by any user, including administrators. This ensures the integrity of the audit record for compliance purposes.

---

## Using Audit Trails for Compliance

The audit trail supports compliance requirements by providing:

- **Access accountability**: Every data access is attributed to a specific user.
- **Change tracking**: Modifications to classifications, flags, and comments are logged with before and after states.
- **Incident investigation**: Detailed logs support forensic analysis of security events.
- **Regulatory reporting**: Exportable logs can be provided to auditors and regulators.

See [HIPAA Compliance](hipaa.md) for how the audit trail supports HIPAA requirements.
