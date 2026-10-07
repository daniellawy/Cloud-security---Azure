# Microsoft Sentinel — Data Connectors

## Objective

Connect security data sources to Microsoft Sentinel and verify telemetry ingestion.

## 1. Microsoft Entra ID

### Configuration

```text
Microsoft Sentinel
→ Content Hub
→ Microsoft Entra ID
→ Install Solution
→ Data Connectors
→ Microsoft Entra ID
→ Configure
```

* **Purpose:** Identity and authentication monitoring
* **Status:** Connected

![Microsoft Entra ID connector](screenshots/01-entra-id.png)

## 2. Azure Activity

### Configuration

```text
Microsoft Sentinel
→ Content Hub
→ Azure Activity
→ Install Solution
→ Data Connectors
→ Azure Activity
→ Configure
```

* **Purpose:** Azure subscription and resource activity monitoring
* **Status:** Connected

![Azure Activity connector](screenshots/azure-activity-installed.png)

## 3. Microsoft Threat Intelligence

### Configuration

```text
Microsoft Sentinel
→ Content Hub
→ Microsoft Threat Intelligence
→ Install Solution
→ Data Connectors
→ Microsoft Threat Intelligence
→ Configure
```

* **Purpose:** Threat intelligence and indicator monitoring
* **Status:** Connected

![Microsoft Threat Intelligence connector](screenshots/03-threat-intelligence.png)

## 4. Microsoft Defender XDR

### Configuration

```text
Microsoft Sentinel
→ Content Hub
→ Microsoft Defender XDR
→ Install Solution
→ Data Connectors
→ Microsoft Defender XDR
→ Connect
```

* **Purpose:** Endpoint and threat telemetry
* **Status:** Connected

![Microsoft Defender XDR connector](screenshots/04-defender-xdr.png)

## Validation

* [ ] Entra ID telemetry verified
* [ ] Azure Activity telemetry verified
* [ ] Microsoft Threat Intelligence configured
* [ ] Defender XDR telemetry verified
* [ ] Telemetry verified in Log Analytics

## Architecture

```text
Microsoft Entra ID ───────────────┐
Azure Activity ──────────────────┤
Microsoft Threat Intelligence ───┼──→ Microsoft Sentinel
Microsoft Defender XDR ───────────┘
                                      ↓
                              Log Analytics Workspace
                                      ↓
                                  KQL Queries
```

## Result

Identity, Azure activity, threat-intelligence, and endpoint security telemetry are connected to Microsoft Sentinel and available for investigation.

