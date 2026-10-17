# KQL — Microsoft Sentinel & Defender XDR

## Objective

Use Kusto Query Language (KQL) to query security telemetry, investigate events, hunt for threats, and develop detection logic.

## Environment

* **Microsoft Sentinel**
* **Log Analytics Workspace**
* **Microsoft Defender XDR**
* **KQL**

## KQL Areas

### Fundamentals

Core KQL operations used to filter, project, sort, summarize, and manipulate security data.

### Authentication

Queries for sign-in activity, failed authentication, suspicious authentication patterns, and account activity.

### Endpoint

Queries for processes, devices, files, and endpoint security events.

### Network

Queries for network connections, IP addresses, ports, and communication patterns.

### Identity

Queries for user activity, account behavior, privilege-related activity, and identity investigations.

### Threat Hunting

Queries designed to identify suspicious or anomalous activity that may not have generated an alert.

### Detection

KQL queries used as the detection logic for Microsoft Sentinel analytics rules.

## Query Workflow

```text
Security Telemetry
        ↓
KQL Query
        ↓
Filter / Correlate / Aggregate
        ↓
Investigation or Detection
        ↓
Result
```

## Validation

Each query should be:

* Executed against the intended table
* Validated for returned results
* Reviewed for false positives
* Documented with its investigation or detection purpose

## Result

KQL queries are used to investigate security telemetry, perform threat hunting, and develop detection logic across Microsoft Sentinel and Microsoft Defender XDR.
