# 06 — Execution

## Objective

Investigate a Microsoft Defender XDR alert involving a script with suspicious content and validate the PowerShell execution activity.

## 1. Locate the Incident

Navigate to:

**Investigation & response → Incidents & alerts → Incidents**

Set the time range to **6 months**.

Locate the related incident and identify the alert:

**A script with suspicious content was observed**

Open the alert page.

![Suspicious script incident](screenshots/01-suspicious-script-incident.png)

## 2. Review Alert Context

Review the alert details to identify the execution context.

The alert page was used to identify:

* Device
* User account
* Execution/event time
* Alert name
* Alert description

![Alert context](screenshots/02-alert-context.png)

## 3. Review Alert Timeline

Open the **Alert timeline** to inspect the specific execution event.

The alert showed:

| Field    | Result                                        |
| -------- | --------------------------------------------- |
| Device   | `<DEVICE_NAME>`                               |
| User     | `<USER_ACCOUNT>`                              |
| Severity | Medium                                        |
| Event    | `powershell.exe` executed a script            |
| Alert    | A script with suspicious content was observed |

![Alert timeline](screenshots/03-alert-timeline.png)

## 4. Review Script Execution Details

Expand the **Remote execution** section to inspect the execution details and suspicious script content.

The investigation reviewed:

* PowerShell execution event
* Script execution timestamp
* Remote execution context
* Suspicious script content

The script content itself is not reproduced in the public documentation.

![Remote execution details](screenshots/04-remote-execution.png)

## 5. Review Available Response Actions

Review the device and alert action menus to identify the available investigation and containment options.

Available actions included:

* Run antivirus scan
* Collect investigation package
* Restrict application execution
* Start automated investigation
* Initiate live response
* Isolate device
* Open Advanced Hunting with **Go hunt**

No remediation or containment action is documented here unless it was actually performed.

![Response actions](screenshots/05-response-actions.png)

## Investigation

The investigation followed the execution chain exposed by Defender XDR:

```text
Affected device
      ↓
User account
      ↓
powershell.exe
      ↓
Script execution
      ↓
Suspicious script content
      ↓
Remote execution context
```

The alert timeline provided the execution-level evidence, while the **Remote execution** details provided additional context for the suspicious script.

## Result

Microsoft Defender XDR was used to investigate a suspicious PowerShell script execution.

The investigation identified the affected device and account, confirmed the `powershell.exe` execution event, reviewed the alert timeline and remote execution details, and examined the available endpoint investigation and containment actions.
