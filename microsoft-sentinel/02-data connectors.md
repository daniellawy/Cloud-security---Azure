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


## 2. Microsoft Defender XDR

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

## 3. Windows Security Events via AMA

### Configuration

```text
Microsoft Sentinel
→ Content Hub
→ Windows Security Events
→ Install Solution
→ Data Connectors
→ Windows Security Events via AMA
→ Configure
```

* **Purpose:** Windows security and authentication events
* **Status:** Connected

## Validation

* [ ] Entra ID telemetry verified
* [ ] Defender XDR telemetry verified
* [ ] Windows Security Events verified
* [ ] Telemetry verified in Log Analytics

## Architecture

```text
Microsoft Entra ID ──────────┐
Microsoft Defender XDR ──────┼──→ Microsoft Sentinel
Windows Security Events ─────┘
                                      ↓
                              Log Analytics Workspace
                                      ↓
                                  KQL Queries
```

## Result

Identity, cloud, endpoint, and Windows security telemetry are connected to Microsoft Sentinel and available for investigation.

