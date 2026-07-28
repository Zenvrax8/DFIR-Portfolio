# Chapter 18 – Indicators of Compromise (IOCs), Indicators of Attack (IOAs), and Tactics, Techniques, and Procedures (TTPs)

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What IOCs, IOAs, and TTPs are
> - The differences between them
> - Why each is important during an investigation
> - How investigators identify and use indicators
> - How TTPs relate to the MITRE ATT&CK framework
> - Common mistakes when interpreting indicators
> - Best practices for documenting and sharing findings

---

# 1. Introduction

Imagine a detective investigating a series of burglaries.

At one house, they find:

- A muddy boot print.
- A broken window.
- A discarded crowbar.

These are **clues** left behind after the crime.

However, the detective also notices that every burglary follows the same pattern:

- The burglar enters through a rear window.
- They disable the alarm first.
- They search the master bedroom before leaving.

These recurring behaviors reveal **how** the burglar operates.

Cyber investigations work the same way.

Some evidence tells us **what happened**.

Other evidence tells us **how the attacker operates**.

Understanding both is essential.

---

# 2. What is an Indicator of Compromise (IOC)?

An **Indicator of Compromise (IOC)** is a piece of evidence that suggests a system may have been compromised.

Think of an IOC as a **digital fingerprint** left behind after an attack.

Examples include:

- Malicious IP addresses
- Malicious domain names
- File hashes
- Malware filenames
- Suspicious registry keys
- Known phishing URLs
- Command and Control (C2) server addresses

IOCs help investigators identify systems that may have been affected.

---

# 3. What is an Indicator of Attack (IOA)?

An **Indicator of Attack (IOA)** describes suspicious behavior that may indicate an attack is occurring or has recently occurred.

Unlike IOCs, IOAs focus on **behavior**, not specific artifacts.

Examples include:

- PowerShell launching from Microsoft Word
- A process injecting code into another process
- Multiple failed logins followed by a successful login
- A user creating a new administrator account unexpectedly
- Large amounts of data being compressed before transfer

IOAs help detect attacks even when the attacker changes tools or malware.

---

# 4. What are Tactics, Techniques, and Procedures (TTPs)?

**TTPs** describe **how threat actors operate**.

They are generally more stable than specific malware or infrastructure.

- **Tactic** – The attacker's objective (for example, gaining persistence).
- **Technique** – The method used to achieve that objective (for example, creating a scheduled task).
- **Procedure** – The specific implementation used by a particular threat actor.

TTPs help investigators understand attacker behavior rather than focusing only on technical artifacts.

---

# 5. IOC vs IOA vs TTP

| IOC | IOA | TTP |
|-----|-----|-----|
| Evidence of compromise | Suspicious behavior | Attacker methodology |
| Often found after an attack | Often detected during an attack | Observed across multiple attacks |
| Can change quickly | More difficult for attackers to avoid | Usually remains consistent over time |
| Examples: IPs, hashes, domains | Examples: privilege escalation, code injection | Examples: phishing, credential dumping, scheduled task persistence |

Understanding the differences allows investigators to build stronger detections and investigations.

---

# 6. The MITRE ATT&CK Framework

The **MITRE ATT&CK** framework organizes known adversary behaviors into tactics and techniques.

Examples of tactics include:

- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Credential Access
- Discovery
- Lateral Movement
- Collection
- Exfiltration
- Impact

Each tactic contains multiple techniques describing how attackers commonly achieve their objectives.

Investigators often map observed TTPs to MITRE ATT&CK during incident reporting.

---

# 7. How Investigators Use Indicators

During an investigation, analysts may:

- Search for known malicious file hashes (IOCs).
- Review logs for suspicious process behavior (IOAs).
- Identify persistence mechanisms such as scheduled tasks (TTPs).
- Compare findings with threat intelligence reports.
- Map attacker behavior to MITRE ATT&CK.

Combining these approaches provides a more complete understanding of the incident.

---

# 8. Real-World Example

An employee opens a phishing attachment.

The investigation reveals:

### Indicators of Compromise (IOCs)

- Malicious domain: `example-malicious.com`
- File hash matching known malware
- Connection to a known C2 IP address

### Indicators of Attack (IOAs)

- Microsoft Word launches PowerShell.
- PowerShell downloads an executable.
- A new administrator account is created.

### TTPs

- Initial Access through phishing.
- Persistence using a scheduled task.
- Credential Access through password dumping.
- Data Exfiltration over HTTPS.

Each category provides different but complementary information about the attack.

---

# 9. Why TTPs Matter More Over Time

Attackers frequently change:

- Malware names
- File hashes
- Domains
- IP addresses

However, they often continue to use similar techniques and procedures.

For example:

An attacker may replace one malware family with another, but still:

- Gain access through phishing.
- Execute PowerShell commands.
- Create scheduled tasks.
- Steal credentials.

This is why behavioral analysis has become increasingly important in modern DFIR and threat hunting.

---

# 10. Common Mistakes

New investigators often:

- Treat IOCs and IOAs as the same thing.
- Focus only on known malware hashes.
- Ignore attacker behavior.
- Fail to map findings to MITRE ATT&CK.
- Assume the absence of IOCs means the system is safe.

Behavior often reveals attacks that traditional signatures miss.

---

# 11. Best Practices

Professional investigators should:

- Collect both artifact-based and behavioral evidence.
- Correlate IOCs with logs and forensic artifacts.
- Document observed IOAs.
- Map attacker behavior to MITRE ATT&CK techniques.
- Update detections as attacker behaviors evolve.
- Share validated indicators with the security team where appropriate.

Effective investigations combine technical evidence with behavioral analysis.

---

# Remember This

- **IOCs** are evidence that a compromise has occurred.
- **IOAs** describe suspicious behaviors that may indicate an attack.
- **TTPs** describe how attackers operate.
- TTPs generally remain useful longer than individual IOCs.
- MITRE ATT&CK helps investigators classify attacker behavior.
- Strong investigations combine IOCs, IOAs, and TTPs.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Indicator of Compromise (IOC) | Evidence suggesting that a system has been compromised |
| Indicator of Attack (IOA) | Suspicious behavior that may indicate an attack |
| TTP | Tactics, Techniques, and Procedures used by an attacker |
| MITRE ATT&CK | A knowledge base that categorizes adversary behaviors |
| Tactic | The attacker's objective |
| Technique | The method used to achieve a tactic |
| Procedure | The specific implementation of a technique by a threat actor |

---

# Chapter Summary

In this chapter, you learned:

- The differences between IOCs, IOAs, and TTPs
- How investigators use each during an investigation
- Why behavioral analysis is increasingly important
- How the MITRE ATT&CK framework helps classify attacker behavior
- Best practices for documenting and sharing indicators

Modern DFIR is no longer limited to searching for known malware or malicious IP addresses. Successful investigators combine artifact-based evidence, behavioral observations, and attacker methodologies to understand not only **what** happened, but also **how** and **why** it happened.

---

# Review Questions

1. What is an Indicator of Compromise (IOC)?
2. How does an Indicator of Attack (IOA) differ from an IOC?
3. What are Tactics, Techniques, and Procedures (TTPs)?
4. Why are TTPs often more valuable than individual IOCs?
5. What is the purpose of the MITRE ATT&CK framework?
6. Give three examples of IOCs.
7. Give three examples of IOAs.
8. Why should investigators map findings to MITRE ATT&CK?

---

# Practical Exercise

A company reports a suspected phishing attack that led to unauthorized access to sensitive data.

Develop an investigation plan by identifying:

- At least five possible IOCs.
- At least five possible IOAs.
- The likely TTPs used by the attacker.
- Which MITRE ATT&CK tactics and techniques might apply.
- How you would use these findings to improve future detections and incident response.

Your objective is to demonstrate how combining indicators and attacker behavior leads to a more complete understanding of a cyber incident.

---

# What's Next?

In the next chapter, we will explore **Introduction to Malware in DFIR**, learning what malware is, the major malware categories, common infection techniques, and how investigators identify, preserve, and analyze malware during forensic investigations.