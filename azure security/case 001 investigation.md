# Case 001 — Azure Cloud Security Investigation

## Objective

Assess the Azure environment associated with compromised credentials and identify privilege-escalation opportunities involving Azure RBAC, managed identities, virtual machines, and Azure Key Vault.

## Scope

Testing was restricted to the authorized TryHackMe Azure lab environment.

Activities included:

* Azure identity reconnaissance
* Resource enumeration
* RBAC analysis
* Managed-identity assessment
* Virtual-machine configuration review
* Key Vault access validation

## Environment

The environment contained:

* Microsoft Entra ID
* Azure subscription
* Azure resource group
* Linux virtual machine
* System-assigned managed identity
* Azure RBAC
* Azure Key Vault
* Azure management APIs

## 1. Initial Reconnaissance

The compromised Azure account was used to establish the tenant and subscription context and enumerate accessible resources.

The investigation reviewed:

* Current Azure identity
* Subscription
* Resource group
* Virtual machine configuration
* VM managed identity
* RBAC assignments
* Key Vault configuration

The VM's **system-assigned managed identity** was identified as a relevant security principal.

![Azure reconnaissance](screenshots/01-reconnaissance.png)

## 2. RBAC Analysis

The managed identity's Azure RBAC assignments were reviewed to determine whether its permissions exceeded the requirements of the workload.

The investigation identified excessive permissions assigned to the VM-associated managed identity.

![RBAC assignments](screenshots/02-rbac-assignments.png)

## 3. Attack Path

The identified privilege path was:

```text
Compromised Azure Identity
        ↓
Azure Resource Enumeration
        ↓
Linux VM
        ↓
System-Assigned Managed Identity
        ↓
Over-Privileged RBAC Assignment
        ↓
Azure Resource Access
        ↓
Key Vault
        ↓
Protected Lab Secret
```

![Attack path](screenshots/03-attack-path.png)

## 4. Managed Identity Assessment

The VM's system-assigned managed identity was examined as an independent Azure security principal.

Its assigned permissions demonstrated that the identity could interact with Azure resources beyond the minimum privileges required by the workload.

![Managed identity](screenshots/04-managed-identity.png)

## 5. Key Vault Access Validation

The protected Key Vault resource was identified during resource enumeration.

Access was then validated through the authorized lab attack path using the permissions available to the managed identity.

The lab-provided protected secret was successfully accessed, confirming that the excessive permissions were exploitable.

![Key Vault validation](screenshots/05-key-vault-access.png)

## Finding

### Over-Privileged Managed Identity

**Severity:** High

The VM-associated managed identity possessed excessive Azure permissions.

This created an indirect privilege-escalation path in which compromise of the workload could be converted into access to additional Azure resources.

## Validation

The attack path was validated by:

1. Identifying the managed identity.
2. Enumerating its RBAC assignments.
3. Establishing authorized management access through the identity.
4. Identifying the protected Key Vault.
5. Validating access to the lab-provided secret.

The retrieved lab flag confirmed successful exploitation.

## Remediation

* Apply least privilege to managed identities.
* Remove unnecessary RBAC assignments.
* Reduce role-assignment scope.
* Review managed-identity permissions regularly.
* Monitor managed-identity access to Key Vault.
* Separate workload identities from administrative identities where appropriate.

## Result

The investigation demonstrated that an over-privileged system-assigned managed identity created a privilege-escalation path from a compromised workload to protected Azure resources.

The attack path was validated against the authorized lab environment through RBAC analysis, managed-identity assessment, and Key Vault access validation.
