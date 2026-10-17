# Azure Cloud Penetration Testing

## Overview

This directory contains practical Azure cloud security projects focused on cloud security assessment, DevSecOps principles, identity and access management, virtual machine security, and investigation of Azure resources.

The projects document hands-on learning through structured investigations, technical notes, evidence collection, and security recommendations. The goal is to understand how Azure configurations and permissions affect security and how defenders can identify, assess, and mitigate potential risks.

## Objectives

- Understand common security risks in Microsoft Azure environments.
- Explore DevSecOps principles and security integration throughout the development lifecycle.
- Examine Azure role-based access control (RBAC), managed identities, and permission scopes.
- Investigate virtual machine configurations and VM extension security implications.
- Develop structured cloud investigation and evidence-documentation skills.
- Recommend security improvements based on verified findings and least-privilege principles.

## Projects and Case Studies

### 02. Azure DevSecOps

**Project:** [Azure DevSecOps](./02-Azure%20DevSecOps/)

**Focus:** Understanding how security practices can be integrated into development and deployment workflows in Azure environments.

**Key Learning Areas:**
- DevSecOps principles and security throughout the software development lifecycle.
- Azure security controls and configuration review.
- Identification of potential security weaknesses in development and deployment workflows.
- Secure configuration and access management.
- Security validation and remediation planning.

### 03. Azure Virtual Machine Privilege Escalation — Case 002

**Report:** [Azure Virtual Machine Privilege Escalation — Case 002](./03-Azure%20Virtual%20Machine%20Privilege%20Escalation%20%28case%20002.md)

**Focus:** Investigating Azure virtual machine permissions and privilege-escalation risks, with attention to managed identities, RBAC assignments, permission scopes, and VM management capabilities.

**Key Learning Areas:**
- Azure RBAC roles, assignments, and scopes.
- System-assigned managed identities and their effective permissions.
- Virtual machine management capabilities and associated security risks.
- Least privilege and excessive-permission risk assessment.
- Investigation evidence, findings, and mitigation recommendations.

### 04. Azure Cloud Security Investigation — Case 001

**Report:** [Azure Cloud Security Investigation — Case 001](./04-Azure%20Cloud%20Security%20Investigation%20%28case%20001.md)

**Focus:** Assessing Azure cloud security activity and configurations to identify potential weaknesses, review access controls, and document evidence-based findings.

**Key Learning Areas:**
- Azure resource discovery and security posture review.
- Identity and access management (IAM).
- Review of cloud configurations and permission assignments.
- Investigation methodology and evidence collection.
- Risk assessment, remediation priorities, and defensive recommendations.

### 05. Azure VM and Extension Investigation — Case 003

**Report:** [Azure VM and Extension Investigation — Case 003](./05-Azure%20VM%20and%20Extension%20Investigation%20%28case%20003.md)

**Focus:** Examining Azure virtual machines and VM extensions to understand their purpose, configuration, management permissions, and potential security implications.

**Key Learning Areas:**
- Azure VM extensions and their operational purpose.
- VM configuration and extension-related security risks.
- Permissions required to manage virtual machines and extensions.
- Review of available configuration and activity evidence.
- Secure VM management, hardening, and least-privilege recommendations.

## Investigation Methodology

Projects and case studies follow a structured workflow where applicable:

1. **Define scope:** Identify the lab environment, objectives, and resources being assessed.
2. **Review the environment:** Examine relevant Azure resources, configurations, identities, and permissions.
3. **Collect evidence:** Record relevant observations, logs, command outputs, and screenshots.
4. **Analyze findings:** Assess the security implications of observed configurations or activities.
5. **Document risks:** Explain the potential impact and supporting evidence.
6. **Recommend mitigations:** Propose practical security improvements aligned with Azure security best practices.
7. **Validate conclusions:** Ensure documented findings are supported by evidence from the lab.

## Tools and Technologies

Tools and services may include the following, depending on the individual project:

- Microsoft Azure Portal
- Azure role-based access control (RBAC)
- Azure managed identities
- Azure virtual machines and VM extensions
- Azure CLI
- PowerShell and Bash
- Azure activity and diagnostic logs
- GitHub for technical documentation and version control

Only list tools and services that were actually used in each project.

## Key Skills Demonstrated

- Azure cloud security assessment
- Identity and access management
- RBAC and permission-scope analysis
- Virtual machine security investigation
- Cloud configuration review
- DevSecOps security principles
- Evidence collection and technical reporting
- Risk assessment and remediation planning
- Security documentation and version control

## Evidence and Reporting

Each case study should document the work performed and, where available, include:

- Investigation objectives and scope
- Environment and methodology
- Relevant commands, configurations, or log observations
- Screenshots and other supporting evidence
- Verified findings and security implications
- Recommended mitigations and lessons learned

All screenshots and reports should exclude passwords, access tokens, secret values, personal information, and other sensitive data.

## Responsible Testing

All security testing documented in this directory should be conducted in authorized lab environments or against resources for which permission has been granted.

The purpose of these projects is to strengthen cloud security knowledge, improve defensive understanding, and develop responsible investigation practices.

## Disclaimer

This repository is for educational and professional development purposes. The findings and techniques documented here reflect the specific environments and evidence examined during each project. Results should not be assumed to apply to every Azure deployment.

## Repository Navigation

- [Azure DevSecOps](./02-Azure%20DevSecOps/)
- [Case 002 — Azure Virtual Machine Privilege Escalation](./03-Azure%20Virtual%20Machine%20Privilege%20Escalation%20%28case%20002.md)
- [Case 001 — Azure Cloud Security Investigation](./04-Azure%20Cloud%20Security%20Investigation%20%28case%20001.md)
- [Case 003 — Azure VM and Extension Investigation](./05-Azure%20VM%20and%20Extension%20Investigation%20%28case%20003.md)

---
