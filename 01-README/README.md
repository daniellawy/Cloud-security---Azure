# Cloud Security Engineering — Azure


Welcome to my **Cloud Security Engineering portfolio**. This repository documents my hands-on learning, technical investigations, detection engineering exercises, and security analysis across the Microsoft Azure ecosystem.

The project brings together Security Information and Event Management (SIEM), threat hunting, log analysis, incident investigation, identity and access management, cloud penetration-testing concepts, and DevSecOps.

My objective is to develop the practical skills required to investigate security events, understand cloud attack paths, identify misconfigurations, develop detection logic, and communicate findings through structured technical documentation.

Rather than treating security as a collection of isolated tools, this portfolio explores how telemetry, identities, permissions, detections, alerts, incidents, and remediation fit together in a defensive security workflow.

**Primary focus:** Cloud Security | SOC Analysis | Blue Team | Threat Detection | Security Engineering

---

## Table of Contents

- [Project Overview](#project-overview)
- [Objectives](#objectives)
- [Technology Stack](#technology-stack)
- [Repository Roadmap](#repository-roadmap)
- [1. Microsoft Sentinel](#1-microsoft-sentinel)
- [2. Kusto Query Language](#2-kusto-query-language-kql)
- [3. Microsoft Defender XDR](#3-microsoft-defender-xdr)
- [4. Azure Cloud Penetration Testing](#4-azure-cloud-penetration-testing)
- [5. Security Investigations](#5-security-investigations)
- [Investigation Methodology](#investigation-methodology)
- [Core Security Concepts](#core-security-concepts)
- [Skills Demonstrated](#skills-demonstrated)
- [Evidence and Documentation](#evidence-and-documentation)
- [Learning Roadmap](#learning-roadmap)
- [Responsible Use](#responsible-use)

---

## Project Overview

Cloud adoption introduces security challenges that extend beyond traditional endpoint and network protection. Misconfigured permissions, excessive privileges, incomplete logging, suspicious authentication, and insecure workload configurations can all increase an organization's exposure to attack.

This portfolio explores these challenges through practical exercises and documented investigations involving Microsoft security technologies.

The repository is organized into five main technical areas:

| Area | Purpose |
|---|---|
| Microsoft Sentinel | SIEM configuration, log ingestion, KQL investigations, analytics rules, alerts, incidents, workbooks, and automation |
| KQL | Query development, authentication analysis, endpoint and network investigation, identity analysis, threat hunting, and detection engineering |
| Microsoft Defender XDR | Investigation of attack techniques and defensive security scenarios |
| Azure Cloud Penetration Testing | Authorized cloud-security testing concepts and DevSecOps |
| Security Investigations | Structured case studies documenting security questions, evidence, findings, and remediation |

Together, these areas represent the workflow I am learning to follow: understand the environment, examine available evidence, investigate suspicious behaviour, assess risk, and recommend improvements.

**Portfolio principle:** Every technical conclusion should be supported by the available evidence, and every investigation should document its limitations.

## Objectives

The project is designed to help me:

1. Build practical experience with Microsoft Sentinel and Azure security monitoring.
2. Develop KQL skills for querying, filtering, aggregating, and investigating security telemetry.
3. Understand how data connectors and log tables affect detection and investigation capabilities.
4. Learn how detection rules, alerts, incidents, and investigation workflows relate to one another.
5. Investigate identity-related activity, endpoint events, network behaviour, and suspicious execution patterns where the required telemetry is available.
6. Understand Microsoft Defender XDR investigation concepts and common adversary techniques.
7. Analyze Azure identity permissions, resource configurations, and potential cloud attack paths.
8. Document security findings clearly and recommend appropriate defensive controls.
9. Develop a portfolio that demonstrates practical learning and supports progression toward SOC analyst, blue-team, cloud security, and security engineering roles.

---

## Technology Stack

| Technology | Role in the portfolio |
|---|---|
| Microsoft Azure | Cloud environment, resources, identities, and access controls |
| Microsoft Sentinel | SIEM concepts, monitoring, detection, and incident workflows |
| Azure Monitor and Log Analytics | Log collection, table inspection, and telemetry analysis |
| Kusto Query Language (KQL) | Security queries, investigations, and detection logic |
| Microsoft Defender XDR | Cross-domain security investigation and threat-detection concepts |
| Microsoft Entra ID | Identity and authentication security concepts |
| Azure RBAC | Permission assignments, effective scope, and least-privilege analysis |
| Bash / PowerShell / Azure CLI | Command-line workflows where supported by the relevant environment |
| Git and GitHub | Version control, project documentation, and portfolio development |
| Markdown | Technical reports, investigation notes, and repository documentation |

Tools are listed as part of the portfolio's technical scope. Each project should specify which tools and capabilities were actually used.

---

## Repository Roadmap

The repository is divided into five top-level areas.

### 1. Microsoft Sentinel

[Open the Microsoft Sentinel projects](./microsoft-sentinel/)

A structured learning path covering the SIEM workflow, from environment setup and data ingestion to investigation, detection, and automation.

### 2. KQL

[Open the KQL projects](./KQL/)

A collection of query-development and investigation topics covering authentication, endpoint activity, network events, identities, threat hunting, and detection engineering.

### 3. Microsoft Defender XDR

[Open the Defender XDR projects](./[Microsoft Defender XDR](./Microsoft-Defender-XDR/)

Investigations organized around adversary behaviour and security techniques, including credential access, execution, privilege escalation, lateral movement, and defense evasion.

### 4. Azure Cloud Penetration Testing

[Open the Azure cloud-testing projects](./[Azure Cloud Penetration Testing](./Azure%20cloud%20penetration%20testing/)/)

Authorized cloud-security testing concepts, cloud configuration assessment, and DevSecOps-related learning.


## 1. Microsoft Sentinel

**Directory:** [`microsoft-sentinel/`](./microsoft-sentinel/)

This section follows the typical progression of a SIEM investigation environment, from setup and data collection to detections, incident handling, visualization, and automation.

### Project 01 — Environment Setup

[Open 01-environment-setup](./microsoft-sentinel/01-environment-setup/)

**Purpose:** Document the initial Sentinel and Log Analytics environment.

Topics include:

- Workspace and environment configuration.
- Understanding the relationship between Sentinel and Log Analytics.
- Establishing a baseline for subsequent exercises.
- Recording configuration evidence and setup notes.

**Key files:**
- `README.md` — project overview and setup documentation.
- `notes.md` — supplementary learning notes.
- `screenshots/` — supporting evidence, where available.

### Project 02 — Data Connectors

[Open 02-data-connectors](./microsoft-sentinel/02-data-connectors/)

**Purpose:** Explore how security data is connected to a monitoring environment.

Topics include:

- Understanding data-source requirements.
- Examining connector configuration and collection status.
- Identifying which telemetry is available for investigation.
- Recognizing the impact of missing or incomplete data.

**Key files:**
- `README.md` — project description.
- `connectors.md` — connector notes and documentation.
- `screenshots/` — configuration evidence, where available.

### Project 03 — Log Analytics

[Open 03-log-analytics](./microsoft-sentinel/03-log-analytics/)

**Purpose:** Understand the data available to an analyst before developing queries or detections.

Topics include:

- Table discovery and schema inspection.
- Identifying relevant columns and data types.
- Understanding timestamps and event context.
- Selecting suitable data sources for investigative questions.

**Key files:**
- `README.md` — project overview.
- `tables.md` — table and schema notes.
- `screenshots/` — supporting evidence, where available.

### Project 04 — KQL Investigation

[Open 04-kql-investigation](./microsoft-sentinel/04-kql-investigation/)

**Purpose:** Apply KQL to investigate available security telemetry.

Topics include:

- Filtering and projecting relevant events.
- Aggregating activity across users, IP addresses, and other fields where present.
- Examining authentication and security-event patterns.
- Refining queries to improve readability and investigative value.
- Interpreting results in context.

**Key files:**
- `README.md` — investigation methodology.
- `queries.kql` — saved query examples.
- `screenshots/` — query results and supporting evidence, where available.

### Project 05 — Analytics Rules

[Open 05-analytics-rules](./microsoft-sentinel/05-analytics-rules/)

**Purpose:** Explore how query logic can support repeatable security detection.

Topics include:

- Detection objectives and hypotheses.
- KQL-based detection logic.
- Rule configuration and scheduling concepts.
- False-positive considerations.
- Detection limitations and tuning.

**Key files:**
- `README.md` — project overview.
- `detection-rules.md` — documented detection logic.
- `screenshots/` — rule configuration evidence, where available.

### Project 06 — Alerts

[Open 06-alerts](./microsoft-sentinel/06-alerts/)

**Purpose:** Understand how detection outputs become alerts that require analyst attention.

Topics include:

- Alert review and triage.
- Examining alert context and supporting evidence.
- Distinguishing a detection signal from a confirmed security incident.
- Identifying additional information needed to validate an alert.

**Key files:**
- `README.md` — alert investigation notes.
- `screenshots/` — supporting evidence, where available.

### Project 07 — Incidents

[Open 07-incidents](./microsoft-sentinel/07-incidents/)

**Purpose:** Examine how related alerts and evidence can be managed as a security incident.

Topics include:

- Incident review and prioritization.
- Assessing scope and potential impact.
- Recording investigation progress.
- Understanding incident status and response workflows.

**Key files:**
- `README.md` — incident-management documentation.
- `screenshots/` — supporting evidence, where available.

### Project 08 — Investigations

[Open 08-investigations](./microsoft-sentinel/08-investigations/)

**Purpose:** Develop a structured approach to following evidence from an initial alert or investigative question.

Topics include:

- Establishing a working hypothesis.
- Examining related events and entities.
- Correlating available evidence.
- Recording findings and investigative limitations.
- Identifying next steps.

**Key files:**
- `README.md` — investigation workflow and notes.
- `screenshots/` — supporting evidence, where available.

### Project 09 — Workbooks

[Open 09-workbooks](./microsoft-sentinel/09-workbooks/)

**Purpose:** Explore how security telemetry can be summarized and presented for investigation and monitoring.

Topics include:

- Visualizing security activity.
- Summarizing trends and event counts.
- Improving the presentation of investigative results.
- Supporting monitoring and operational review.

**Key file:** `README.md`

### Project 10 — Automation

[Open 10-automation](./microsoft-sentinel/10-automation/)

**Purpose:** Study automation concepts that support consistent security operations.

Topics include:

- Repetitive investigation workflows.
- Automation and response concepts.
- Playbook design considerations.
- Approval, permissions, and safeguards for automated actions.

**Key file:** `README.md`

---

## 2. Kusto Query Language (KQL)

**Directory:** [`KQL/`](./KQL/)

KQL is central to investigating security telemetry in Azure Monitor, Log Analytics, and supported Microsoft security environments.

This section organizes query development by investigative domain.

### [Fundamentals](./KQL/fundamentals/)

Core query syntax, filtering, projection, sorting, aggregation, time ranges, and data exploration.

### [Authentication](./KQL/authentication-investigation/)

Authentication-event analysis, sign-in patterns, account activity, and risk-related metadata where available.

### [Endpoint Investigation](./KQL/endpoint-investigation/)

Investigation of process execution and endpoint events when suitable endpoint telemetry is available.

### [Network Investigation](./KQL/network-investigation/)

Analysis of network-related events, connections, and communication patterns where the data source contains the required fields.

### [Identity Investigation](./KQL/identity-investigation/)

Investigation of identity activity, account relationships, authentication context, and access-related events.

### [Threat Hunting Investigation](./KQL/threat-hunting-investigation/)

Hypothesis-driven searches for patterns that may indicate suspicious behaviour and warrant further analysis.

### [Detection Engineering](./KQL/detection-engineering/)

Development and refinement of query logic intended to identify security-relevant activity.

**Important:** Table names and fields vary between Azure Log Analytics and Defender XDR Advanced Hunting. Queries should be validated against the actual environment and schema before use.

---

## 3. Microsoft Defender XDR

**Directory:** [`defender-xdr/`](./defender-xdr/)

This section organizes security investigation topics around common adversary tactics and techniques.

The objective is to understand how defenders recognize suspicious behaviour, investigate available evidence, and determine appropriate response measures.

### [Defense Evasion](./defender-xdr/defense-evasion/)

Explores behaviours intended to avoid security controls or reduce visibility.

### [Privilege Escalation](./defender-xdr/privilege-escalation/)

Examines how excessive permissions or security weaknesses can allow access to capabilities beyond those initially available.

### [Lateral Movement](./defender-xdr/lateral-movement/)

Focuses on the concept of movement between systems or resources and the evidence that may help defenders investigate it.

### [Execution](./defender-xdr/execution/)

Covers the investigation of process execution and related telemetry where supported by the available data.

### [Credential Access](./defender-xdr/credential-access/)

Examines activity associated with credential-access techniques, including the investigation of Mimikatz-related alerts and process evidence where present.

**Featured project:** [Credential Access — Mimikatz Detection](./defender-xdr/credential-access/07-credential-access.md)

This investigation focuses on reviewing security alerts, examining process-related evidence, documenting findings, and considering defensive responses.

The report and screenshots should reflect the evidence actually captured during the lab.

---

## 4. Azure Cloud Penetration Testing

**Directory:** [`azure-cloud-penetration-testing/`](./azure-cloud-penetration-testing/)

This section focuses on understanding cloud-security weaknesses, access boundaries, and the defensive implications of misconfigured resources in authorized training environments.

### [DevSecOps](./azure-cloud-penetration-testing/devsecops/)

Explores the integration of security into development and operational processes.

Topics may include secure configuration, permissions, security checks, and reducing risk throughout the development lifecycle.

### [Cloud Testing](./azure-cloud-penetration-testing/cloud-testing/)

Documents authorized cloud-security testing concepts and the assessment of cloud resources, identities, configurations, and access controls.

A well-documented assessment should establish its scope, describe the evidence collected, explain the potential impact of a finding, and recommend remediation.

---

## 5. Security Investigations

**Directory:** [`investigations/`](./investigations/)

The case-study section brings together security questions, technical evidence, findings, and remediation recommendations.

Each case should be independently understandable and should distinguish confirmed observations from hypotheses.

### [Case 001 — Azure Cloud Security Investigation](./investigations/case-001%20Azure%20Cloud%20Security%20Investigation/)

**Focus:** Azure cloud-security investigation.

This case is intended to document the investigation of an Azure security scenario, including the environment, available evidence, relevant identities or resources, findings, and recommended defensive improvements.

### [Case 002 — Azure Virtual Machine Privilege Escalation](./investigations/case-002%20Azure%20Virtual%20Machine%20Privilege%20Escalation/)

**Focus:** Managed identities, Azure RBAC, role-assignment scope, and virtual-machine security.

This case examines how an over-privileged identity may create risk beyond its originating workload. The investigation should establish the actual permissions, scope, and demonstrated impact in the authorized lab rather than assume an attack path.

Key learning areas include:

- Understanding system-assigned managed identities.
- Reviewing Azure role assignments.
- Assessing permission scope.
- Evaluating least-privilege requirements.
- Documenting potential privilege-escalation paths.
- Recommending tighter access controls and monitoring.

### [Case 003 — Azure VM and Extension Investigation](./investigations/case-003%20Azure%20VM%20and%20Extension%20Investigation/)

**Focus:** Azure virtual-machine management and extension-related security considerations.

This case is intended to document how VM-management capabilities and extension configuration may affect the security of a cloud workload.

Areas of analysis include the relevant resource configuration, identity and permission requirements, observed behaviour, potential impact, and defensive controls.

The final report should distinguish the lab's demonstrated behaviour from general security implications.

---

## Investigation Methodology

Across the portfolio, I aim to apply a consistent investigation process.

### 1. Define the security question

Identify the objective, relevant environment, scope, and expected outcome.

### 2. Establish available visibility

Inspect the data sources, tables, schemas, resources, and configuration evidence available to the investigation.

### 3. Collect and analyze evidence

Use appropriate queries and investigation tools to filter events, identify patterns, and develop a clearer understanding of the scenario.

### 4. Validate the hypothesis

Check whether the evidence supports the initial assessment. Investigative leads should not be presented as confirmed malicious activity without sufficient evidence.

### 5. Assess impact

Explain how the observed behaviour or configuration could affect confidentiality, integrity, availability, identity security, or cloud-resource control.

### 6. Recommend remediation

Identify practical improvements such as least privilege, narrower role scopes, stronger monitoring, configuration hardening, and improved detection coverage.

### 7. Document the outcome

Record the methodology, evidence, findings, limitations, and recommended next steps.

---

## Core Security Concepts

The repository brings together several connected defensive security principles.

**Identity is a security boundary.** Accounts, workload identities, and service principals require appropriate access controls.

**Permissions determine impact.** Excessive privileges may allow a compromised identity to affect resources beyond its intended responsibilities.

**Logging supports investigation.** Effective analysis depends on collecting relevant telemetry and understanding its schema, coverage, and limitations.

**Detection requires context.** A query result or alert is a signal to investigate, not automatic proof of compromise.

**Remediation should address root causes.** Improving permissions, configurations, and monitoring can reduce the likelihood or impact of similar issues.

**Documentation supports reproducibility.** Clear technical reports allow others to understand the reasoning behind findings and recommendations.

---

## Skills Demonstrated

This portfolio is intended to demonstrate practical development in the following areas:

- Cloud security concepts and Azure resource assessment.
- SIEM workflows and security monitoring.
- KQL query development and log analysis.
- Authentication and identity investigation.
- Detection engineering concepts.
- Alert triage and incident investigation.
- Managed identity and RBAC analysis.
- Cloud attack-path assessment in authorized labs.
- Technical writing and evidence-based reporting.
- Security remediation and least-privilege recommendations.
- GitHub-based project organization and version-controlled documentation.

The strength of each skill claim depends on the corresponding project's completed work and available evidence.

---

## Evidence and Documentation Standards

Each project should include the artefacts appropriate to its objective.

| Artefact | Purpose |
|---|---|
| `README.md` | Project objective, scope, methodology, findings, and lessons learned |
| `.kql` files | Reusable and documented KQL queries |
| Notes and reference files | Supporting explanations and technical observations |
| `screenshots/` | Genuine, relevant evidence captured during the exercise |
| Detection documentation | Detection purpose, logic, assumptions, and limitations |
| Remediation section | Recommended actions and their security rationale |

Not every project requires every artefact. Files should be included when they add value and should not imply work that has not been completed.

Before publishing, sensitive values such as passwords, tokens, keys, and secret contents should be removed or redacted.

---

## Learning Roadmap

This repository is a record of continuous technical development.

The current structure supports learning across:

1. SIEM environment setup and log collection.
2. KQL fundamentals and security investigations.
3. Detection logic, alerts, and incident workflows.
4. Defender XDR investigation concepts.
5. Azure identity, RBAC, and cloud-resource security.
6. Cloud-security case studies and DevSecOps concepts.
7. Evidence-based reporting and remediation.

As the portfolio grows, I intend to improve query quality, investigation depth, documentation consistency, and the evidence supporting each finding.

---

## Responsible Use

All security testing should remain within explicitly authorized environments, including designated training labs.

This portfolio is intended for educational, defensive, and professional development purposes. Cloud-testing exercises should follow the applicable lab rules and scope.

Published reports should accurately represent what was tested, observed, and verified. Lab results should not be presented as production incidents, and missing evidence should not be described as completed validation.

---

## About This Portfolio

I am building this repository to strengthen my practical understanding of cloud security, security operations, threat detection, and defensive security engineering.

Each project is an opportunity to improve my ability to investigate technical problems, reason from evidence, document findings, and recommend security improvements.

**Thank you for reviewing my work.**

Feedback and suggestions for improving the technical quality of these investigations are welcome.

[Explore the repository](https://github.com/daniellawy/Cloud-security---Azure)
