# 🛡️ TryHackMe (THM) Writeups & Lab Notes

A personal repository of hands-on penetration testing notes, command outputs, and step-by-step walkthroughs documented while completing rooms on [TryHackMe](https://tryhackme.com/).

---

## 📋 Completed Rooms

| # | Room Name | Focus Areas / Tools Used | Status |
| :--- | :--- | :--- | :---: |
| 1 | [Basic Pentesting](./1.%20Basic%20Pentesting%20(THM%20Room).md) | Nmap, Nikto, SMB Enumeration (`enum4linux`, `smbclient`), Hydra, John the Ripper (`ssh2john`) | ✅ Completed |
| 1.1 | [Takeover](./1.1%20Takeover%20(Tryhackme%20room).md) | Nmap, Nikto, Directory & VHost Fuzzing (`dirsearch`, `ffuf`), SSL/TLS Certificate Inspection | ✅ Completed |

---

## 🛠️ Methodology & Toolkit

Each writeup follows a structured penetration testing workflow:

1. **Reconnaissance & Scanning** – Port scanning and service version detection (`nmap -sC -sV`).
2. **Enumeration** – Web directory brute-forcing (`nikto`, `dirsearch`), virtual host/subdomain discovery (`ffuf`), and SMB share enumeration (`enum4linux`, `smbclient`).
3. **Exploitation & Credential Access** – Password brute-forcing (`hydra`), SSH key cracking (`ssh2john` + `john`), and SSL certificate inspection.
4. **Post-Exploitation & Privilege Escalation** – Lateral movement and flag capture.

---

## 📂 Note Structure

Every `.md` file in this repository is organized using a consistent format:
* **Metadata:** Tags, room status, and target/attacker IP addresses.
* **Commands & Raw Output:** Exact terminal commands executed alongside their full outputs for easy reference.
* **Step-by-Step Findings:** Discovered usernames, credentials, subdomains, and flags.

---

## ⚠️ Disclaimer

All techniques, tools, and walkthroughs documented in this repository were performed strictly within authorized, isolated TryHackMe lab environments for educational purposes only.
