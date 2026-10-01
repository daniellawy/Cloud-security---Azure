# 04 — Privilege Escalation

## Objective

Investigate a Microsoft Defender XDR incident involving a detected UAC bypass and validate the detection using alert metadata, suspicious evidence, and the process tree.

## 1. Locate the Incident

Navigate to:

**Investigation & response → Incidents & alerts → Incidents**

Set the time range and locate:

**Multi-stage incident involving Privilege escalation on one endpoint**

Open the incident.

![Privilege escalation incident](screenshots/01-privilege-escalation-incident.png)

## 2. Review Incident Alerts

Open the **Alerts** tab and review the alerts associated with the incident.

Where necessary, remove restrictive filters and locate:

**UAC bypass was detected**

Open the alert.

![Incident alerts](screenshots/02-incident-alerts.png)

## 3. Review MITRE ATT&CK Techniques

Review the alert details pane and open **MITRE ATT&CK Techniques**.

Use **View all techniques** to identify the techniques associated with the detection.

The alert was investigated specifically as a **privilege escalation / UAC bypass** event.

![MITRE ATT\&CK techniques](screenshots/03-mitre-techniques.png)

## 4. Review Suspicious Evidence

Review the **Evidence** section of the alert to identify the entities Defender XDR associated with the detection.

The investigation focused on:

* Suspicious processes
* Associated files or other entities
* User and device context
* Entities contributing to the detection

![Suspicious evidence](screenshots/04-suspicious-evidence.png)

## 5. Validate the Detection with the Process Tree

Open the **Process tree** and trace the execution chain associated with the alert.

The process tree was used to correlate the detected UAC bypass with the processes responsible for the activity.

The investigation checked:

* Parent process
* Child process
* Process execution order
* Associated user/device context
* Processes identified by the alert

![Process tree](screenshots/05-process-tree.png)

## Investigation

The investigation followed this sequence:

```text
Defender XDR Incident
        ↓
UAC bypass detection
        ↓
MITRE ATT&CK technique mapping
        ↓
Suspicious evidence
        ↓
Process tree
        ↓
Detection validation
```

The alert was reviewed as a privilege-escalation event, with the process tree used to validate the execution context identified by Defender XDR.

## Result

Microsoft Defender XDR was used to investigate a multi-stage privilege-escalation incident.

The investigation located the associated **UAC bypass** alert, reviewed its MITRE ATT&CK technique mappings, examined the suspicious entities identified by Defender, and validated the alert using the process tree.
