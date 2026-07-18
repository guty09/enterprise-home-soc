# Enterprise Home SOC

> A professional Security Operations Center (SOC) built in a home lab to develop and demonstrate Security Operations, Detection Engineering, SIEM Administration, Network Security, Threat Hunting, and Incident Response skills using enterprise technologies.

![Project Status](https://img.shields.io/badge/Status-Phase%201%20Complete-brightgreen)
![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![SIEM](https://img.shields.io/badge/SIEM-Splunk%20Enterprise-orange)
![Telemetry](https://img.shields.io/badge/Endpoint-Sysmon-success)
![Firewall](https://img.shields.io/badge/Firewall-Cisco%20Firepower-blue)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

# Project Overview

The Enterprise Home SOC is a long-term cybersecurity engineering project that simulates the design, deployment, and operation of a modern Security Operations Center.

Unlike isolated cybersecurity labs, this project is built as a continuously evolving enterprise environment where endpoint telemetry, network visibility, detection engineering, threat hunting, and incident response are developed together.

Every deployment, dashboard, detection, investigation, and architectural improvement is documented to demonstrate real-world security engineering practices.

---

# Project Objectives

- Build an enterprise-style Security Operations Center
- Centralize endpoint and network telemetry
- Develop custom Splunk dashboards
- Engineer high-fidelity detections
- Practice incident response
- Perform proactive threat hunting
- Integrate Cisco security infrastructure
- Expand into wireless monitoring
- Document every engineering decision

---

# Current Lab Architecture

```text
                    Internet
                        │
            Cisco Firepower 1010 NGFW
                        │
                Netgear R7000 Router
                        │
             Cisco Catalyst 2100 Switch
                        │
        ┌───────────────┴───────────────┐
        │                               │
 Windows Workstation              Future Linux
     Sysmon                         Auditd
        │                               │
        └───────────────┬───────────────┘
                        │
          Splunk Universal Forwarder
                        │
                 Splunk Enterprise
                        │
        ┌───────────────┼────────────────┐
        │               │                │
   Dashboards     Detection Rules   Threat Hunting
                        │
               Incident Response
```

---

# Technology Stack

## SIEM

- Splunk Enterprise

## Endpoint Monitoring

- Sysmon
- Windows Security Logs
- Splunk Universal Forwarder

## Network Infrastructure

- Cisco Firepower 1010 (FDM)
- Cisco Catalyst 2100
- Netgear R7000

## Operating Systems

- Windows 11

## Future Integrations

- Linux Auditd
- Wireless Monitoring
- Threat Intelligence
- Cloud Log Sources

---

# Current Capabilities

## Endpoint Telemetry

- Windows Security Event Logs
- Sysmon XML Events
- Process Creation
- Network Connections
- DNS Queries

## Splunk

- Dedicated Sysmon Index
- XML Event Parsing
- Custom SPL Searches
- Endpoint Visibility

---

# Verified Event Collection

## Windows Security

| Event ID | Description |
|----------|-------------|
|4624|Successful Logon|
|4672|Special Privileges Assigned|
|5379|Credential Manager Activity|

## Sysmon

| Event ID | Description |
|----------|-------------|
|1|Process Creation|
|3|Network Connection|
|22|DNS Query|

Verified fields include:

- Image
- CommandLine
- ParentImage
- User
- Hashes
- DestinationIp
- DestinationPort
- QueryName
- ProcessGuid

---

# Project Roadmap

## ✅ Phase 1 — SOC Foundation

- Splunk Enterprise deployment
- Sysmon deployment
- Universal Forwarder deployment
- Windows Security log ingestion
- Dedicated Sysmon index
- XML event parsing
- Endpoint telemetry validation

---

## 🚧 Phase 2 — Detection Engineering

- Endpoint Overview Dashboard
- Authentication Dashboard
- Network Dashboard
- PowerShell Monitoring
- Custom SPL detections
- Scheduled alerts
- MITRE ATT&CK mapping

---

## ⏳ Phase 3 — Network Visibility

- Cisco Firepower syslog
- Firewall dashboards
- ACL monitoring
- IPS events
- VPN monitoring
- Threat events

---

## ⏳ Phase 4 — Wireless Monitoring

- Wi-Fi authentication
- Client associations
- DHCP activity
- DNS activity
- Rogue AP detection

---

## ⏳ Phase 5 — Enterprise Expansion

- Linux Auditd
- Threat Intelligence
- Correlation Searches
- Incident Response Playbooks
- Threat Hunting
- Cloud Security Monitoring

---

# Planned Detection Library

- Brute Force
- Password Spray
- Encoded PowerShell
- Mimikatz
- PsExec
- LOLBins
- Registry Persistence
- Service Creation
- Scheduled Tasks
- Beaconing
- Reverse Shells
- Network Reconnaissance
- Lateral Movement

Each detection will include:

- Objective
- Detection Logic
- SPL Query
- MITRE ATT&CK Mapping
- Validation
- False Positives
- Investigation Guide

---

# Repository Structure

```text
enterprise-home-soc/

├── architecture/
├── assets/
├── configs/
├── dashboards/
├── detections/
├── docs/
├── investigations/
├── playbooks/
└── screenshots/
```

---

# Skills Demonstrated

- Security Operations (SOC)
- SIEM Administration
- Splunk Enterprise
- Detection Engineering
- Threat Hunting
- Windows Internals
- Sysmon
- Cisco Network Security
- Firewall Administration
- Network Monitoring
- Incident Response
- MITRE ATT&CK
- Security Engineering

---

# Current Status

**Enterprise Home SOC — Phase 1 Complete**

The endpoint telemetry pipeline has been successfully deployed and validated. Current development is focused on enterprise dashboard creation, detection engineering, and alerting before expanding into Cisco network telemetry and wireless monitoring.

---

# Future Repository Content

As the project evolves, this repository will include:

- Architecture diagrams
- Dashboard documentation
- Detection documentation
- Investigation case studies
- Incident response playbooks
- Splunk SPL queries
- Configuration examples
- Screenshots
- Engineering notes
- Lessons learned

---

> **This repository is actively maintained as a long-term cybersecurity engineering portfolio project documenting the design, deployment, operation, and continuous improvement of an Enterprise Home Security Operations Center.**
