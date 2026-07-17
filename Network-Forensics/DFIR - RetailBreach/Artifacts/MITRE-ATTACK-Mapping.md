# MITRE ATT&CK Mapping

## Purpose

This document maps the adversary behavior observed during the RetailBreach investigation to the MITRE ATT&CK framework.

The mapping is based on forensic analysis of the captured network traffic and documents the tactics and techniques used by the attacker throughout the attack lifecycle.

> **Note:** This mapping represents the techniques directly observed within the packet capture. No techniques have been inferred without supporting evidence.

---

| Attack Phase | MITRE Tactic | Technique | Technique ID | Evidence |
|--------------|--------------|-----------|--------------|----------|
| Directory Enumeration | Reconnaissance | Gather Victim Network Information | T1590 | The attacker performed automated directory enumeration using Gobuster to identify accessible application resources. |
| Stored XSS Exploitation | Initial Access | Exploit Public-Facing Application | T1190 | A Stored Cross-Site Scripting (XSS) vulnerability was exploited through `reviews.php`. |
| Cookie Theft | Credential Access | Steal Web Session Cookie | T1539 | Malicious JavaScript exfiltrated the administrator's authenticated `PHPSESSID` cookie. |
| Malicious Script Execution | Defense Evasion | Exploitation for Client Execution | T1203 | The injected JavaScript executed within the administrator's browser after visiting the compromised page. |
| Session Hijacking | Persistence | Valid Accounts | T1078 | The attacker reused the stolen administrator session cookie to maintain authenticated access. |
| Administrative Access | Privilege Escalation | Valid Accounts | T1078 | The stolen session token provided unauthorized administrative privileges. |
| Administrative Resource Discovery | Discovery | File and Directory Discovery | T1083 | Administrative resources and application files were enumerated during reconnaissance and subsequent authenticated access. |
| Local File Inclusion | Initial Access | Exploit Public-Facing Application | T1190 | The attacker exploited the vulnerable `log_viewer.php` script using a directory traversal payload. |
| Sensitive File Collection | Collection | Data from Local System | T1005 | Successful retrieval of `/etc/passwd` through the Local File Inclusion vulnerability. |

---

## Attack Progression

| Step | Activity | ATT&CK Technique |
|------|----------|------------------|
| 1 | Directory brute-force using Gobuster | T1590 |
| 2 | Discovery of hidden application resources | T1083 |
| 3 | Stored XSS payload injection | T1190 |
| 4 | Administrator executes malicious JavaScript | T1203 |
| 5 | Administrator session cookie stolen | T1539 |
| 6 | Stolen session reused for authentication | T1078 |
| 7 | Administrative dashboard accessed | T1078 |
| 8 | Local File Inclusion exploited | T1190 |
| 9 | Sensitive system file collected | T1005 |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/Indicators-of-Compromise.md`
- `Artifacts/Challenge-Answers.md`
- `Evidence/Timeline-Evidence.md`