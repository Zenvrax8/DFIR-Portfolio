# Investigation Queries

## Purpose

This document contains the Wireshark display filters and investigation techniques used throughout the RetailBreach forensic investigation.

These queries were used to identify attacker activity, reconstruct the attack timeline, validate evidence, and answer the investigation objectives.

> **Note:** The filters documented below represent the primary investigation workflow. Additional packet analysis was performed using HTTP Stream reconstruction, packet inspection, and manual traffic correlation.

---

# Initial Reconnaissance

| Purpose | Wireshark Filter |
|----------|------------------|
| Identify attacker traffic | `ip.src == 111.224.180.128` |
| View HTTP traffic | `http` |
| View HTTP GET requests | `http.request.method == "GET"` |
| View HTTP POST requests | `http.request.method == "POST"` |

---

# Directory Enumeration

| Purpose | Wireshark Filter |
|----------|------------------|
| Identify directory brute-force requests | `http.user_agent contains "gobuster"` |
| Locate discovered application resources | `ip.src == 111.224.180.128 && http` |

---

# Stored Cross-Site Scripting (XSS)

| Purpose | Wireshark Filter |
|----------|------------------|
| Review review page requests | `http.request.uri contains "reviews.php"` |
| Locate malicious POST request | `http.request.method == "POST" && http.request.uri contains "reviews.php"` |
| Inspect injected payload | **Follow HTTP Stream** |

---

# Session Hijacking

| Purpose | Wireshark Filter |
|----------|------------------|
| Locate stolen session cookie | `http.cookie contains "PHPSESSID"` |
| Search for compromised session token | `http contains "lqkctf24s9h9lg67teu8uevn3q"` |
| Review attacker HTTP requests | `ip.src == 111.224.180.128` |

---

# Local File Inclusion (LFI)

| Purpose | Wireshark Filter |
|----------|------------------|
| Locate vulnerable script | `http.request.uri contains "log_viewer.php"` |
| Search for directory traversal attempts | `http contains "../"` |
| Inspect LFI exploitation | **Follow HTTP Stream** |

---

# Timeline Reconstruction

| Purpose | Wireshark Filter |
|----------|------------------|
| Review all attacker activity | `ip.src == 111.224.180.128` |
| Correlate administrator activity | `http.request.uri contains "reviews.php"` |
| Validate attack sequence | Packet timestamps + HTTP Stream analysis |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Evidence/Timeline-Evidence.md`
- `Artifacts/Indicators-of-Compromise.md`