# 🛡️ Wazuh + Sysmon Threat Detection Lab

## 📌 Problem Statement

How can a SOC analyst monitor a Windows endpoint, detect suspicious activities, and investigate security events using open-source security monitoring tools?

This project explores the use of Wazuh and Sysmon to collect endpoint telemetry, generate security alerts, and support threat investigation on a Windows 11 system.


## 🎯 Objectives

- Deploy Wazuh using Docker Desktop on Windows 11.
- Integrate a Windows 11 endpoint with Wazuh for centralized monitoring.
- Configure Sysmon to collect detailed endpoint telemetry.
- Detect activities such as PowerShell execution, process creation, and failed login attempts.
- Investigate generated alerts through the Wazuh Dashboard.
- Gain hands-on experience with SOC monitoring and threat investigation workflows.

## 🧪 Lab Setup

### Host System
- Operating System: Windows 11
- Processor: AMD Ryzen 5 5500U
- Memory: 16 GB RAM
- Storage: NVMe SSD

### Wazuh Deployment
- Deployment Method: Docker Desktop
- Wazuh Version: 4.14.5
- Architecture: Single-Node Deployment

### Monitored Endpoint
- Operating System: Windows 11
- Wazuh Agent: Installed and enrolled
- Endpoint Name: Ironhead

### Tools Used
- Wazuh Manager
- Wazuh Dashboard
- Wazuh Indexer
- Docker Desktop
- Sysmon
- Windows Event Logs


## 🏗️ Architecture

```text
Windows 11 Endpoint
(Sysmon + Wazuh Agent)
          │
          ▼
     Wazuh Manager
          │
          ▼
     Wazuh Indexer
          │
          ▼
    Wazuh Dashboard
```

The Windows 11 endpoint generates security events and Sysmon telemetry. The Wazuh Agent forwards logs to the Wazuh Manager, where events are processed and analyzed. Processed events are stored in the Wazuh Indexer and visualized through the Wazuh Dashboard for monitoring and investigation.
