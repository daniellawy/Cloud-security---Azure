# KQL — Threat Hunting Investigation

## Objective

Use KQL to proactively identify suspicious activity that may not have generated a security alert.

## Data Sources

* `DeviceProcessEvents`
* `DeviceNetworkEvents`
* `SigninLogs`

## 1. Hunt for PowerShell Activity

Review PowerShell execution across endpoints.

```kql
DeviceProcessEvents
| where FileName =~ "powershell.exe"
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    ProcessCommandLine,
    InitiatingProcessFileName
| sort by Timestamp desc
```

Review command-line activity and the initiating process for unusual execution patterns.

![PowerShell activity](../screenshots/threat-hunting/01-powershell-activity.png)

## 2. Hunt for Encoded PowerShell

Search for command-line indicators commonly associated with encoded PowerShell execution.

```kql
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
| sort by Timestamp desc
```

![Encoded PowerShell activity](../screenshots/threat-hunting/02-encoded-powershell.png)

## 3. Hunt for Suspicious Network Connections

Identify network connections initiated by PowerShell.

```kql
DeviceNetworkEvents
| where InitiatingProcessFileName =~ "powershell.exe"
| project
    Timestamp,
    DeviceName,
    InitiatingProcessAccountName,
    RemoteIP,
    RemotePort,
    Protocol,
    InitiatingProcessCommandLine
| sort by Timestamp desc
```

![PowerShell network connections](../screenshots/threat-hunting/03-powershell-network.png)

## 4. Hunt for Repeated Authentication Failures

Identify accounts generating repeated failed sign-ins.

```kql
SigninLogs
| where ResultType != 0
| summarize
    FailedAttempts = count(),
    SourceIPs = make_set(IPAddress, 10)
    by UserPrincipalName
| where FailedAttempts >= 5
| sort by FailedAttempts desc
```

![Repeated authentication failures](../screenshots/threat-hunting/04-failed-signins.png)

## 5. Investigate Authentication Followed by Success

Identify accounts with both failed and successful authentication activity during the investigation period.

```kql
SigninLogs
| summarize
    FailedAttempts = countif(ResultType != 0),
    SuccessfulAttempts = countif(ResultType == 0),
    SourceIPs = make_set(IPAddress, 10)
    by UserPrincipalName
| where FailedAttempts > 0
    and SuccessfulAttempts > 0
| sort by FailedAttempts desc
```

![Authentication pattern](../screenshots/threat-hunting/05-authentication-pattern.png)

## 6. Investigation

For suspicious results:

1. Identify the affected user or device.
2. Review the associated timestamp.
3. Inspect the process or command line.
4. Review related network activity.
5. Correlate authentication activity.
6. Determine whether the activity is expected or suspicious.
7. Escalate confirmed suspicious activity for incident investigation.

## Validation

* [ ] Queries execute successfully.
* [ ] Returned events were reviewed.
* [ ] Suspicious results were investigated.
* [ ] False positives were considered.
* [ ] Relevant findings were correlated with endpoint, network, or identity telemetry.

## Result

KQL was used to proactively hunt for suspicious process execution, encoded PowerShell activity, related network connections, and abnormal authentication patterns.

> Portfolio note: environment-specific usernames, device names, IP addresses, tenant identifiers, and other sensitive values should be sanitized before publishing screenshots.
