# KQL Fundamentals — Core Operators

## Objective

Use core KQL operators to filter, select, transform, sort, and aggregate security telemetry.

## Environment

- Microsoft Sentinel
- Log Analytics Workspace
- KQL

---

## 1. `where` — Filter Events

Filter events based on a specific condition.

```kql
SecurityEvent
| where TimeGenerated > ago(3h)
```

**Purpose:** Identify events within a specified time range.

![KQL where operator](screenshots/01-where.png)

---


## 2. `sort` — Order Results

Filter virtual machine connection events by computer and remote country, then sort the results by process name.

```kql
VMConnection
| where Computer == "DC11.na.contosohotels.com"
| where RemoteCountry == "France"
| order by ProcessName asc
```

**Purpose:** Organize matching connection events by process name in ascending order.

![KQL sort operator](screenshots/03-sort.png)

---

## 3. `summarize` — Aggregate Events

Count failed sign-ins by user.

```kql
SecurityEvent
| where ResultType != 0
| summarize FailedAttempts = count()
    by UserPrincipalName
| sort by FailedAttempts desc
```

**Purpose:** Identify accounts with high numbers of failed authentication attempts.

---


## 4. `take` — Limit Results

Return a small sample of events.

```kql
SecurityEvent
| take 10
```

**Purpose:** Quickly inspect the structure and available data in a table.

![KQL take operator](screenshots/07-take.png)

---

## Validation

- [ ] `where` query executed
- [ ] `project` query executed
- [ ] `extend` query executed
- [ ] `sort` query executed
- [ ] `summarize` query executed
- [ ] `distinct` query executed
- [ ] `take` query executed

## Result

Core KQL operators were used to filter, select, transform, sort, sample, and aggregate security telemetry for investigation.
