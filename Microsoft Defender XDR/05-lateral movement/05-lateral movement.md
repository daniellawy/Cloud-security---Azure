# 05 — Lateral Movement

## Objective

Investigate a Microsoft Defender XDR incident involving a hands-on-keyboard attack from a compromised account and validate the detected lateral movement activity.

## 1. Locate the Incident

Navigate to:

**Investigation & response → Incidents & alerts → Incidents**

Set the time range to **6 months** and locate:

**Hands-on keyboard attack was launched from a compromised account (attack disruption)**

Open the incident.

![Lateral movement incident](screenshots/01-lateral-movement-incident.png)

## 2. Review Incident Graph

Review the incident graph to identify the entities associated with the attack.

The graph was used to review:

* Processes
* Registry values
* User accounts
* IP addresses
* Files
* Devices and other related entities

![Incident graph](screenshots/02-incident-graph.png)

## 3. Replay the Attack Story

Open the **Attack story** and select **Play attack story**.

The attack story was used to review the sequence of activity and observe how the attack scope expanded across the associated entities.

The graph provided a visual relationship between:

* Source activity
* User accounts
* Devices
* Alerts
* Other affected entities

![Attack story](screenshots/03-attack-story.png)

## 4. Review Related Alerts

Open the **Alerts** tab and review the alerts associated with the incident.

Locate:

**Compromised account conducting hands-on-keyboard attack**

Open the alert.

![Related alerts](screenshots/04-related-alert.png)

## 5. Review Alert Timeline

Open the **Alert timeline** tab.

Expand the alert details to inspect the execution context and command associated with the detection.

The investigation focused on:

* Event timestamp
* Process activity
* Command-line context
* Account involved
* Device involved
* Detection status

The exact command is not reproduced in the public documentation.

![Alert timeline](screenshots/05-alert-timeline.png)

## 6. Validate Detection Status

Review the alert metadata to confirm the state of the detection.

| Field            | Result                                                  |
| ---------------- | ------------------------------------------------------- |
| Alert            | Compromised account conducting hands-on-keyboard attack |
| Status           | New                                                     |
| Detection status | Detected                                                |
| Activity         | Suspicious lateral movement                             |
| Account          | `<USER_ACCOUNT>`                                        |
| Device           | `<DEVICE_NAME>`                                         |

![Detection status](screenshots/06-detection-status.png)

## 7. Review Incident Assets

Return to the incident and open the **Assets** tab.

Review the devices and user accounts associated with the incident.

![Incident assets](screenshots/07-incident-assets.png)

## 8. Review Device Response Actions

Open the device details pane for an affected asset.

Review the available response actions associated with the device.

The available actions provide options for investigating and responding to suspicious endpoint activity.

No containment or remediation action is documented here unless it was actually performed.

![Device response actions](screenshots/08-device-response-actions.png)

## Investigation

The investigation followed the attack path exposed by Defender XDR:

```text
Compromised account
        ↓
Hands-on-keyboard activity
        ↓
Suspicious command execution
        ↓
Lateral movement detection
        ↓
Affected devices / entities
```

The **Attack story** was used to understand the broader incident scope, while the alert timeline provided the execution-level context for the lateral movement detection.

## Result

Microsoft Defender XDR was used to investigate a hands-on-keyboard attack originating from a compromised account.

The investigation reviewed the incident graph and attack story, identified the associated lateral movement alert, examined its timeline and command context, confirmed the detection status, and reviewed the affected assets and available device response actions.
