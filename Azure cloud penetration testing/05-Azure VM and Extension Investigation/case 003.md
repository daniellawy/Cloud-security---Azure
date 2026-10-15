# Case 003 — Azure VM and Extension Investigation

## Objective

Assess the permissions and configuration of an Azure environment accessed through compromised credentials and identify potential privilege-escalation paths involving virtual machines, managed identities, and VM extensions.

## Scope

Testing was restricted to the authorized TryHackMe Azure lab environment.

Activities included:

* Azure identity reconnaissance
* Resource-group enumeration
* Azure RBAC analysis
* Virtual machine configuration review
* Managed-identity assessment
* VM extension analysis
* Network and storage resource review

## Environment

The environment contained:

* Microsoft Entra ID
* Azure subscription
* Azure resource group
* Linux VM `VM1`
* System-assigned managed identity
* Virtual network
* Network interface
* Managed disk
* `AADSSHLoginForLinux` extension
* `CustomScriptExtension`

## Initial Reconnaissance

The compromised Azure account was first examined to determine its direct Azure permissions.

The account had:

**Reader**

access at the resource-group scope.

The accessible resources were then enumerated.

The investigation identified `VM1` and its associated networking, storage, managed-identity, and VM-extension resources.

![Azure resource enumeration](screenshots/01-resource-enumeration.png)

## Security Testing

`VM1` was identified as having a **system-assigned managed identity**.

The identity was investigated as a potential privilege-escalation mechanism.

Unlike Case 002, direct RBAC enumeration did not identify an exploitable role assignment for the managed identity.

The investigation therefore expanded to the VM configuration and installed extensions.

The following extensions were identified:

* `AADSSHLoginForLinux`
* `CustomScriptExtension`

![VM configuration](screenshots/02-vm-configuration.png)

## Managed Identity Analysis

The VM's system-assigned managed identity was reviewed to determine whether it had additional Azure permissions that could provide an escalation path.

The investigation did not identify the same directly exploitable RBAC relationship observed in Case 002.

This established an important distinction between identifying a managed identity and demonstrating that the identity actually provides additional Azure privileges.

![Managed identity](screenshots/03-managed-identity.png)

## VM Extension Analysis

The VM extensions were then examined as a separate attack surface.

`AADSSHLoginForLinux` was identified as part of the VM's authentication configuration.

The `CustomScriptExtension` was also identified.

VM extensions can provide administrative execution capabilities within the VM, making extension configuration and modification permissions relevant to privilege-escalation analysis.

![VM extensions](screenshots/04-vm-extensions.png)

## Attack Path Analysis

The investigation produced the following assessment path:

```text id="x8xq6u"
Compromised Azure Identity
        ↓
Reader Access
        ↓
Resource Group Enumeration
        ↓
VM1
        ↓
System-Assigned Managed Identity
        ↓
RBAC Analysis
        ↓
No Direct Escalation Identified
        ↓
VM Extension Analysis
        ↓
CustomScriptExtension
        ↓
Additional Security Boundary
```

The investigation therefore did not treat the presence of a managed identity as proof of privilege escalation.

Instead, RBAC permissions, resource scope, VM configuration, and extension configuration were assessed together.

![Attack path analysis](screenshots/05-attack-path.png)

## Findings

### Finding: Potential VM Extension Attack Surface

**Severity:** Medium

`VM1` had a `CustomScriptExtension`, representing a potentially significant administrative execution surface within the virtual machine.

The investigation did not identify a directly exploitable RBAC privilege-escalation path through the VM's managed identity.

The extension configuration was therefore treated as a separate security boundary requiring review.

## Validation

The following were validated:

1. The compromised Azure identity.
2. Direct RBAC permissions.
3. Accessible resource-group scope.
4. VM resources.
5. VM system-assigned managed identity.
6. Managed-identity RBAC assignments.
7. VM extensions.
8. `AADSSHLoginForLinux` configuration.
9. `CustomScriptExtension` presence.

The investigation confirmed that the managed identity did not provide the same directly exploitable RBAC path identified in Case 002.

## Remediation

* Remove unnecessary VM extensions.
* Review `CustomScriptExtension` configurations.
* Restrict permissions to modify VM extensions.
* Monitor VM extension creation and modification.
* Review managed-identity permissions regularly.
* Apply least privilege to Azure identities.
* Monitor Azure Activity Logs for VM configuration changes.

## Result

The investigation demonstrated a broader Azure cloud-security assessment methodology.

The VM's managed identity did not provide an immediately exploitable RBAC escalation path. However, the VM extensions represented an additional security boundary that required investigation.

The case reinforced the importance of analyzing Azure privilege escalation as an **attack-path problem**, correlating identities, RBAC, resource scope, VM configuration, extensions, and management capabilities rather than relying on a single permission or configuration.
