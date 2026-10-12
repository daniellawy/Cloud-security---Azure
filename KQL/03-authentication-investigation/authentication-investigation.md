# KQL — Account Authentication Investigation

## Objective

Investigate suspicious authentication activity associated with a potentially compromised administrative account and identify affected systems.

## Scenario

A security alert identified suspicious access attempts involving an administrative account.

The investigation focused on:

1. Identifying activity associated with the account
2. Reviewing authentication events
3. Identifying systems associated with the activity
4. Documenting appropriate remediation actions

## Data Source

```text
SecurityEvent_CL
```

## 1. Identify Account Activity

Search for security events associated with the account under investigation.

```kql
SecurityEvent_CL
| where Account_s contains_cs "<ACCOUNT>"
```

Review the `Activity_s` field to identify relevant or suspicious activity.

![Account security events](../screenshots/authentication/01-account-events.png)

---

## 2. Investigate Authentication Events

Filter the account activity to logon and logoff events.

```kql
SecurityEvent_CL
| where Account_s contains_cs "<ACCOUNT>"
| where Activity_s contains "logged on"
    or Activity_s contains_cs "logged off"
```

Review the event timestamps and available event details.

![Authentication events](../screenshots/authentication/02-authentication-events.png)

---

## 3. Identify Affected Systems

Aggregate authentication events by computer.

```kql
SecurityEvent_CL
| where Account_s contains_cs "<ACCOUNT>"
| where Activity_s contains "logged on"
    or Activity_s contains_cs "logged off"
| summarize EventCount = count() by Computer
| order by Computer
```

Use the results to identify systems associated with the account's authentication activity.

![Authentication events by system](../screenshots/authentication/03-authentication-by-system.png)

---

## 4. Investigation

Compare the identified systems and authentication activity against the account's expected administrative responsibilities.

Review:

* Authorized systems
* Authentication timestamps
* Logon and logoff activity
* Unusual access patterns
* Additional security events associated with affected systems

Sensitive environment-specific values are intentionally omitted from this documentation.

---

## 5. Remediation

Potential remediation actions identified from the investigation:

1. Reset the affected account's credentials.
2. Review the account's permissions and access to critical workloads.
3. Investigate affected systems for signs of compromise.
4. Disable the account if unauthorized access cannot be ruled out.
5. Review related authentication activity for additional suspicious behavior.

## Validation

* [ ] Account activity identified
* [ ] Authentication events reviewed
* [ ] Authentication activity correlated with systems
* [ ] Potentially affected systems identified
* [ ] Access reviewed against expected activity
* [ ] Remediation actions documented

## Result

KQL was used to investigate account activity, isolate authentication events, and identify systems associated with the activity. The investigation results were used to determine appropriate account and endpoint remediation actions.

> **Portfolio note:** Environment-specific usernames, hostnames, IP addresses, tenant information, and other sensitive identifiers have been replaced with generic placeholders.
