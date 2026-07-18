# Phase 1 — SOC Foundation

## Executive Summary

Phase 1 focused on designing and deploying the foundational components of an Enterprise Home Security Operations Center (SOC). The primary objective was to establish a reliable endpoint telemetry pipeline capable of collecting, transporting, indexing, and searching Windows security events and Sysmon telemetry within Splunk Enterprise.

This phase successfully validated end-to-end log collection from a Windows endpoint using Sysmon and the Splunk Universal Forwarder, providing the visibility required for future detection engineering, threat hunting, and incident response activities.

With the telemetry pipeline operational, the environment is now ready for dashboard development, detection rule creation, and integration of additional enterprise log sources.

---

# Objectives

* Deploy Splunk Enterprise as the centralized SIEM platform.
* Configure a Windows endpoint for telemetry collection.
* Deploy Sysmon for enhanced endpoint visibility.
* Install and configure the Splunk Universal Forwarder.
* Create a dedicated index for Sysmon events.
* Verify successful ingestion of Windows Security and Sysmon events.
* Validate searchable endpoint telemetry.
* Prepare the environment for future detection engineering.

---

# Lab Environment

## Security Platform

* Splunk Enterprise

## Endpoint

* Windows Workstation
* Sysmon
* Splunk Universal Forwarder

## Network Infrastructure

* Cisco Firepower 1010 (FDM Managed)
* Netgear R7000
* Cisco Catalyst 2100

---

# Network Architecture

```text
                    Internet
                        │
             Cisco Firepower 1010
                        │
               Netgear R7000 Router
                        │
            Cisco Catalyst 2100 Switch
                        │
                 Windows Workstation
                        │
                     Sysmon
                        │
          Splunk Universal Forwarder
                        │
                 Splunk Enterprise
```

---

# Splunk Deployment

Splunk Enterprise was deployed as the centralized Security Information and Event Management (SIEM) platform for the Home SOC. The deployment serves as the primary location for ingesting, indexing, searching, and visualizing security telemetry collected throughout the environment.

A dedicated `sysmon` index was created to logically separate endpoint telemetry from other data sources, improving organization and simplifying future detection development.

---

# Sysmon Deployment

Sysmon was installed on the Windows endpoint to extend native Windows logging with high-value security telemetry.

The deployment enables detailed visibility into endpoint activity including:

* Process creation
* Network connections
* DNS queries
* Process hashes
* Parent-child process relationships
* Process GUID tracking

These events provide the foundation for building high-fidelity detections.

---

# Universal Forwarder Configuration

The Splunk Universal Forwarder was installed on the Windows workstation to securely forward Windows Security and Sysmon Operational logs to Splunk Enterprise.

Configured log sources included:

* Windows Security Log
* Microsoft-Windows-Sysmon/Operational

Successful forwarding established continuous endpoint telemetry into the SIEM.

---

# Endpoint Telemetry Validation

The following Windows Security events were successfully collected:

| Event ID | Description                 |
| -------- | --------------------------- |
| 4624     | Successful Logon            |
| 4672     | Special Privileges Assigned |
| 5379     | Credential Manager Activity |

The following Sysmon events were successfully collected:

| Event ID | Description        |
| -------- | ------------------ |
| 1        | Process Creation   |
| 3        | Network Connection |
| 22       | DNS Query          |

Verified event fields included:

* Image
* CommandLine
* ParentImage
* User
* Hashes
* DestinationIp
* DestinationPort
* QueryName
* ProcessGuid

These fields confirm successful XML parsing and provide rich endpoint telemetry for future analysis.

---

# Verification

The telemetry pipeline was validated using Splunk searches against the dedicated Sysmon index.

Example search:

```spl
index=sysmon
```

Additional validation confirmed events were arriving from:

```text
WinEventLog:Microsoft-Windows-Sysmon/Operational
```

Example endpoint activity observed during validation included:

* Splunk Optimize process execution
* Grammarly HTTPS connections
* Grammarly DNS queries
* Windows background processes

These events confirmed that endpoint telemetry was being ingested and indexed correctly.

---

# Troubleshooting

## Universal Forwarder Permission Issue

### Problem

The Universal Forwarder failed to subscribe to the Sysmon Operational log and generated the following error:

```text
errorCode=5
Could not subscribe to Microsoft-Windows-Sysmon/Operational
```

### Root Cause

The Windows service account running the Universal Forwarder did not initially have sufficient permissions to access the Sysmon Operational event channel.

### Resolution

The service configuration and permissions were corrected, allowing the forwarder to successfully subscribe to the Sysmon Operational log.

### Result

Successful ingestion of Sysmon events into the dedicated `sysmon` index verified that the telemetry pipeline was functioning as expected.

---

# Lessons Learned

This phase reinforced several important operational concepts:

* Endpoint telemetry is only valuable after end-to-end validation.
* Windows Event Log permissions can directly impact data collection.
* Dedicated indexes simplify data organization and future search performance.
* Verification searches should be performed immediately after deployment.
* Rich endpoint telemetry significantly improves future detection capabilities.

---

# Outcome

Phase 1 successfully established the foundational infrastructure for the Enterprise Home SOC.

### Completed

* Splunk Enterprise deployment
* Universal Forwarder deployment
* Sysmon deployment
* Windows Security log ingestion
* Sysmon XML ingestion
* Dedicated `sysmon` index
* Endpoint telemetry validation

---

# Next Phase

Phase 2 will focus on Detection Engineering and SOC Visualization.

Planned work includes:

* Enterprise SOC dashboards
* SPL detection development
* Scheduled alerts
* MITRE ATT&CK mapping
* Threat hunting workflows
* Detection validation through controlled attack simulation

The successful completion of Phase 1 provides a stable platform for expanding the Home SOC into a comprehensive security monitoring and incident response environment.
