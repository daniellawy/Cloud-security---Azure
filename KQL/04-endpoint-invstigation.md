# KQL — Endpoint Investigation

## Objective

Use KQL to investigate endpoint activity, identify suspicious processes, and correlate process execution with affected devices.

## Data Source

```text
DeviceProcessEvents
```

## 1. Review Recent Process Activity

```kql
DeviceProcessEvents
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    ProcessCommandLine,
    InitiatingProcessFileName
| sort by Timestamp desc
```

Review recent process execution activity across endpoints.

![Recent process activity](../screenshots/endpoint/01-process-activity.png)

---

## 2. Search for a Specific Process

Search for activity associated with a process under investigation.

```kql
DeviceProcessEvents
| where FileName =~ "<PROCESS>"
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    ProcessCommandLine,
    InitiatingProcessFileName
| sort by Timestamp desc
```

Review the process name, command line, initiating process, user, and device.

![Process investigation](../screenshots/endpoint/02-process-investigation.png)

---

## 3. Identify Devices Running the Process

```kql
DeviceProcessEvents
| where FileName =~ "<PROCESS>"
| summarize EventCount = count()
    by DeviceName
| sort by EventCount desc
```

Identify the endpoints where the process was observed.

![Process activity by device](../screenshots/endpoint/03-process-by-device.png)

---

## 4. Investigate Command-Line Activity

Review command-line arguments associated with the process.

```kql
DeviceProcessEvents
| where FileName =~ "<PROCESS>"
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    ProcessCommandLine,
    InitiatingProcessCommandLine
| sort by Timestamp desc
```

Command-line data can provide additional context about how a process was executed.

![Process command line](../screenshots/endpoint/04-command-line.png)

---

## 5. Investigate Process Relationships

Review the process that initiated the activity.

```kql
DeviceProcessEvents
| where FileName =~ "<PROCESS>"
| project
    Timestamp,
    DeviceName,
    AccountName,
    FileName,
    InitiatingProcessFileName,
    InitiatingProcessCommandLine
| sort by Timestamp desc
```

Use the parent/initiating process information to determine whether the execution chain requires further investigation.

![Process relationship](../screenshots/endpoint/05-process-relationship.png)

---

## 6. Investigation

Review the collected endpoint activity and determine:

* Which devices executed the process
* Which accounts were associated with the activity
* How the process was launched
* Whether the command line is expected
* Whether the initiating process is expected
* Whether additional endpoint investigation is required

Sensitive environment-specific values are intentionally omitted.

## Validation

* [ ] Endpoint process activity reviewed
* [ ] Target process identified
* [ ] Affected devices identified
* [ ] Command-line activity reviewed
* [ ] Process relationships reviewed
* [ ] Suspicious activity assessed
* [ ] Additional investigation documented when required

## Result

KQL was used to investigate endpoint process execution, identify affected devices, review command-line activity, and analyze process relationships to determine whether further investigation was required.

> **Portfolio note:** Environment-specific usernames, hostnames, IP addresses, tenant information, and other sensitive identifiers should be removed or blurred before screenshots are uploaded.
