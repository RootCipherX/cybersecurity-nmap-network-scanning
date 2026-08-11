# 🔍 Cybersecurity: Nmap Network Scanning

## 📖 Table of Contents
- [Objective](#-objective)
- [Lab Environment](#️-lab-environment)
- [Practical Tasks Executed](#-practical-tasks-executed)
  - [1. Host Discovery (Ping Sweep)](#1-host-discovery-ping-sweep)
  - [2. TCP SYN Port Scanning](#2-tcp-syn-port-scanning)
  - [3. UDP Port Scanning](#3-udp-port-scanning)
  - [4. Service & Version Detection](#4-service--version-detection)
  - [5. OS Detection](#5-os-detection)
  - [6. Aggressive Scan & Output](#6-aggressive-scan--output)
  - [7. NSE Script Scanning](#7-nse-script-scanning)
- [Scan Report & Conclusion](#-scan-report--conclusion)
- [Authorization & Disclaimer](#️-authorization--disclaimer)

---

## 🎯 Objective
This project demonstrates practical network reconnaissance using Nmap. The objective is to identify live hosts, discover open ports, detect running services, and map out the operating systems and potential vulnerabilities within a target network.

## 🛠️ Lab Environment
*   **Operating System:** Kali Linux
*   **Attacker IP:** `10.145.8.153`
*   **Target Environment:** Local VMware/VirtualBox laboratory network
*   **Target System:** Metasploitable 2
*   **Target IP:** `10.145.8.91`
*   **Tool Used:** Nmap

---

## 🚀 Practical Tasks Executed

### 1. Host Discovery (Ping Sweep)
Identified live hosts on the local subnet without performing a full port scan to remain stealthy.
*   **Command:** `nmap -sn 10.145.8.0/24`
*   **Result:**
<br>

![Host Discovery](images/host-discovery.png)

### 2. TCP SYN Port Scanning
**Objective:** To identify the exposed TCP attack surface of the target by finding open network ports.

**Command Executed:**
`sudo nmap -sS -p- 10.145.8.91`

**Command Breakdown:**
*   `sudo`: Runs Nmap with elevated privileges required to craft and send raw network packets.
*   `nmap`: The network discovery and security auditing tool.
*   `-sS`: Performs a TCP SYN scan (Stealth Scan). It sends a SYN packet and waits for a response, but drops the connection before completing the full TCP handshake.
*   `-p-`: Instructs Nmap to aggressively scan all 65,535 TCP ports instead of just the top 1,000.
*   `10.145.8.91`: The authorized Metasploitable target IP.

**Security Relevance:**
Identifying open ports is a critical phase of reconnaissance. It allows an assessor to determine the exposed attack surface, spot services running on unexpected ports, and prioritize which services require deeper version enumeration. 

**Result / Evidence:**
<br>

![TCP Port Scanning](images/tcp-port-scanning.png)

### 3. UDP Port Scanning
Targeted UDP ports to uncover services that are often missed by standard TCP scans (like DNS or SNMP).
*   **Command:** `sudo nmap -sU -F 10.145.8.91`
*   **Result:**
<br>

![UDP Port Scanning](images/udp-scanning.png)

### 4. Service & Version Detection
Probed open ports to determine the exact service and software version running for vulnerability mapping.
*   **Command:** `nmap -sV 10.145.8.91`
*   **Result:**
<br>

![Service Detection](images/service-detection.png)

### 5. OS Detection
Utilized TCP/IP stack fingerprinting to guess the target's operating system.
*   **Command:** `sudo nmap -O 10.145.8.91`
*   **Result:**
<br>

![OS Detection](images/os-detection.png)

### 6. Aggressive Scan & Output
Performed a comprehensive aggressive scan (OS, version, script, traceroute) and saved the output to a text file for reporting.
*   **Command:** `nmap -A -oN scan_report.txt 10.145.8.91`
*   **Result:**
<br>

![Aggressive Scan](images/aggressive-scan.png)

### 7. NSE Script Scanning
Ran default Nmap Scripting Engine (NSE) scripts to automatically identify common vulnerabilities and misconfigurations.
*   **Command:** `nmap -sC 10.145.8.91`
*   **Result:**
<br>

![NSE Scripts](images/nse-scripts.png)

---

## 📊 Scan Report & Conclusion
The port scanning and enumeration phases successfully identified the attack surface of the Metasploitable 2 target. Multiple open ports providing various network services (including FTP, SSH, HTTP, and SMB) were discovered. These results provide the foundational footprinting data required for the next phases of vulnerability assessment and exploitation.

---

## ⚖️ Authorization & Disclaimer
This activity was performed against an authorized, locally hosted VMware/VirtualBox laboratory environment containing a deliberately vulnerable Metasploitable target. This project was conducted strictly for educational and cybersecurity training purposes. Network scanning and penetration testing should **only** be performed against systems for which explicit, written authorization has been obtained.
