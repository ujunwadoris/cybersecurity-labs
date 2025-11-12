# Week 2 – Kali Linux Setup and Reconnaissance

## Objective
- Verify connectivity between Kali and Metasploitable
- Test communication with ping
- Discover hosts on the subnet
- Scan services and open ports

---

## Steps and Evidence

### 1. Verify IP Addresses
- Kali Linux IP: *192.168.56.103*
- Metasploitable IP: *192.168.56.104*

Screenshots:  
- ![Kali IP](week2_kali_ping.png)  
- ![Metasploitable IP](week2_metasploitable.png)  

---

### 2. Ping Test
- Kali → Metasploitable: Success (0% packet loss)  
- Metasploitable → Kali: Success (0% packet loss)  

Screenshots:  
- ![Kali Ping](week2_kali_ping.png)  
- ![Metasploitable Ping](week2_metasploitable_arp.png)  

---

### 3. ARP Table
- Verified communication and MAC addresses exchanged.  

Screenshot:  
- ![Kali ARP](week2_kali_arp.png)  
- ![Metasploitable ARP](week2_metasploitable_arp.png)  

---

### 4. Host Discovery with Netdiscover
- Detected live hosts in the subnet.  

Screenshot:  
- ![Netdiscover](week2_netdiscover.png)  

---

### 5. Service & Port Scanning with Nmap
- Used nmap -sV 192.168.56.104 to identify services.  
- Found open ports like FTP, SSH, HTTP, MySQL, PostgreSQL, Tomcat, etc.  

Screenshot:  
- ![Nmap Scan](week2_nmap_scan.png)  

---

## Summary
In Week 2, I:  
- Confirmed IP configuration for Kali and Metasploitable  
- Verified connectivity using ping  
- Used ARP to confirm communication  
- Ran Netdiscover for host detection  
- Performed Nmap scans to identify services  

This shows the environment is working and ready for exploitation labs in Week 3.
