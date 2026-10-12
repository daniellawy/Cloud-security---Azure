# KQL — Network Investigation

## Objective

Use KQL to review recent security events, examine logon-related identifiers, identify activity patterns, and investigate records associated with reporting computers.

## Data Source

```text
SecurityEvent_CL
```

## 1. Review Recent Security Activity

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| project
    TimeGenerated,
    SourceComputerId_g,
    EventOriginId_g,
    Type_s,
    LogonGuid_g,
    TargetLogonGuid_g
| sort by TimeGenerated desc
| take 100
```

Review recent security records collected during the last 24 hours.

![Recent security activity](../screenshots/network/01-network-activity.png)

---

## 2. Investigate Logon-Related Identifiers

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| where isnotempty(LogonGuid_g)
    or isnotempty(TargetLogonGuid_g)
| project
    TimeGenerated,
    SourceComputerId_g,
    LogonGuid_g,
    TargetLogonGuid_g
| sort by TimeGenerated desc
| take 100
```

Review events containing logon identifiers for further investigation. These identifiers do not independently establish that a network connection occurred.

![Logon identifier investigation](../screenshots/network/02-logon-identifiers.png)

---

## 3. Review Activity by Source Computer ID

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| summarize
    EventCount = count(),
    FirstSeen = min(TimeGenerated),
    LastSeen = max(TimeGenerated)
    by SourceComputerId_g
| sort by EventCount desc
| take 20
```

Identify source computer IDs associated with the highest number of recorded events.

![Activity by source computer](../screenshots/network/03-activity-by-computer.png)

---

## 4. Identify Frequently Reported Event Types

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| summarize EventCount = count()
    by Type_s
| sort by EventCount desc
```

Compare event volumes by recorded type to identify patterns that may warrant further review.

![Event type summary](../screenshots/network/04-event-types.png)

---

## 5. Review Activity by Event Origin ID

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| summarize
    EventCount = count(),
    FirstSeen = min(TimeGenerated),
    LastSeen = max(TimeGenerated)
    by EventOriginId_g
| sort by EventCount desc
| take 20
```

Identify event origin IDs associated with repeated records. Confirm the meaning of this field in the source data before drawing conclusions about the origin of an event.

![Activity by event origin](../screenshots/network/05-event-origin.png)

---

## 6. Identify Repeated Logon GUIDs

```kql
SecurityEvent_CL
| where TimeGenerated >= ago(24h)
| where isnotempty(LogonGuid_g)
| summarize
    EventCount = count(),
    FirstSeen = min(TimeGenerated),
    LastSeen = max(TimeGenerated)
    by LogonGuid_g
| sort by EventCount desc
| take 20
```

Identify logon GUIDs appearing in multiple records and review their associated events for context.

![Repeated logon identifiers](../screenshots/network/06-logon-frequency.png)

---

## 7. Investigation

Review the available security-event data and correlate records using their timestamps, source computer IDs, event origin IDs, and logon-related identifiers.

Review:

- Event timestamp
- Source computer ID
- Event origin ID
- Recorded event type
- Logon GUID
- Target logon GUID
- Frequency of recorded events
- Whether further investigation is required

**Data limitation:** The supplied `SecurityEvent_CL` schema does not include remote IP addresses, destination ports, protocols, device names, or initiating process details. These queries therefore support security-event review, not direct network-connection analysis. Investigating network destinations and ports requires a data source that contains those fields.

Sensitive environment-specific values are intentionally omitted.

## Validation

- [ ] Recent security events reviewed
- [ ] Logon-related identifiers examined
- [ ] Activity grouped by source computer ID
- [ ] Event type frequencies reviewed
- [ ] Event origin patterns examined
- [ ] Repeated logon GUIDs reviewed
- [ ] Data-source limitations documented
- [ ] Further investigation documented when required

## Result

KQL was used to review recent security events, summarize activity patterns, and examine logon-related identifiers using the columns available in `SecurityEvent_CL`. Direct network-connection analysis remains dependent on additional network telemetry.

> **Portfolio note:** Remove or blur sensitive IP addresses, hostnames, usernames, tenant IDs, GUIDs, resource IDs, and other environment-specific identifiers before publishing screenshots.
