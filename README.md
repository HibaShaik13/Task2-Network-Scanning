# Task2-Network-Scanning
# Task 2: Network Security & Scanning

**Timeline:** Days 13–24
**Objective:** Learn reconnaissance, port/service scanning, vulnerability assessment, traffic analysis, and basic firewall configuration.

## What was done
- **Reconnaissance**
  - Passive: `whois`, `nslookup`, Google dorking (`site:google.com filetype:pdf`), OSINT-style search
  - Active: Ping sweep across the lab subnet, banner grabbing on Metasploitable2 (revealed vsFTPd 2.3.4)
- **Port & Service Scanning**
  - TCP SYN scan, UDP scan, OS detection, and a combined service-version + OS scan saved as a report
- **Vulnerability Assessment**
  - Manually cross-referenced detected service versions against known CVEs, categorized Critical/High/Medium/Low
- **Packet Analysis with Wireshark**
  - Captured an FTP login session, showing credentials sent in plain text
  - Simulated a SYN flood with `hping3` and captured the attack pattern (127,000+ packets)
- **Firewall Basics**
  - Created and tested `iptables` rules (INPUT vs. OUTPUT chains), demonstrated blocking outbound traffic on port 21

## Key findings
| Service | Version | Severity | Issue |
|---|---|---|---|
| vsFTPd | 2.3.4 | Critical | Known backdoor (CVE-2011-2523) |
| Samba | 3.X | Critical | Remote code execution (CVE-2007-2447) |
| UnrealIRCd | (detected) | Critical | Known trojaned source (2010 incident) |
| Apache httpd | 2.2.8 | High | Multiple known CVEs, unsupported branch |
| OpenSSH | 4.7p1 | Medium | Older version, minor known issues |

## Deliverables
- [Network Scanning Report (DOCX)](./Task2_Network_Scanning_Report.docx)
- [Nmap Scan Report (raw output)](./nmap_scan_report.txt)
- [Manual Vulnerability Assessment (Doc)](./vulnerability-assessment.md)

## Lab network (same as Task 1)
| Machine | IP Address | Role |
|---|---|---|
| Kali Linux | 192.168.56.101 | Attacker |
| Metasploitable2 | 192.168.56.102 | Target |
