# 🔍 Cybersecurity: Nmap Network Scanning

## 📖 Table of Contents
- [Objective](#-objective)
- [Tools & Environment](#️-tools--environment)
- [Practical Tasks Executed](#-practical-tasks-executed)
  - [1. Host Discovery](#1-host-discovery)
  - [2. Port Scanning](#2-port-scanning)
  - [3. Service & Version Detection](#3-service--version-detection)
  - [4. OS Detection](#4-os-detection)
  - [5. NSE Script Scanning](#5-nse-script-scanning)
  - [6. Firewall Detection](#6-firewall-detection)
- [Scan Report & Conclusion](#-scan-report--conclusion)

---

## 🎯 Objective
This project demonstrates practical network reconnaissance using Nmap. The objective is to identify live hosts, discover open ports, detect running services, and map out the operating systems and potential vulnerabilities within a target network.

## 🛠️ Tools & Environment
*   **Attacker Machine:** Kali Linux
*   **Target Machine:** Metasploitable 2 / Windows VM *(Update this based on your lab)*
*   **Tool:** Nmap (Network Mapper)

---

## 🚀 Practical Tasks Executed

### 1. Host Discovery
Identified live hosts on the local subnet without performing a full port scan.
*   **Command:** `nmap -sn [Target_IP_Subnet]`
*   **Result:**
<br>

![Host Discovery](images/host-discovery.png)

### 2. Port Scanning
Scanned the target machine to identify all open TCP/UDP ports.
*   **Command:** `nmap -p- [Target_IP]`
*   **Result:**
<br>

![Port Scanning](images/port-scanning.png)

### 3. Service & Version Detection
Probed open ports to determine the exact service and software version running.
*   **Command:** `nmap -sV [Target_IP]`
*   **Result:**
<br>

![Service Detection](images/service-detection.png)

### 4. OS Detection
Utilized TCP/IP stack fingerprinting to guess the target's operating system.
*   **Command:** `nmap -O [Target_IP]`
*   **Result:**
<br>

![OS Detection](images/os-detection.png)

### 5. NSE Script Scanning
Ran default Nmap Scripting Engine (NSE) scripts to identify common vulnerabilities and misconfigurations.
*   **Command:** `nmap -sC [Target_IP]`
*   **Result:**
<br>

![NSE Scripts](images/nse-scripts.png)

### 6. Firewall Detection
Sent fragmented packets and used specific scan types (like ACK or FIN scans) to determine if a firewall is filtering traffic.
*   **Command:** `nmap -f [Target_IP]`
*   **Result:**
<br>

![Firewall Detection](images/firewall-detection.png)

---

## 📊 Scan Report & Conclusion
*(Write 2-3 sentences here summarizing what you found. Example: "The scan revealed a Linux-based target running outdated Apache and vsftpd services, indicating critical vulnerabilities that should be patched.")*
