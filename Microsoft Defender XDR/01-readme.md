# Microsoft Defender XDR — Fundamentals

## Objective

Use Microsoft Defender XDR to review security telemetry, investigate alerts, analyze incidents, and correlate activity across identity, endpoint, email, and cloud workloads.

## Environment

* Microsoft Defender XDR
* Microsoft Defender portal
* Connected Microsoft security services
* Microsoft Entra ID
* Microsoft Defender for Endpoint

## 1. Open Microsoft Defender XDR

Open the Microsoft Defender portal and verify access to the security operations workspace.

Review:

* Incidents & alerts
* Advanced hunting
* Devices
* Identities
* Evidence & response

![Microsoft Defender XDR dashboard](../screenshots/fundamentals/01-defender-dashboard.png)

## 2. Review Incidents

Open **Incidents & alerts** and review the available incidents.

For a selected incident, inspect:

* Incident severity
* Incident status
* Alert count
* Affected devices
* Affected users
* Evidence
* Attack techniques
* Incident timeline

![Defender XDR incident](../screenshots/fundamentals/02-incident.png)

## 3. Investigate an Alert

Open an alert associated with the incident.

Review:

* Detection name
* Detection source
* Timestamp
* Device
* User
* Process
* Command line
* Network indicators
* Related evidence

![Defender XDR alert](../screenshots/fundamentals/03-alert.png)

## 4. Review Incident Entities

Inspect the entities associated with the incident.

Typical entities include:

```text
User
  ↓
Device
  ↓
Process
  ↓
File
  ↓
Network Connection
```

Use the entity information to correlate activity across the investigation.

![Incident entities](../screenshots/fundamentals/04-entities.png)

## 5. Review Advanced Hunting

Open **Advanced hunting** and execute a basic endpoint query.

```kql
DeviceProcessEvents
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    ProcessCommandLine
| sort by Timestamp desc
| take 50
```

![Advanced hunting](../screenshots/fundamentals/05-advanced-hunting.png)

## 6. Investigation Workflow

The Defender XDR investigation workflow used in this lab is:

```text
Incident
   ↓
Alert
   ↓
Entities
   ↓
Evidence
   ↓
Advanced Hunting
   ↓
Correlation
   ↓
Response / Escalation
```

## Validation

* [ ] Defender XDR portal accessible.
* [ ] Incidents reviewed.
* [ ] Alert details inspected.
* [ ] Incident entities identified.
* [ ] Advanced Hunting query executed.
* [ ] Endpoint telemetry returned results.

## Result

Microsoft Defender XDR was used to review incidents, inspect alerts and entities, correlate security telemetry, and perform endpoint investigation through Advanced Hunting.

> Portfolio note: sanitize tenant names, usernames, device names, IP addresses, email addresses, and other environment-specific identifiers before publishing screenshots.
