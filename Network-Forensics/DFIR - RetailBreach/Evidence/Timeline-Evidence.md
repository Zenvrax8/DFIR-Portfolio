# Timeline Evidence

## Purpose

This document reconstructs the chronological sequence of events observed during the RetailBreach investigation.

The timeline was developed through analysis of HTTP requests, packet timestamps, HTTP stream reconstruction, and session activity captured within the provided packet capture (PCAP).

> **Note:** Packet numbers and screenshots referenced below correspond to the evidence contained within the **Evidence/Screenshots** directory.

---

| Phase | Event | Evidence |
|-------|-------|----------|
| 1 | External attacker (`111.224.180.128`) initiates reconnaissance against the ShopSphere web application. | HTTP GET requests originating from attacker IP. |
| 2 | Automated directory enumeration performed using **Gobuster** to discover hidden application resources. | HTTP User-Agent header identifies Gobuster. |
| 3 | Hidden application endpoints and administrative resources are discovered. | Multiple HTTP GET requests to application directories. |
| 4 | Attacker submits a malicious Stored XSS payload through `reviews.php`. | HTTP POST request containing the encoded JavaScript payload. |
| 5 | The malicious JavaScript payload is successfully stored within the web application. | HTTP response confirming successful submission. |
| 6 | An administrator accesses the compromised `reviews.php` page. | HTTP GET request for `reviews.php` containing the injected payload. |
| 7 | The malicious JavaScript executes within the administrator's browser and exfiltrates the authenticated PHP session cookie. | HTTP request containing the stolen `PHPSESSID` value. |
| 8 | The attacker reuses the stolen session cookie to hijack the administrator's authenticated session. | Subsequent HTTP requests containing the compromised session identifier. |
| 9 | Administrative resources become accessible to the attacker. | Authenticated requests to administrative pages (`dashboard.php`). |
| 10 | The attacker exploits the vulnerable `log_viewer.php` script. | HTTP requests targeting `log_viewer.php`. |
| 11 | A directory traversal payload is supplied through the `file` parameter. | `../../../../../../etc/passwd` observed within the HTTP request. |
| 12 | The application returns the contents of `/etc/passwd`, confirming successful Local File Inclusion (LFI). | HTTP response containing the sensitive system file. |
| 13 | Investigation completed with identification of attacker infrastructure, malicious payloads, compromised session, exploited application components, and Indicators of Compromise (IOCs). | Correlation of all forensic evidence. |

---

## Attack Chain Summary

```text
Reconnaissance
        │
        ▼
Directory Enumeration (Gobuster)
        │
        ▼
Stored XSS Injection
        │
        ▼
Administrator Visits Compromised Page
        │
        ▼
PHP Session Cookie Theft
        │
        ▼
Session Hijacking
        │
        ▼
Administrative Access
        │
        ▼
Local File Inclusion (LFI)
        │
        ▼
Sensitive File Access (/etc/passwd)
```

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Evidence/Investigation-Queries.md`
- `Artifacts/Indicators-of-Compromise.md`
- `Artifacts/MITRE-ATTACK-Mapping.md`