# Case 002 — Azure Virtual Machine Privilege Escalation

## Objective

Identify an attack path from a compromised Azure environment to another virtual machine by analyzing managed identities and Azure RBAC permissions.

## Scope

Testing was restricted to the authorized TryHackMe Azure environment.

Activities included:

* Azure resource enumeration
* Virtual machine configuration review
* Managed-identity assessment
* Azure RBAC analysis
* RBAC scope analysis
* Azure VM Run Command validation

## Environment

The environment contained:

* Azure subscription
* Azure resource group
* Linux virtual machines
* System-assigned managed identity
* Azure RBAC
* Azure VM Run Command

## Initial Reconnaissance

The compromised Azure account initially provided limited visibility into the environment.

Azure resources were enumerated, revealing two Linux virtual machines within the assigned resource group.

The primary VM was identified as having a **system-assigned managed identity**.

The investigation then examined the identity's Azure RBAC assignments and effective scope.

![VM enumeration](screenshots/01-vm-enumeration.png)

## Security Testing

The VM's system-assigned managed identity was found to have the:

**Virtual Machine Contributor**

role at the **resource-group scope**.

This was significant because the assignment was not limited to the originating VM. The permissions applied across the resource group and allowed substantial virtual-machine management operations, including Azure VM Run Command.

The second Linux VM was therefore identified as a potential target within the identity's effective permission scope.

![Managed identity RBAC](screenshots/02-managed-identity-rbac.png)

## Attack Path

The identified privilege path was:

```text
Compromised Workload
        ↓
System-Assigned Managed Identity
        ↓
Virtual Machine Contributor
        ↓
Resource-Group Scope
        ↓
Secondary Virtual Machine
        ↓
Azure VM Run Command
        ↓
Root Command Execution
```

![Attack path](screenshots/03-attack-path.png)

## Validation

The attack path was validated within the authorized lab environment by:

1. Identifying the primary VM's system-assigned managed identity.
2. Enumerating the identity's RBAC role.
3. Confirming the resource-group assignment scope.
4. Identifying the secondary VM within the same scope.
5. Using the identity's authorized VM-management capability to invoke Run Command.
6. Confirming command execution on the secondary VM.
7. Confirming execution as `root`.
8. Locating the lab-provided flag on the target VM.

![Run Command validation](screenshots/04-run-command.png)

The target VM confirmed successful command execution with administrative privileges.

![Command execution](screenshots/05-command-execution.png)

The lab flag was located at:

```text
/home/tyler/flag.txt
```

![Flag validation](screenshots/06-flag-validation.png)

## Findings

### Finding: Excessive Virtual Machine Contributor Permissions

**Severity:** High

A VM-associated managed identity possessed **Virtual Machine Contributor** permissions at resource-group scope.

The assignment was broader than necessary for the originating workload and allowed VM-management operations against other virtual machines within the resource group.

This created an indirect privilege-escalation path from the compromised workload to another VM.

## Remediation

* Apply least privilege to VM managed identities.
* Replace broad VM-management roles with narrowly scoped permissions.
* Reduce RBAC assignments from resource-group scope where possible.
* Review managed-identity permissions regularly.
* Restrict and monitor Azure VM Run Command usage.
* Separate workload identities from administrative identities.
* Monitor VM-management operations performed by managed identities.

## Result

The investigation demonstrated that an over-privileged system-assigned managed identity could provide an indirect privilege-escalation path from a compromised workload to another Azure virtual machine.

The attack path was validated through RBAC analysis, scope assessment, managed-identity evaluation, and controlled VM Run Command execution, resulting in administrative command execution on the target VM.
