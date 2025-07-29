#Project_2 Walkthrough — Nmap & Wireshark Lab

##Step 1: Scanning My Router with Nmap
To start this lab, I wanted to understand how to use nmap on a real device in my home network. I chose to scan my router (192.168.1.1) to see what services were exposed internally.
**Command Used:** sudo nmap 192.168.1.1
This is the most basic Nmap scan — it checks the top 1000 TCP ports using the default scan type (SYN scan when run with root/sudo). 
**Purpose:**
To identify what services and ports are open on my home router. This is a real-world scenario: internal reconnaissance is a common technique used by both attackers and defenders during network assessments.
![Nmap Scan of Router](screenshots/Nmap_start.png)
 
**Outcome:** 
The scan showed 7 open ports:
Port	State	Service
21	open	ftp
53	open	domain
80	open	http
139	open	netbios-ssn
445	open	microsoft-ds
1900	open	upnp
8200	open	trivnet1

**What I learned:** 
This scan gave me a basic idea of what services are exposed on my local network. Some ports stood out to me:
•	**FTP (21):** Used for file transfers — I’ll try checking if anonymous login is allowed.
•	**HTTP (80):** There’s probably a web interface running here.
•	**139 and 445 (NetBIOS and SMB):** These are often used for Windows file sharing. I noted them down for deeper enumeration later.
•	**UPnP (1900):** Might be useful for discovering devices on the network.
•	**Port 8200 (trivnet1):** associated with Bomgar, a remote support and access tool. Specifically, it's used as a backup /rollover port for port 443.




