# 03 — Defense Evasion

## Objective

Investigate a Microsoft Defender XDR incident involving an attempt to turn off Microsoft Defender Antivirus protection.

## Environment

* Microsoft Defender XDR
* Microsoft Defender for Endpoint
* Microsoft Defender Antivirus
* Windows endpoint
* Defender Incidents & Alerts
* Alert Timeline

## 1. Locate the Incident

Navigate to:

**Investigation & response → Incidents & alerts → Incidents**

Set the time range to **6 months** and search for:

```text
Attempt to turn off Microsoft Defender Antivirus protection
```

Open the matching incident.

![Incident search](screenshots/01-incident-search.png)

## 2. Review Incident Details

Review the incident to identify the affected asset and account.

| Field     | Result                                                      |
| --------- | ----------------------------------------------------------- |
| Device    | `<DEVICE_NAME>`                                             |
| User      | `<USER_ACCOUNT>`                                            |
| Severity  | High                                                        |
| Category  | Defense Evasion                                             |
| Detection | Attempt to turn off Microsoft Defender Antivirus protection |

![Incident details](screenshots/02-incident-details.png)

## 3. Review Alert Timeline

Open **Alert timeline** to review the individual events associated with the detection.

The timeline was used to identify:

* Event timestamp
* Process involved
* Initiating process
* Command-line context
* Registry modification
* Original registry value
* Modified registry value

![Alert timeline](screenshots/03-alert-timeline.png)

## 4. Identify the Process Chain

The alert identified the following process relationship:

```text
cmd.exe
    ↓
reg.exe
    ↓
Registry modification
```

`reg.exe` was identified as the process performing the registry operation.

`cmd.exe` was identified as the initiating process.

![Process chain](screenshots/04-process-chain.png)

## 5. Review Registry Modification

The alert details exposed the registry modification associated with the detection.

The following information was reviewed:

* Registry location
* Original value
* New value
* Process responsible for the change
* Initiating process
* Event timestamp

The exact registry command and sensitive registry values are not included in the public documentation.

![Registry modification](screenshots/05-registry-modification.png)

## 6. Review Initiating Process

The initiating process was expanded from the alert timeline to inspect additional execution context.

The investigation reviewed the relationship between:

```text
User
 ↓
cmd.exe
 ↓
reg.exe
 ↓
Registry modification
```

![Initiating process](screenshots/06-initiating-process.png)

## 7. Review Alert Metadata

The detection metadata was reviewed to confirm the classification and severity of the event.

| Field              | Result                                                      |
| ------------------ | ----------------------------------------------------------- |
| Detection          | Attempt to turn off Microsoft Defender Antivirus protection |
| Severity           | High                                                        |
| Tactic             | Defense Evasion                                             |
| Process            | `reg.exe`                                                   |
| Initiating process | `cmd.exe`                                                   |
| Device             | `<DEVICE_NAME>`                                             |
| User               | `<USER_ACCOUNT>`                                            |

![Alert metadata](screenshots/07-alert-metadata.png)

## 8. Review Response Actions

The alert and device action menus were reviewed to identify available investigation and containment capabilities.

Available actions included:

* Collect Investigation Package
* Start Automated Investigation
* Start Live Response
* Isolate device

These capabilities provide additional options for endpoint investigation and containment when malicious activity is confirmed.

![Response actions](screenshots/08-response-actions.png)

## 9. Investigation

The investigation established the following activity:

```text
Microsoft Defender XDR Detection
              ↓
Attempt to modify Defender Antivirus
              ↓
Registry modification
              ↓
reg.exe
              ↓
cmd.exe
              ↓
Affected device / user
```

The alert was categorized under **Defense Evasion**.

The incident was then reviewed for additional occurrences of the same detection to compare the associated activity and identify differences between events.

![Related incidents](screenshots/09-related-incidents.png)

## Result

Microsoft Defender XDR was used to investigate an attempted modification of Microsoft Defender Antivirus protection.

The investigation identified the affected device and user, reviewed the alert timeline, traced the process relationship between `cmd.exe` and `reg.exe`, examined the associated registry modification, and reviewed available endpoint investigation and containment actions.

The investigation demonstrated the use of Defender XDR to analyze a security-control tampering event and correlate process, user, device, and registry activity.
