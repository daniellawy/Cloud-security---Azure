# 07 — Credential Access

## Objective

Investigate a Microsoft Defender XDR password-spraying alert, identify the affected account and device, review the associated execution evidence, and use Advanced Hunting for additional investigation.

## 1. Locate the Password Spraying Alert

Navigate to:

**Investigation & response → Incidents & alerts → Incidents**

Set the time range to **6 months**.

Locate the related incident and identify the **Password spraying** alert.

Open the alert page.

![Password spraying incident](screenshots/01-password-spraying-incident.png)

## 2. Review Alert Context

Review the alert page to identify the entities and activity associated with the password-spraying detection.

The investigation reviewed:

* Device
* User account
* Event timestamps
* Process/event names
* Password-spraying activity

![Password spraying alert](screenshots/02-password-spraying-alert.png)

## 3. Review Alert Timeline

Open the **Alert timeline**.

The alert showed:

| Field     | Result                             |
| --------- | ---------------------------------- |
| Device    | `<DEVICE_NAME>`                    |
| User      | `<USER_ACCOUNT>`                   |
| Severity  | Medium                             |
| Event     | `powershell.exe` executed a script |
| Detection | Password spraying                  |

![Password spraying timeline](screenshots/03-alert-timeline.png)

## 4. Review PowerShell Execution

Expand the **PowerShell.exe executed a script** event to inspect the execution details.

The investigation reviewed the command-line context associated with the event.

The exact command and script content are not reproduced in the public documentation.

![PowerShell execution](screenshots/04-powershell-execution.png)

## 5. Review Password Spraying Evidence

Open the **Password spraying** alert details to review the associated evidence and detection description.

The evidence was used to establish the relationship between the detected activity, affected account, device, and password-spraying alert.

![Password spraying evidence](screenshots/05-password-spraying-evidence.png)

## 6. Review Response Actions

Review the available response actions for the affected device.

Available actions included:

* Run antivirus scan
* Restrict application execution
* Start automated investigation
* Initiate live response
* Isolate device

No remediation or containment action is documented here unless it was actually performed.

![Credential access response actions](screenshots/06-response-actions.png)

## 7. Open Advanced Hunting

From the alert timeline, select **Go hunt** to continue the investigation in Advanced Hunting.

Advanced Hunting was used to broaden the investigation beyond the individual alert and examine activity associated with the affected device.

![Go hunt](screenshots/07-go-hunt.png)

## 8. Run Advanced Hunting Query

In Advanced Hunting, extend the time range as required and run the generated query.

The query was used to review the top events associated with the affected device across available tables.

The investigation focused on identifying additional activity that could support or extend the password-spraying investigation.

![Advanced Hunting results](screenshots/08-advanced-hunting.png)

## Investigation

The investigation followed this sequence:

```text id="k7n4vp"
Password spraying detection
        ↓
Affected account / device
        ↓
Alert timeline
        ↓
PowerShell script execution
        ↓
Alert evidence
        ↓
Advanced Hunting
        ↓
Additional device activity
```

The alert was treated as a credential-access investigation, with Advanced Hunting used to expand visibility beyond the original detection.

## Result

Microsoft Defender XDR was used to investigate a password-spraying event associated with a compromised-account attack.

The investigation identified the affected device and account, reviewed the password-spraying alert and PowerShell execution evidence, examined available response actions, and used **Go hunt** to continue the investigation in Advanced Hunting.
