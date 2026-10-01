# Microsoft Sentinel — Log Analytics rule

## Objective

Verify ingested security telemetry and identify the Log Analytics tables used for investigation. 
Step 1: ## Enable an Analytics Rule                                                        Step 2: Review the Enabled Analytics Rule
→ Log in to the Azure portal(opens in new tab) using your credentials                      Go back to the Analytics page of your Sentinel workspace   
→ Go to your Microsoft Sentinel dashboard and select the available workspace               Switch to the Active rules tab  
→ Under Content management, select Content hub                                             Select the recently saved rule - Rare subscription-level operations in Azure   
→ Search for Azure Activity and install it                                            On the right pane, review the rule details, and scroll down to see your settings for:  → Under Configuration, select Analytics                                                               Rule frequency
→ Switch to the Rule templates tab                                                                       Rule period

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

* **Workspace:** e.g. `law-sentinel-lab`
* **Resource Group:** e.g.`rg-sentinel-lab`

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
