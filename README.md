# 🔍 Cybersecurity: Nmap Network Scanning

## 📖 Table of Contents
- [Objective](#-objective)
- [Tools & Environment](#️-tools--environment)
- [Practical Tasks Executed](#-practical-tasks-executed)
  - [1. Host Discovery (Ping Sweep)](#1-host-discovery-ping-sweep)
  - [2. TCP Port Scanning](#2-tcp-port-scanning)
  - [3. UDP Port Scanning](#3-udp-port-scanning)
  - [4. Service & Version Detection](#4-service--version-detection)
  - [5. OS Detection](#5-os-detection)
  - [6. Aggressive Scan & Output](#6-aggressive-scan--output)
  - [7. NSE Script Scanning](#7-nse-script-scanning)
- [Scan Report & Conclusion](#-scan-report--conclusion)

---

## 🎯 Objective
This project demonstrates practical network reconnaissance using Nmap. The objective is to identify live hosts, discover open ports, detect running services, and map out the operating systems and potential vulnerabilities within a target network.

## 🛠️ Tools & Environment
*   **Attacker Machine:** Kali Linux (IP: `10.145.8.153`)
*   **Target Machine:** Metasploitable 2 (IP: `10.145.8.91`)
*   **Tool:** Nmap (Network Mapper)

---

## 🚀 Practical Tasks Executed

### 1. Host Discovery (Ping Sweep)
Identified live hosts on the local subnet without performing a full port scan to remain stealthy.
*   **Command:** `nmap -sn 10.145.8.0/24`
*   **Result:**
<br>

![Host Discovery](images/host-discovery.png)

### 2. TCP Port Scanning
Scanned the target machine to identify all open TCP ports.
*   **Command:** `nmap -p- 10.145.8.91`
*   **Result:**
<br>

![TCP Port Scanning](images/tcp-port-scanning.png)

### 3. UDP Port Scanning
Targeted UDP ports to uncover services that are often missed by standard TCP scans (like DNS or SNMP).
*   **Command:** `sudo nmap -sU -F 10.145.8.91` *(Used -F for a fast scan of top 100 ports)*
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
*(Write 2-3 sentences here summarizing what you found. Example: "The Nmap reconnaissance on 10.145.8.91 revealed a highly vulnerable Metasploitable 2 instance running outdated vsftpd, Apache, and SSH services. The aggressive and NSE scans successfully identified multiple entry points for potential exploitation.")*
