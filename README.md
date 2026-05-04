
The goal of this lab is to discover active devices on a network, identify open ports, and analyze network traffic.
# 🔐 Network Security Lab 1 – Network Reconnaissance

## 🎯 Objective

This lab demonstrates basic network reconnaissance using Nmap in a controlled virtual environment.

---

## 🧰 Environment

* Kali Linux (Attacker)
* Windows 7 (Target 1)
* Windows 11 (Target 2)
* VirtualBox internal network

---

## 🌐 Network Setup

All machines are configured in the same subnet:
192.168.10.0/24

---

## 🔍 Step 1 – Host Discovery

Command:
nmap -sn 192.168.10.0/24

### Result:

* 3 hosts detected:

  * Kali Linux (192.168.10.30)
  * Windows 11 (192.168.10.20)
  * Windows 7 (192.168.10.21)

---

## 🔎 Step 2 – Port Scanning (Windows 7)

Command:
nmap -sS -sV 192.168.10.21

### Open ports:

* 135/tcp → RPC
* 139/tcp → NetBIOS
* 445/tcp → SMB
* 3389/tcp → RDP

---
## 📌 Security Analysis for Step 2

- SMB (445/tcp): High risk service, commonly targeted for exploitation (e.g., file sharing vulnerabilities).
- NetBIOS (139/tcp): Legacy protocol that may expose system and user information.
- RPC (135/tcp): Used for Windows internal communication and can be used for enumeration.
- RDP (3389/tcp): Remote access service that can be targeted by brute-force attacks if exposed.

 ---
 ## 📌 Key Findings for Step 2

- Windows 7 exposes multiple legacy services.
- Attack surface is relatively large compared to modern systems.
- System is suitable for security testing and lab exercises.

 --- 
 -----> ### The Windows 7 system shows several exposed services that increase its attack surface. This makes it an ideal target for learning network reconnaissance and basic exploitation techniques in a controlled lab environment.

## 🔎 Step 3 – Port Scanning (Windows 11)

Result:
All ports filtered (Firewall enabled)

---

## 🧠 Key Findings

* Windows 11 is fully filtered and hardened
---
## 🪟 Windows 11 Scan Analysis

### 🟢 Host Status
- The host is up and responding successfully.

---

### 🔒 Port Scan Result
All 1000 scanned TCP ports are in filtered state.  
Not shown: 1000 filtered ports (no-response)

---

### 🧠 Interpretation of "Filtered"

A **filtered** state means that a firewall or security mechanism is blocking or dropping the probe packets sent by Nmap.

This usually indicates:
- Windows Firewall is enabled
- No response is returned to TCP probes
- Ports are not directly exposed to the network

---

### ⚖️ Comparison: Windows 7 vs Windows 11

| System        | Result              | Security Interpretation |
|---------------|---------------------|--------------------------|
| Windows 7     | Open ports visible  | High attack surface ⚠️   |
| Windows 11    | All ports filtered  | Hardened system 🟢       |

---

### 🔥 Security Analysis for step 3

- Windows 11 has an active firewall.
- No exposed network services were detected.
- The system appears hardened against basic network reconnaissance.

---

### 📌 Key Takeaway

A "filtered" result does not mean the system is invisible, but rather that it is actively protected and not exposing services to network scans.

## 📌 Conclusion
* Network reconnaissance successfully performed
  ### 🧠 SOC Perspective

From a Security Operations Center (SOC) point of view:

- Windows 7 → suspicious / high exposure endpoint
- Windows 11 → secured and normal enterprise endpoint
This lab helped understand how attackers discover systems, services, and potential attack surfaces using Nmap.
