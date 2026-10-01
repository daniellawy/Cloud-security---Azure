# Microsoft Sentinel — Analytics Rules

## Objective

Create and configure Microsoft Sentinel analytics rules to detect suspicious activity and generate security alerts.

## 1. Create Analytics Rule

```text
Microsoft Sentinel
→ Analytics
→ Create
→ Scheduled query rule
```

## 2. Detection Query

Example detection for repeated failed sign-ins:

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts=count() 
    by UserPrincipalName, IPAddress, bin(TimeGenerated, 15m)
| where FailedAttempts >= 5
```

## 3. Rule Configuration

```text
Rule type:
Scheduled query rule

Frequency:
Every 5 minutes

Lookup period:
15 minutes

Trigger:
Results > 0

Severity:
Medium
```

## 4. Entity Mapping

Map investigation entities from the query results:

```text
Account
→ UserPrincipalName

IP
→ IPAddress
```

## 5. Incident Creation

Configure the rule to:

```text
Create an alert
        ↓
Create an incident
        ↓
Assign severity
        ↓
Make incident available for SOC triage
```

## Validation

* [ ] Analytics rule created
* [ ] KQL query validated
* [ ] Schedule configured
* [ ] Entity mapping configured
* [ ] Incident creation enabled
* [ ] Rule enabled
* [ ] Alert/incident generation verified

## Result

```text
Security Telemetry
        ↓
KQL Detection
        ↓
Analytics Rule
        ↓
Alert
        ↓
Incident
        ↓
SOC Investigation
```
