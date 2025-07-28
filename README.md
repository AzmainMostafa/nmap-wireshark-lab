# Nmap + Wireshark Lab (Project 2 of Cybersecurity Roadmap)

This project is part of my 12-month journey. In **Project 2**, I explored core **network scanning** and **traffic analysis** skills using two fundamental tools: **Nmap** and **Wireshark**.

---

## What I Learned

- Basics of networking: TCP, ports, services, IP addresses
- Nmap scanning techniques: SYN scan, ACK scan, FIN scan, XMAS scan, NULL scan, Ping scan
- Analyzing port behavior and service banners
- Using Wireshark to inspect and understand Nmap packet behavior
- Observing the network behavior of open, closed, and filtered ports
- Identifying and understanding exposed services (e.g. SMB on port 139)
- Real-world relevance: how attackers probe systems, and how defenders detect them

---

## Tools Used

- Kali Linux (VM)
- Nmap 7.95
- Wireshark
- Home network devices (router and other hosts)

---

## Key Activities

### 1. Nmap Port Scanning

I performed and documented multiple scan types:

- **SYN Scan** (`-sS`): Fast and stealthy scan for open ports
- **ACK Scan** (`-sA`): Checks if ports are filtered or unfiltered
- **FIN Scan** (`-sF`), **XMAS Scan** (`-sX`), **NULL Scan** (`-sN`): Bypass basic firewalls
- **Ping Scan** (`-sP` / `-sn`): Host discovery
- **Version Detection** (`-sV`): To reveal service version details
- **Specific Port Scans**: Focused scans on port `139` and other interesting ports

Each scan was run with `sudo`, and outputs were saved as screenshots.

### 2. Screenshots + Observations

- For each scan, I captured:
  - The **Nmap command**
  - The **terminal output**
  - A **Wireshark packet capture** filtered by specific flags (e.g., `tcp.flags.syn == 1`)
- Observed differences in TCP behavior for open, closed, and filtered ports
- Noted reset packets (RST), ACK replies, and lack of responses depending on port status

### 3. Analyzing Port 139

- Identified port `139` (NetBIOS/SMB) was open on my router (192.168.1.1)
- Performed service version detection: `Samba smbd 3.X – 4.X`
- Compared behavior with a filtered device (`192.168.1.149`)
- Captured and reviewed the traffic in Wireshark to understand service behavior

### 4. Traffic Analysis in Wireshark

- Inspected packet-level details of different Nmap scans
- Used filters like:
  - `tcp.flags.syn == 1`
  - `tcp.flags.ack == 1 && tcp.flags.syn == 0`
  - `icmp`
- Observed the three-way handshake and variations in responses
- Analyzed how filtered ports don’t respond (no SYN-ACK or RST)

---

## Real-World Relevance

| Role         | How this project helps                        |
|--------------|-----------------------------------------------|
| Red Team  | Understand how attackers map networks          |
| Blue Team | Learn to detect and defend against scans       |
| SOC Analyst | Analyze scan patterns in Wireshark or SIEM tools |
| Pentester  | Identify misconfigured or exposed services    |

---

## Project Structure

```bash
nmap-wireshark-lab/
├── README.md            # This file
├── walkthrough.md       # (Will contain detailed steps + screenshots)
├── screenshots/         # All terminal and Wireshark screenshots
│   ├── nmap-syn.png
│   ├── nmap-ack.png
│   ├── wireshark-syn.png
│   └── ...

