# KQL — Detection Engineering

## Objective

Develop and validate KQL detection logic for Microsoft Sentinel analytics rules.

## Detection Workflow

```text
Security Telemetry
        ↓
KQL Detection Query
        ↓
Filter / Aggregate
        ↓
Detection Result
        ↓
Microsoft Sentinel Analytics Rule
        ↓
Incident
```

## 1. Detect Repeated Failed Sign-Ins

Identify accounts generating repeated authentication failures within a short period.

```kql id="q7v2kp"
SigninLogs
| where ResultType != 0
| summarize
    FailedAttempts = count(),
    SourceIPs = make_set(IPAddress, 10)
    by UserPrincipalName, bin(TimeGenerated, 15m)
| where FailedAttempts >= 5
| project
    TimeGenerated,
    UserPrincipalName,
    FailedAttempts,
    SourceIPs
| order by TimeGenerated desc
```

![Failed sign-in detection](../screenshots/detection/01-failed-signins.png)

## 2. Detect Suspicious PowerShell Execution

Identify PowerShell processes using command-line indicators associated with encoded or obfuscated execution.

```kql id="k6c8xw"
DeviceProcessEvents
| where FileName =~ "powershell.exe"
| where ProcessCommandLine has_any (
    "-EncodedCommand",
    "-enc",
    "FromBase64String"
)
| project
    Timestamp,
    DeviceName,
    AccountName,
    ProcessCommandLine,
    InitiatingProcessFileName
| order by Timestamp desc
```

![PowerShell detection](../screenshots/detection/02-powershell-detection.png)

## 3. Detect PowerShell Network Activity

Identify network connections initiated by PowerShell.

```kql id="w2n5sa"
DeviceNetworkEvents
| where InitiatingProcessFileName =~ "powershell.exe"
| summarize
    ConnectionCount = count(),
    RemoteIPs = make_set(RemoteIP, 20),
    RemotePorts = make_set(RemotePort, 20)
    by DeviceName, InitiatingProcessAccountName, bin(Timestamp, 15m)
| where ConnectionCount > 0
| project
    Timestamp,
    DeviceName,
    InitiatingProcessAccountName,
    ConnectionCount,
    RemoteIPs,
    RemotePorts
| order by Timestamp desc
```

![PowerShell network detection](../screenshots/detection/03-powershell-network.png)

## 4. Detection Validation

Run each query manually before creating the analytics rule.

Validate:

* Query executes without errors.
* Returned events match the intended detection condition.
* Entity fields contain usable values.
* The query does not generate excessive false positives.
* The time window is appropriate for the detection objective.

## 5. Sentinel Analytics Rule Configuration

For a production-style implementation:

* **Rule type:** Scheduled query rule
* **Query:** Validated KQL detection query
* **Frequency:** Defined according to detection requirements
* **Lookup period:** Appropriate to the detection window
* **Trigger:** Create alert when query returns results
* **Severity:** Assigned according to the detection's operational impact
* **Entity mapping:** Map available user, host, IP, or other entities
* **Incident creation:** Enabled when the detection should generate a Sentinel incident

![Analytics rule configuration](../screenshots/detection/04-analytics-rule.png)

## 6. Detection Testing

Generate or identify representative telemetry and execute the detection query.

Confirm:

1. The query returns the expected event.
2. Sentinel generates the corresponding alert.
3. The alert contains the expected entities.
4. The alert is grouped into an incident when configured.
5. The resulting incident can be investigated using the underlying telemetry.

![Detection test result](../screenshots/detection/05-detection-result.png)

## Validation

* [ ] Detection queries execute successfully.
* [ ] Detection logic returns expected results.
* [ ] False-positive conditions were reviewed.
* [ ] Entity mappings were validated.
* [ ] Analytics rule configuration was tested.
* [ ] Alert generation was verified.
* [ ] Incident creation was verified where enabled.

## Result

KQL detection logic was developed, validated, and prepared for deployment as Microsoft Sentinel analytics rules.

> Portfolio note: environment-specific usernames, device names, IP addresses, tenant identifiers, and other sensitive values should be sanitized before publishing screenshots.
