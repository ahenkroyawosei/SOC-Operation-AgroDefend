# 🔐 Operation AgroDefend  
## SOC Deployment in a Segmented Enterprise Network Environment

---

## 📌 Project Overview

Operation AgroDefend simulates a real-world enterprise Security Operations Center (SOC) deployment within a segmented network infrastructure.

The project was designed to address the lack of centralized logging, cross-network visibility, and correlated threat detection across enterprise segments. A structured SOC lab was built to simulate live attack scenarios and validate detection engineering capabilities.

This project demonstrates practical blue-team skills including network segmentation, SIEM deployment, attack simulation, log correlation, and security hardening.

---

## 🎯 Objectives

- Implement enterprise-style network segmentation
- Deploy centralized log collection and correlation
- Simulate real-world attack scenarios
- Validate brute-force detection capability
- Assess segmentation effectiveness against lateral movement
- Produce security recommendations based on findings

---

## 🏗 Network Architecture

The environment was built using:

- **pfSense** (Firewall & Segmentation)
- **Wazuh** (SIEM & Log Correlation)
- Ubuntu Server (DMZ & Wazuh Manager)
- Windows 10 Endpoint
- Kali Linux (Attacker Machine)

### Network Segments

- **WAN** – Simulated internet access  
- **LAN** – Internal user network & SOC infrastructure  
- **DMZ** – Public-facing server segment  

### Core Assets

| Asset | Role | IP Address |
|-------|------|------------|
| Wazuh Manager (Ubuntu) | Log Collector & SIEM | 192.168.2.10 |
| Windows 10 Endpoint | Monitored Client | 192.168.1.102 |
| Ubuntu Server (DMZ) | Target Server | 192.168.2.11 |
| Kali Linux | Attacker Machine | 192.168.1.100 |

---

## 🔎 SOC Deployment

### Wazuh Manager Responsibilities

- Log aggregation
- Event correlation
- Real-time alerting
- Dashboard visualization
- Severity classification

### Agent Deployment

Wazuh agents were installed on:

- Windows 10 endpoint  
- Ubuntu DMZ server  

### Log Sources Collected

- `/var/log/auth.log`
- `/var/log/vsftpd.log`
- Windows Security Event Logs

---

## 🔥 Threat Simulation Methodology

Attack simulations were conducted from Kali Linux.

### 1️⃣ Reconnaissance

- Network scanning using Nmap
- Identified exposed services:
  - SSH (22/tcp)
  - FTP (21/tcp)

### 2️⃣ Brute-Force Attacks

Using Hydra, 100+ authentication attempts were launched against:

- FTP service
- SSH service

Generated:
- Repeated failed login entries
- Authentication anomalies
- Credential discovery events

### 3️⃣ Post-Exploitation Simulation

- Successful SSH login
- Successful FTP login
- Privilege escalation attempts (sudo)
- User account creation

These actions simulated persistence and privilege abuse behaviors.

---

## 📊 Detection & Correlation Results

Wazuh successfully:

- Detected and correlated 100+ brute-force attempts
- Identified source IP (192.168.1.100)
- Classified SSH brute-force as higher severity
- Aggregated multi-source authentication logs
- Generated real-time alerts in dashboard

### Log Sources Correlated

- Linux authentication logs
- FTP logs
- Windows security logs
- Wazuh alert engine outputs

---

## 🛡 Segmentation Effectiveness

Firewall rules enforced:

- LAN → DMZ access allowed  
- DMZ → LAN traffic blocked  
- Logged monitored traffic  

### Outcome

- Brute-force attempts were detected
- No lateral movement from DMZ to LAN
- Internal asset exposure was prevented

Segmentation reduced attack propagation risk but highlighted weaknesses in credential policies.

---

## 🚨 Key Risks Identified

- Weak credential exposure
- No account lockout policy
- Public-facing SSH and FTP services
- Potential privilege escalation
- Authentication abuse patterns

---

## 🔐 Security Recommendations

- Implement account lockout policy
- Enforce strong password requirements
- Restrict SSH by IP allowlisting
- Enable IDS/IPS on pfSense
- Implement Multi-Factor Authentication (MFA)
- Conduct proactive log review & threat hunting

---

## 🧠 Skills Demonstrated

- SOC deployment & configuration
- SIEM implementation (Wazuh)
- Network segmentation design
- Firewall rule engineering
- Threat simulation
- Brute-force detection engineering
- Log correlation & alert tuning
- Security posture assessment
- Technical reporting

---

## 📈 Project Outcomes

- Built a 3-zone segmented enterprise lab
- Centralized 3+ log sources
- Simulated 100+ authentication attack attempts
- Achieved real-time correlated detection
- Prevented lateral movement via firewall enforcement
- Produced actionable security hardening recommendations

- 📄[Read_report](https://drive.google.com/file/d/1FJW-GNNGe8k0kODb-1t0X4jifGtCYTl8/view?usp=sharing)
---
## 👤 Author

Yaw Osei Ahenkro  
Cybersecurity Analyst | SOC & Blue Team Focus

---
