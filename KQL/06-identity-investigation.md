# KQL — Identity Investigation

## Objective

Use KQL to investigate identity activity, account behavior, privilege-related events, and potentially suspicious changes to user accounts.

## Data Sources

Common identity-related tables include:

```text
SigninLogs
AuditLogs
IdentityInfo
```

Use the tables available in the connected Microsoft Sentinel or Defender environment.

---

## 1. Review User Sign-In Activity

```kql id="r7h1xk"
SigninLogs
| project
    TimeGenerated,
    UserPrincipalName,
    AppDisplayName,
    IPAddress,
    ResultType,
    ResultDescription
| sort by TimeGenerated desc
```

Review recent authentication activity and identify unusual sign-in behavior.

![User sign-in activity](../screenshots/identity/01-user-signins.png)

---

## 2. Investigate a Specific Account

```kql id="p2m4fz"
SigninLogs
| where UserPrincipalName == "<USER_ACCOUNT>"
| project
    TimeGenerated,
    UserPrincipalName,
    AppDisplayName,
    IPAddress,
    ResultType,
    ResultDescription
| sort by TimeGenerated desc
```

Use this query to investigate authentication activity for a specific account.

![Account investigation](../screenshots/identity/02-account-investigation.png)

---

## 3. Identify Failed Authentication Activity

```kql id="4q8n0v"
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count()
    by UserPrincipalName
| sort by FailedAttempts desc
```

Identify accounts associated with repeated authentication failures.

![Failed authentication by account](../screenshots/identity/03-failed-authentication.png)

---

## 4. Review Identity Audit Activity

```kql id="h7m3ks"
AuditLogs
| project
    TimeGenerated,
    OperationName,
    Category,
    Result,
    InitiatedBy,
    TargetResources
| sort by TimeGenerated desc
```

Review administrative and identity-related operations recorded in the audit logs.

![Identity audit activity](../screenshots/identity/04-audit-activity.png)

---

## 5. Investigate Administrative Changes

Search for operations associated with administrative or privileged activity.

```kql id="n5k2wp"
AuditLogs
| where Category =~ "RoleManagement"
| project
    TimeGenerated,
    OperationName,
    Result,
    InitiatedBy,
    TargetResources
| sort by TimeGenerated desc
```

Review role-management events for unexpected privilege assignments or changes.

![Role management activity](../screenshots/identity/05-role-management.png)

---

## 6. Investigate Account Changes

```kql id="c4r8ys"
AuditLogs
| where Category =~ "UserManagement"
| project
    TimeGenerated,
    OperationName,
    Result,
    InitiatedBy,
    TargetResources
| sort by TimeGenerated desc
```

Review user-management activity such as account or identity changes.

![User management activity](../screenshots/identity/06-user-management.png)

---

## 7. Investigation

Correlate authentication and audit activity to determine whether identity activity is expected.

Review:

* User account
* Authentication timestamps
* Source IP
* Application
* Authentication result
* Administrative operations
* Role or privilege changes
* Account modifications

Determine whether the activity requires additional investigation or escalation.

Sensitive environment-specific values are intentionally omitted.

## Validation

* [ ] User authentication activity reviewed
* [ ] Specific account investigated
* [ ] Failed authentication activity reviewed
* [ ] Identity audit activity reviewed
* [ ] Role-management activity investigated
* [ ] User-management activity investigated
* [ ] Suspicious identity activity assessed

## Result

KQL was used to investigate authentication activity, identity audit events, role-management operations, and account changes to identify potentially suspicious identity behavior.

> **Portfolio note:** Environment-specific usernames, email addresses, IP addresses, tenant information, role names, and other sensitive identifiers should be removed or blurred before screenshots are uploaded.
