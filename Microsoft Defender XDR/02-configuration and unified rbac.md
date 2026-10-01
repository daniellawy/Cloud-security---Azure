# Microsoft Defender XDR — Configuration and Unified RBAC

## Objective

Configure Microsoft Defender XDR Unified Role-Based Access Control (RBAC) and review how centralized permissions are assigned across Defender workloads.

## Environment

* Microsoft Defender portal
* Microsoft Defender XDR Unified RBAC
* Defender workloads available in the lab tenant
* Custom security role

## 1. Access Defender XDR

Sign in to the Microsoft Defender portal.

Navigate to:

**Permissions → Roles → Microsoft Defender XDR**

Review the **Permissions and roles** page.

![Microsoft Defender XDR permissions and roles](screenshots/fundamentals/01-permissions-and-roles.png)

## 2. Activate Defender Workloads

From **Permissions and roles**, select **Activate workloads**.

Review the Defender workloads available for activation.

Enable the workloads required by the lab environment.

> Available workloads depend on the licensing and configuration of the tenant.

![Activate Defender workloads](screenshots/fundamentals/02-activate-workloads.png)

## 3. Review Workload Settings

Return to **Permissions and roles** and open **Workload settings**.

Review the available Defender workloads and their RBAC activation state.

![Defender workload settings](screenshots/fundamentals/03-workload-settings.png)

## 4. Review the Defender Portal

Review the main Defender XDR navigation areas.

Relevant areas include:

* Incidents
* Alerts
* Advanced hunting
* Devices
* Identities
* Email and collaboration
* Exposure management
* Settings
* Permissions

![Microsoft Defender XDR portal](screenshots/fundamentals/04-defender-portal.png)

## 5. Review an Existing Custom Role

Navigate to:

**Permissions → Roles → Microsoft Defender XDR**

Open the lab-provided custom role.

Example:

```text
Defender Analyst T1
```

Review the role configuration without modifying it.

![Custom RBAC role](screenshots/fundamentals/05-custom-role.png)

## 6. Review Permission Groups

Review the permission groups assigned to the role.

### Security Operations

Permissions associated with security operations and incident response.

Review the configured permissions using **Edit**.

![Security operations permissions](screenshots/fundamentals/06-security-operations.png)

### Security Posture

Permissions associated with security recommendations, vulnerabilities, remediation tasks, and exceptions.

![Security posture permissions](screenshots/fundamentals/07-security-posture.png)

### Authorization and Settings

Permissions associated with security configuration, settings, and role administration.

![Authorization and settings permissions](screenshots/fundamentals/08-authorization-settings.png)

## 7. Review Role Assignment

Scroll to **Assignments** and select **Edit assignment**.

Review:

* Assignment name
* Assigned users or groups
* Data sources
* Defender workloads covered by the assignment

![RBAC assignment](screenshots/fundamentals/09-role-assignment.png)

## 8. Review Data Source Scope

Inspect which Defender data sources are included in the assignment.

The assignment can be scoped so that the same role provides different access depending on the assigned data sources.

Example:

```text
Defender Analyst Role
        │
        ├── Assignment A
        │     └── Multiple Defender data sources
        │
        └── Assignment B
              └── Endpoint data sources only
```

![RBAC data sources](screenshots/fundamentals/10-data-sources.png)

## 9. RBAC Configuration Model

The configuration reviewed in this lab follows:

```text
Defender XDR
      ↓
Unified RBAC
      ↓
Role
      ↓
Permission Groups
      ↓
Assignment
      ↓
Users / Groups
      ↓
Data Sources
```

This separates the definition of permissions from the users and data-source scope to which those permissions are assigned.

## Validation

* [ ] Defender XDR permissions page accessed.
* [ ] Available workloads reviewed.
* [ ] Required workloads activated where applicable.
* [ ] Workload settings reviewed.
* [ ] Custom role reviewed.
* [ ] Security Operations permissions reviewed.
* [ ] Security Posture permissions reviewed.
* [ ] Authorization and Settings permissions reviewed.
* [ ] Role assignment reviewed.
* [ ] Data-source scope reviewed.

## Result

Microsoft Defender XDR Unified RBAC was configured/reviewed to demonstrate centralized permission management across Defender workloads.

The lab demonstrates how roles, permission groups, assignments, users/groups, and data-source scope combine to implement least-privilege access.

> Portfolio note: replace lab-specific role names, usernames, tenant information, and other environment-specific values where necessary
