
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

## 🔎 Step 3 – Port Scanning (Windows 11)

Result:
All ports filtered (Firewall enabled)

---

## 🧠 Key Findings

* Windows 7 exposes multiple services (high attack surface)
* Windows 11 is fully filtered and hardened
* Network reconnaissance successfully performed

---

## 📌 Conclusion

This lab helped understand how attackers discover systems, services, and potential attack surfaces using Nmap.
