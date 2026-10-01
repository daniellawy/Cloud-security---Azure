# Microsoft Sentinel — Log Analytics

## Objective

Verify ingested security telemetry and identify the Log Analytics tables used for investigation.

## Configuration

```text
Microsoft Sentinel
        ↓
Log Analytics Workspace
        ↓
Tables
        ↓
Security Telemetry
        ↓
KQL Investigation
```

## Workspace

* **Workspace:** `law-sentinel-lab`
* **Resource Group:** `rg-sentinel-lab`

## Tables

| Data Source             | Table                                     |
| ----------------------- | ----------------------------------------- |
| Microsoft Entra ID      | `SigninLogs`                              |
| Azure Activity          | `AzureActivity`                           |
| Windows Security Events | `SecurityEvent`                           |
| Defender XDR            | Depends on connected Defender data source |

# Log Analytics Tables

## SigninLogs

**Source:** Microsoft Entra ID  
**Purpose:** Authentication and sign-in investigation.

## AzureActivity

**Source:** Azure Activity  
**Purpose:** Azure resource and subscription activity.

## SecurityEvent

**Source:** Windows Security Events  
**Purpose:** Windows security event investigation.


## Validation

Run the following queries in **Microsoft Sentinel → Logs**.

### Entra ID

```kql
SigninLogs
| take 10
```

### Azure Activity

```kql
AzureActivity
| take 10
```

### Windows Security Events

```kql
SecurityEvent
| take 10
```

## Result

Security telemetry is confirmed in the Log Analytics workspace and can be queried using KQL.
