# Microsoft Defender XDR

## Objective

Demonstrate practical Microsoft Defender XDR administration, security investigation, and threat-analysis workflows.

The work in this section focuses on understanding the Defender XDR platform, configuring access controls, investigating security activity, and applying security concepts across endpoint and identity environments.

## Environment

* Microsoft Defender XDR
* Microsoft Defender portal
* Microsoft Defender XDR Unified RBAC
* Microsoft Defender for Endpoint
* Microsoft Entra ID
* Advanced Hunting
* Defender security workloads available in the lab tenant

## Tasks Performed

### 01 — XDR Configuration and RBAC

Configured and reviewed Microsoft Defender XDR Unified RBAC.

Activities included:

* Accessing **Permissions and roles**
* Reviewing available Defender workloads
* Activating applicable workloads
* Reviewing workload settings
* Reviewing custom security roles
* Reviewing permission groups
* Reviewing role assignments
* Reviewing assigned users/groups
* Reviewing Defender data-source scope
* Validating least-privilege access concepts

### 02 — Defense Evasion

Investigated techniques associated with attempts to avoid or bypass security controls.

Activities include:

* Reviewing endpoint telemetry
* Identifying suspicious process activity
* Investigating security-control evasion indicators
* Correlating process and network activity
* Reviewing related alerts and evidence

### 03 — Privilege Escalation

Investigated activity associated with attempts to obtain elevated permissions.

Activities include:

* Reviewing identity activity
* Investigating privileged account activity
* Reviewing process and account context
* Correlating endpoint and identity telemetry

### 04 — Lateral Movement

Investigated activity associated with movement between systems.

Activities include:

* Reviewing device-to-device activity
* Investigating authentication patterns
* Reviewing network connections
* Correlating users, devices, and processes
* Identifying related security events

### 05 — Execution

Investigated suspicious process and command execution.

Activities include:

* Reviewing process creation
* Investigating command-line activity
* Reviewing parent/child process relationships
* Correlating execution with network activity
* Reviewing associated Defender alerts

### 06 — Credential Access

Investigated activity associated with credential theft and unauthorized authentication.

Activities include:

* Reviewing authentication activity
* Investigating account behavior
* Correlating identity and endpoint telemetry
* Reviewing suspicious credential-related activity

## Evidence

Evidence for each activity is stored with the relevant investigation or task.

```text
defender-xdr/
│
├── defense-evasion/
├── privilege-escalation/
├── lateral-movement/
├── execution/
└── credential-access/
```

Screenshots are stored alongside the relevant Markdown documentation and show configuration, investigation, query results, alerts, incidents, and other lab results.

Sensitive tenant-specific information should be sanitized or blurred before publishing the repository publicly.

## Investigation Workflow

The Defender XDR investigations follow a consistent workflow:

```text
Security Event
      ↓
Alert / Detection
      ↓
Incident
      ↓
Entities
      ↓
Evidence
      ↓
Advanced Hunting
      ↓
Correlation
      ↓
Investigation
      ↓
Response / Escalation
```

## Notes

* Defender XDR provides a unified security operations interface across supported Microsoft security workloads.
* Unified RBAC controls access through roles, permission groups, assignments, users/groups, and data-source scope.
* Available Defender workloads and permissions depend on the tenant's licensing and configuration.
* Incident investigations should correlate multiple evidence sources rather than relying on a single alert.
* Advanced Hunting is used to query security telemetry and support proactive investigation.
* Lab-specific usernames, hostnames, IP addresses, tenant identifiers, and other sensitive values should not be published unless intentionally sanitized.

## Result

This section documents practical experience with Microsoft Defender XDR configuration, access control, security investigation, endpoint and identity telemetry analysis, and threat-oriented investigation workflows.

