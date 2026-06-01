# 🎯 TryHackMe Writeups & Walkthroughs

Welcome to my TryHackMe CTF repository! This directory contains my step-by-step documentation, methodologies, and evidence screenshots for various rooms I've solved on the platform.

The walkthroughs are organized below by room name, along with a quick overview of the key security concepts, vulnerabilities, and exploitation techniques encountered in each box.

---

## 🗺️ Repository Navigation

| Room Name | Primary Concepts & Techniques Covered | Walkthrough Link |
| :--- | :--- | :--- |
| **The Marketplace** | Stored XSS, Cookie Stealing, Blind/Union SQLi, Tar Wildcard Injection, Docker Escape | [View Walkthrough](./Marketplace/) |
| **Red** | Local File Inclusion (LFI), `.bash_history` Analysis, Traffic Hijacking (`/etc/hosts`), PwnKit (`pkexec`) | [View Walkthrough](./Red/) |
| **Startup** | Anonymous FTP Write Access, Reverse Shell Injection, PCAP Traffic Analysis, Cronjob Exploitation | [View Walkthrough](./Startup/) |
| **0day** | CGI Directory Enumeration, Shellshock (CVE-2014-6271), Linux Kernel Exploitation (`overlayfs`) | [View Walkthrough](./0day/) |
| **Boiler** | Deep Web Brute-Forcing, Unauthenticated App RCE (`sar2html`), Cleartext Credentials, SUID `find` | [View Walkthrough](./Boiler/) |
| **Checkmate** | Weak Default Administrative Panel Credentials, OSINT Formula Analysis, Targeted Wordlists via `crunch` & `hydra` | [View Walkthrough](./Checkmate/) |
| **Source** | Outdated Web Management Interfaces, Webmin 1.890 Exploit (CVE-2019-15107), Remote Code Execution (RCE) | [View Walkthrough](./Source/) |
| **Magician** | Subverting Image/File Upload Parsers, Local Privilege Escalation Vectors | [View Walkthrough](./Magician/) |
| **Injectics** | Web Form Inputs, Injection Vulnerabilities, Filter/Sanitization Bypasses | [View Walkthrough](./Injectics/) |
| **Include** | File Inclusion Flaws, Local Path Traversals, System Foothold Enumeration | [View Walkthrough](./Include/) |
| **Whats_your_name** | Web Form Parameter Tampering, Input Validation Bypasses | [View Walkthrough](./Whats_your_name/) |
| **Mr. Robot** | Web Robots Probing, Dictionary Attacks via Staged Wordlists, WordPress Theme Editing, SUID `nmap` | [View Walkthrough](./mr_robot/) |

---

## 🛠️ Tools & Technologies Used Throughout

Throughout these challenges, I frequently utilize industry-standard tools for penetration testing and vulnerability analysis:
* **Reconnaissance & Scanning:** `nmap`, `nikto`
* **Directory Brute-Forcing:** `gobuster`, `dirb`
* **Authentication Cracking:** `hydra`, `hashcat`, `crunch`
* **Traffic & Packet Analysis:** `wireshark`
* **Exploitation & Shells:** `netcat`, `rlwrap`, `metasploit-framework`

---
*Disclaimer: These writeups are intended strictly for educational purposes, documenting my personal growth, methodology, and technical progress along the SOC Analyst and Penetration Testing learning paths.*
