# 🛡️ Wazuh & Sysmon Threat Detection Lab

## 📌 Project Overview

This project demonstrates the deployment of a Security Information and Event Management (SIEM) environment using **Wazuh** integrated with **Sysmon** on a **Windows 11** endpoint.

The objective was to gain hands-on experience with SOC Analyst workflows by collecting endpoint telemetry, investigating security events, performing threat hunting, and understanding how alerts are generated and analyzed.

---

## 🎯 Project Goals

✅ Deploy Wazuh using Docker

✅ Onboard a Windows 11 endpoint

✅ Install and configure Sysmon

✅ Collect Windows Security and Sysmon logs

✅ Investigate authentication events

✅ Analyze process creation activity

✅ Monitor file creation events

✅ Perform threat hunting using DQL

✅ Understand alert triage and validation

---

## 🏗️ Lab Architecture

```text
┌─────────────────────────────┐
│      Windows 11 Endpoint    │
│                             │
│  • Sysmon                   │
│  • Windows Event Logs       │
│  • Wazuh Agent              │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│     Wazuh Manager           │
│        (Docker)             │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│      Wazuh Indexer          │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│     Wazuh Dashboard         │
│ • Alert Investigation       │
│ • Threat Hunting (DQL)      │
└─────────────────────────────┘
```

---

## 🛠️ Technologies Used

| Category            | Technology   |
| ------------------- | ------------ |
| SIEM                | Wazuh        |
| Endpoint Monitoring | Sysmon       |
| Platform            | Windows 11   |
| Containerization    | Docker       |
| Query Language      | DQL          |
| Framework           | MITRE ATT&CK |

---

## 📸 Screenshots

### Sysmon Installation

![Sysmon Installation](https://github.com/user-attachments/assets/073d6cf0-7f2a-4fd5-8af5-62bc6aa80efe)

Sysmon was installed to provide enhanced visibility into endpoint activity such as process creation and file creation events.

---

### Sysmon Event Verification

![Sysmon Event Viewer](https://github.com/user-attachments/assets/391ec564-6eb2-4cc4-a9bf-214013d76f0b)


Verified Sysmon Event ID 1 (Process Creation) events using Windows Event Viewer before forwarding logs to Wazuh.

---

### Sysmon Events in Wazuh

![Sysmon Events in Wazuh](https://github.com/user-attachments/assets/0727a67a-fb4a-4ba9-a8c3-3928d57e624e)


Successfully ingested Sysmon telemetry into Wazuh and validated event collection.

---

### Threat Hunting Dashboard

![Threat Hunting Dashboard](https://github.com/user-attachments/assets/a34978b1-14b6-4a75-ad73-ad476e707ee1)


Used DQL queries to hunt and investigate Windows Security and Sysmon events.

---

# 🔍 Investigations Performed

## 1️⃣ Failed Login Investigation

### Event ID: 4625

**Description:**
An account failed to log on.

### Investigation

* Reviewed failed authentication events
* Checked logon type
* Analyzed authentication failure details
* Verified event collection in Wazuh

### Outcome

✅ Successfully detected and investigated failed login activity.

---

## 2️⃣ Successful Login Investigation

### Event ID: 4624

**Description:**
An account successfully logged on.

### Investigation

* Reviewed successful authentication events
* Analyzed logon type information
* Correlated activity with endpoint usage

### Outcome

✅ Successfully validated authentication monitoring.

---

## 3️⃣ Process Creation Investigation

### Sysmon Event ID: 1

**Description:**
Process Creation Event

### Investigation

Analyzed:

* Process Image
* Command Line
* Parent Process
* User Context

### Example Processes Observed

```text
powershell.exe
docker.exe
secedit.exe
```

### Outcome

✅ Gained visibility into endpoint process execution activity.

---

## 4️⃣ File Creation Investigation

### Sysmon Event ID: 11

**Description:**
File Creation Event

### Observed Artifact

```text
__PSScriptPolicyTest_*.ps1
```

### Investigation

* Reviewed generated file
* Investigated associated PowerShell activity
* Validated file purpose

### Outcome

✅ Identified the activity as legitimate PowerShell behavior.

---

# 🎯 Threat Hunting Queries

### Failed Logins

```dql
data.win.system.eventID:4625
```

### Successful Logins

```dql
data.win.system.eventID:4624
```

### Sysmon Events

```dql
rule.groups:sysmon
```

### Process Creation Events

```dql
data.win.system.eventID:1
```

### File Creation Events

```dql
data.win.system.eventID:11
```

---

# 🧠 Key Concepts Learned

### Windows Security Events

| Event ID | Description      |
| -------- | ---------------- |
| 4624     | Successful Login |
| 4625     | Failed Login     |

### Sysmon Events

| Event ID | Description      |
| -------- | ---------------- |
| 1        | Process Creation |
| 11       | File Creation    |

---

# 🚧 Challenges Encountered

### Wazuh Agent Disconnection

**Issue**

The Windows endpoint stopped communicating with the Wazuh Manager.

**Root Cause**

The Windows host IP address changed, causing the agent to lose connectivity with the manager.

**Resolution**

Updated the manager IP address in the agent configuration file and restarted the Wazuh Agent service.

**Outcome**

✅ Successfully restored communication and resumed log collection.

---

# 💡 Skills Demonstrated

* SIEM Monitoring
* Log Analysis
* Alert Triage
* Threat Hunting
* Windows Event Analysis
* Sysmon Analysis
* Authentication Monitoring
* Process Creation Analysis
* File Creation Monitoring
* Endpoint Visibility
* Security Investigation

---

# 📚 Key Learning Outcomes

Through this project I gained practical experience in:

* Deploying a SIEM solution using Wazuh
* Collecting endpoint telemetry with Sysmon
* Investigating Windows Security events
* Investigating Sysmon process and file creation events
* Performing threat hunting using DQL queries
* Understanding alert generation and analysis workflows
* Validating alerts and identifying benign activity

---

## ⭐ Conclusion

This project provided hands-on experience with deploying and operating a Wazuh SIEM environment integrated with Sysmon on a Windows 11 endpoint.

Through this lab I learned how endpoint telemetry is generated, collected, analyzed, and investigated using Wazuh. I performed authentication monitoring, process creation analysis, file creation analysis, alert triage, and threat hunting using DQL queries.

The project strengthened my understanding of SOC Analyst workflows, Windows event logging, Sysmon telemetry, and security event investigation.
