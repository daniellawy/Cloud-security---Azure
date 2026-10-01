# KQL — Network Investigation

## Objective

Use KQL to investigate network activity, identify communication patterns, and correlate network connections with affected devices.

## Data Source

```text id="h82r2w"
DeviceNetworkEvents
```

## 1. Review Recent Network Activity

```kql id="y4qjz4"
DeviceNetworkEvents
| project
    Timestamp,
    DeviceName,
    InitiatingProcessAccountName,
    InitiatingProcessFileName,
    RemoteIP,
    RemotePort,
    Protocol
| sort by Timestamp desc
```

Review recent outbound network connections from monitored endpoints.

![Recent network activity](../screenshots/network/01-network-activity.png)

---

## 2. Investigate a Specific Remote IP

Search for connections to an IP address under investigation.

```kql id="m2a0la"
DeviceNetworkEvents
| where RemoteIP == "<REMOTE_IP>"
| project
    Timestamp,
    DeviceName,
    InitiatingProcessAccountName,
    InitiatingProcessFileName,
    RemoteIP,
    RemotePort,
    Protocol
| sort by Timestamp desc
```

Review which devices and processes communicated with the destination.

![Remote IP investigation](../screenshots/network/02-remote-ip.png)

---

## 3. Identify Frequently Contacted IPs

```kql id="7y3nqz"
DeviceNetworkEvents
| summarize ConnectionCount = count()
    by RemoteIP
| sort by ConnectionCount desc
```

Identify remote IP addresses associated with frequent network connections.

![Connections by remote IP](../screenshots/network/03-connections-by-ip.png)

---

## 4. Investigate Network Activity by Device

```kql id="1w6d8s"
DeviceNetworkEvents
| summarize ConnectionCount = count()
    by DeviceName
| sort by ConnectionCount desc
```

Identify devices generating the highest volume of recorded network connections.

![Network activity by device](../screenshots/network/04-network-by-device.png)

---

## 5. Investigate Network Activity by Process

```kql id="4j2l9p"
DeviceNetworkEvents
| summarize ConnectionCount = count()
    by InitiatingProcessFileName
| sort by ConnectionCount desc
```

Identify processes responsible for network connections and investigate unusual processes.

![Network activity by process](../screenshots/network/05-network-by-process.png)

---

## 6. Investigate a Specific Port

```kql id="q9x7na"
DeviceNetworkEvents
| where RemotePort == <PORT>
| project
    Timestamp,
    DeviceName,
    InitiatingProcessFileName,
    RemoteIP,
    RemotePort,
    Protocol
| sort by Timestamp desc
```

Review endpoints and processes communicating over the selected port.

![Port investigation](../screenshots/network/06-port-investigation.png)

---

## 7. Investigation

Correlate network activity with endpoint and identity data.

Review:

* Source device
* Remote destination
* Remote port
* Protocol
* Initiating process
* Associated account
* Connection frequency
* Time of activity

Determine whether the communication is expected or requires additional investigation.

Sensitive environment-specific values are intentionally omitted.

## Validation

* [ ] Network activity reviewed
* [ ] Remote destinations identified
* [ ] Network activity correlated with devices
* [ ] Initiating processes reviewed
* [ ] Port activity investigated
* [ ] Suspicious connections assessed
* [ ] Additional investigation documented when required

## Result

KQL was used to investigate endpoint network connections, identify remote destinations, correlate connections with devices and processes, and identify network activity requiring further investigation.

> **Portfolio note:** Environment-specific IP addresses, hostnames, usernames, ports, tenant information, and other sensitive identifiers should be removed or blurred before screenshots are uploaded.
