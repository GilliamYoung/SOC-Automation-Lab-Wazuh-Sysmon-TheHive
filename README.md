# SOC Automation Lab | Wazuh + Sysmon + TheHive

## Overview
This project demonstrates the creation of a small-scale Security Operations Center (SOC) automation environment using virtualization, cloud infrastructure, SIEM monitoring, custom detection engineering, and automated incident response workflows.

The lab was designed to simulate real-world detection and response operations by monitoring a Windows 11 endpoint with Sysmon, forwarding telemetry into Wazuh SIEM, detecting malicious activity involving Mimikatz, and automatically creating incidents in TheHive through Shuffle SOAR automation.

---

## Technologies Used
- Windows 11 Pro
- Sysmon
- Wazuh SIEM
- TheHive
- Shuffle SOAR
- VirtualBox
- Vultr Cloud Infrastructure
- Ubuntu Linux
- Sysmon Event Logging
- MITRE ATT&CK Mapping

---

# Project Objectives
- Build a functional SOC environment from scratch
- Configure centralized logging and telemetry collection
- Deploy Sysmon for advanced Windows event monitoring
- Create custom Wazuh detection rules
- Detect Mimikatz credential dumping activity
- Automate alert triage and case creation using Shuffle
- Integrate alerts into TheHive for incident management
- Simulate adversary behavior in a controlled lab

---

# Environment Setup

## Infrastructure
The environment consists of:

| Windows 11 VM | Endpoint generating telemetry |
| Ubuntu Server (Wazuh) | SIEM and log analysis |
| Ubuntu Server (TheHive) | Incident response platform |

The Windows 11 virtual machine was hosted locally using Oracle VirtualBox and configured with Sysmon for advanced telemetry generation.

<img width="998" height="623" alt="windows 11 vm virtual box" src="https://github.com/user-attachments/assets/b877a25d-b156-4024-8fdc-f894793a0138" />

Two Ubuntu cloud servers were deployed through Vultr:
- Wazuh SIEM Server
- TheHive Incident Response Server

<img width="1905" height="902" alt="vultr cloud instances" src="https://github.com/user-attachments/assets/57df5968-4a37-4704-9b17-8d19715eb727" />

---

# Wazuh SIEM Deployment

Wazuh was configured as the centralized SIEM platform for:
- Event collection
- Log analysis
- Threat detection
- Rule-based alerting
---

# Wazuh Dashboard

<img width="977" height="596" alt="active agent" src="https://github.com/user-attachments/assets/c16b29b4-63a8-4399-92a6-e039a1878d8a" />

---

# Sysmon Configuration

Sysmon was installed on the Windows 11 endpoint to provide enhanced visibility into:
- Process creation
- Network connections
- PowerShell activity
- Command execution
- Credential dumping activity

The Windows endpoint was onboarded into Wazuh using the Wazuh agent.


<img width="1910" height="840" alt="actualsysmonhighlight" src="https://github.com/user-attachments/assets/0ac24a2f-077b-406a-87b4-0aa41b70d517" />

---

# Filebeat Configuration

Filebeat was modified to enable Wazuh archive indexing for improved event visibility and custom detection testing.

<img width="1176" height="553" alt="change archives to true in filebeat" src="https://github.com/user-attachments/assets/80295b9e-994a-44b5-8d4f-6e562f04537a" />

---

# Wazuh Archive Indexing

Custom indexing was configured to allow deeper inspection of raw event data from Sysmon logs.

<img width="1153" height="556" alt="raw data from ossec archives" src="https://github.com/user-attachments/assets/fe92f071-0a9d-4771-9f48-773582fa12a9" />

---

# Detection Engineering

A custom Wazuh detection rule was created to identify Mimikatz execution activity using Sysmon Event ID monitoring.

## Custom Rule

<img width="1900" height="848" alt="rule updated wazuh" src="https://github.com/user-attachments/assets/72efb947-d2df-4ea9-8cdd-07d8875f705d" />


---

# Adversary Simulation

Mimikatz was downloaded and executed on the Windows 11 endpoint to simulate credential dumping behavior commonly used by attackers.

<img width="1016" height="670" alt="mimikatz downloaded" src="https://github.com/user-attachments/assets/c16961fb-f4b0-4503-abc8-6dd7dc57351c" />


---

# Detection Results

Once Mimikatz executed, Sysmon generated telemetry which was ingested by Wazuh and triggered the custom detection rule.

## Detection Events
- Process creation logged
- Sysmon telemetry generated
- Wazuh alert triggered
- MITRE ATT&CK mapping applied
- Alert forwarded into Shuffle SOAR

---

# Wazuh Detection Output

<img width="1885" height="902" alt="mimikatz alerts wazuh" src="https://github.com/user-attachments/assets/f4ad7e1f-b846-4c56-96dc-cdd79c4c3418" />

<img width="1893" height="892" alt="mimikatz discovery wazuh" src="https://github.com/user-attachments/assets/c41ea0bb-7642-4758-9997-6772f084cfc2" />


---

# SOAR Automation with Shuffle

Shuffle SOAR was integrated to automate incident response workflows.

## Automated Workflow
1. Wazuh generates alert
2. Alert sent to Shuffle webhook
3. Shuffle processes IOC data
4. Alert forwarded into TheHive
5. Incident case automatically created
6. Email sent to Analyst

<img width="1898" height="911" alt="shuffle automation" src="https://github.com/user-attachments/assets/155e1936-86bf-438a-bf32-ecb28071e86d" />

---

# TheHive Integration

TheHive was configured as the incident response platform for:
- Case management
- Alert triage
- Investigation tracking
- Incident documentation

---

# TheHive Alert Creation

<img width="1247" height="377" alt="mimikatz usage detected the hive" src="https://github.com/user-attachments/assets/9f3232f4-a418-46bc-b78d-26efb5fa79ee" />


---


# Skills Demonstrated

## Blue Team Skills
- SIEM Engineering
- Threat Detection
- Detection Rule Development
- Endpoint Monitoring
- Incident Response
- Log Analysis
- Threat Hunting
- SOAR Automation

## Infrastructure Skills
- Windows Administration
- Virtualization
- Cloud Infrastructure
- Networking
- System Hardening

---

# Key Accomplishments
- Built an end-to-end SOC environment
- Created custom Wazuh detection rules
- Successfully detected Mimikatz execution
- Automated incident escalation workflows
- Integrated SIEM + SOAR + Case Management
- Simulated attacker credential dumping techniques
- Implemented MITRE ATT&CK-aligned detections

---

# Future Improvements
- Integrate Slack or Discord alerting
- Add Sigma rule conversions
- Deploy Suricata IDS
- Add YARA scanning
- Implement automated containment actions
- Add threat intelligence enrichment
- Integrate VirusTotal API

---

# Author

## Gilliam Young
Cybersecurity Enthusiast | SOC Analyst Aspirant | Detection Engineering & SIEM Automation
