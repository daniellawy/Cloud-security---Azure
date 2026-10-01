# KQL Fundamentals — Core Operators

## Objective

Use core KQL operators to filter, select, transform, sort, and aggregate security telemetry.

## Environment

* Microsoft Sentinel
* Log Analytics Workspace
* KQL

---

## 1. `where` — Filter Events

Filter events based on a specific condition.

```kql
SigninLogs
| where ResultType != 0
```

**Purpose:** Identify failed sign-in events.

![KQL where operator](../screenshots/fundamentals/01-where.png)

---

## 2. `project` — Select Columns

Return only the fields required for investigation.

```kql
SigninLogs
| project TimeGenerated, UserPrincipalName, IPAddress, ResultDescription
```

**Purpose:** Reduce the result set to relevant authentication fields.

![KQL project operator](../screenshots/fundamentals/02-project.png)

---

## 3. `extend` — Create Calculated Fields

Create a new column from existing data.

```kql
SigninLogs
| extend SignInResult = tostring(ResultDescription)
| project TimeGenerated, UserPrincipalName, SignInResult
```

**Purpose:** Create derived fields for analysis.

![KQL extend operator](../screenshots/fundamentals/03-extend.png)

---

## 4. `sort` — Order Results

Sort events by timestamp.

```kql
SigninLogs
| sort by TimeGenerated desc
```

**Purpose:** Display the newest events first.

![KQL sort operator](../screenshots/fundamentals/04-sort.png)

---

## 5. `summarize` — Aggregate Events

Count failed sign-ins by user.

```kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count()
    by UserPrincipalName
| sort by FailedAttempts desc
```

**Purpose:** Identify accounts with high numbers of failed authentication attempts.

![KQL summarize operator](../screenshots/fundamentals/05-summarize.png)

---

## 6. `distinct` — Identify Unique Values

Return unique source IP addresses.

```kql
SigninLogs
| where ResultType != 0
| distinct IPAddress
```

**Purpose:** Identify unique IP addresses associated with failed sign-ins.

![KQL distinct operator](../screenshots/fundamentals/06-distinct.png)

---

## 7. `take` — Limit Results

Return a small sample of events.

```kql
SigninLogs
| take 10
```

**Purpose:** Quickly inspect the structure and available data in a table.

![KQL take operator](../screenshots/fundamentals/07-take.png)

---

## Validation

* [ ] `where` query executed
* [ ] `project` query executed
* [ ] `extend` query executed
* [ ] `sort` query executed
* [ ] `summarize` query executed
* [ ] `distinct` query executed
* [ ] `take` query executed

## Result

Core KQL operators were used to filter, select, transform, sort, sample, and aggregate security telemetry for investigation.

