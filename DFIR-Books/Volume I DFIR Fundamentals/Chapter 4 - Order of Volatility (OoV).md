# Chapter 4 – Order of Volatility (OoV)

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What the Order of Volatility (OoV) is
> - Why some evidence disappears faster than others
> - How investigators prioritize evidence collection
> - Common sources of volatile and non-volatile evidence
> - Best practices for collecting volatile evidence
> - Common mistakes made during evidence acquisition

---

# 1. Introduction

Imagine you arrive at a crime scene on a rainy day.

On the muddy ground, you notice fresh footprints.

If you stop to photograph the house before documenting the footprints, the rain may wash them away.

Once they disappear, they are gone forever.

An experienced investigator understands that some evidence is temporary and must be collected immediately.

The same principle applies in digital forensics.

Some digital evidence disappears within seconds.

Other evidence can remain on a hard drive for months or even years.

To avoid losing valuable information, investigators follow a principle called the **Order of Volatility (OoV)**.

---

# 2. What is the Order of Volatility?

The **Order of Volatility (OoV)** is the sequence in which digital evidence should be collected based on how quickly it may change or disappear.

Simply put,

> **Collect the evidence that disappears first before collecting evidence that lasts longer.**

The longer an investigator waits, the greater the chance that volatile evidence will be lost.

---

# 3. What is Volatile Data?

**Volatile data** is information that exists only while a system is powered on or actively running.

Once the system is shut down, restarted, or loses power, this data may be permanently lost.

Examples include:

- Running processes
- Active network connections
- Logged-in users
- Open files
- Command history
- Encryption keys stored in memory
- Clipboard contents
- RAM contents

This information cannot usually be recovered after shutdown.

---

# 4. What is Non-Volatile Data?

**Non-volatile data** remains available even after a system is powered off.

Examples include:

- Documents
- Installed software
- Windows Registry
- Event Logs
- Browser history
- Images
- Videos
- Databases
- Emails
- Hard drive contents

Although this data can still change over time, it is generally much more persistent than volatile data.

---

# 5. Why is the Order of Volatility Important?

Imagine investigators receive a report that a server has been compromised.

They immediately shut down the server.

Although this may stop the attack, it also destroys valuable evidence stored in memory, such as:

- Malware running only in RAM
- Active network sessions
- Command and Control (C2) connections
- Decryption keys
- Injected code
- Unsaved command history

The investigation becomes significantly more difficult because critical evidence has been lost.

Following the Order of Volatility helps investigators preserve information before it disappears.

---

# 6. Typical Order of Volatility

The following is a commonly accepted Order of Volatility, starting with the most volatile evidence.

| Priority | Evidence |
|----------|----------|
| 1 | CPU Registers and Cache |
| 2 | RAM (Memory) |
| 3 | Running Processes |
| 4 | Active Network Connections |
| 5 | Logged-in Users and Sessions |
| 6 | Temporary Files |
| 7 | Local Storage (Hard Drives / SSDs) |
| 8 | Remote Logs and Backups |
| 9 | Archived Data |

The exact order may vary depending on the situation, but the guiding principle remains the same:

**Collect the most volatile evidence first.**

---

# 7. Understanding Volatility with an Analogy

Imagine three pieces of evidence.

### Ice Cube

Melts within minutes.

Equivalent to:

- RAM
- Active network sessions
- Running processes

---

### Wet Ink

Can remain for several hours.

Equivalent to:

- Temporary files
- Session information
- Cached browser data

---

### Carved Stone

Can remain for years.

Equivalent to:

- Hard drives
- Archived backups
- Documents
- Database files

A good investigator collects the "ice cube" before it melts.

---

# 8. Common Sources of Volatile Evidence

Volatile evidence includes:

### Memory (RAM)

Contains:

- Running malware
- Active processes
- Passwords
- Encryption keys
- Network connections
- Command history

---

### Active Network Connections

Reveal:

- Remote attackers
- C2 servers
- File transfers
- Open ports
- Connected systems

---

### Running Processes

Show:

- Legitimate applications
- Suspicious executables
- Malware
- Parent-child process relationships

---

### Logged-in Users

May identify:

- Active users
- Remote desktop sessions
- SSH sessions
- Administrator activity

---

### Clipboard

May contain:

- Passwords
- Cryptocurrency wallet addresses
- Sensitive text
- Commands copied by attackers

---

# 9. Real-World Example

A company discovers ransomware spreading through its network.

The first instinct is to pull the power cable from the infected server.

However, an experienced DFIR investigator pauses and asks:

"What evidence will we lose?"

Before shutting the system down, the investigator acquires:

- A memory image
- Active network connections
- Running processes
- Logged-in users
- Command history

Only after preserving this volatile evidence does the response team isolate the system and continue the investigation.

This approach provides a much clearer picture of the attack.

---

# 10. Balancing Investigation and Business Needs

In real incidents, investigators often face difficult decisions.

Sometimes:

- Leaving a compromised system running preserves evidence.
- Shutting it down immediately protects the business.

There is rarely a perfect answer.

DFIR professionals must balance:

- Evidence preservation
- Business continuity
- Safety
- Legal requirements
- Risk to the organization

This is why Incident Response and Digital Forensics work together.

---

# 11. Common Mistakes

New investigators often make mistakes such as:

- Powering off a system before acquiring memory.
- Rebooting a compromised server without documenting its state.
- Ignoring active network connections.
- Collecting disk images before volatile evidence.
- Assuming event logs contain everything.
- Forgetting that some malware exists only in memory.

These mistakes can permanently destroy valuable evidence.

---

# 12. Best Practices

To preserve volatile evidence effectively:

- Assess the situation before taking action.
- Follow your organization's incident response procedures.
- Acquire memory whenever appropriate.
- Document every action performed.
- Record timestamps accurately.
- Capture active network information.
- Preserve running process information.
- Avoid unnecessary interaction with the compromised system.
- Collect forensic disk images after volatile evidence has been preserved whenever circumstances allow.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Order of Volatility (OoV) | The sequence for collecting evidence based on how quickly it may disappear |
| Volatile Data | Data that may be lost when a system loses power or changes state |
| Non-Volatile Data | Data that persists after the system is powered off |
| Memory Acquisition | The process of capturing the contents of RAM |
| Active Session | A currently authenticated user or service session |

---

# Chapter Summary

In this chapter, you learned:

- What the Order of Volatility is
- Why volatile evidence must be collected first
- The difference between volatile and non-volatile data
- Common examples of volatile evidence
- How improper handling can permanently destroy valuable information
- Best practices for preserving time-sensitive evidence

The Order of Volatility is one of the most important concepts in DFIR because an investigator often has only one opportunity to collect certain evidence before it disappears forever.

---

# Review Questions

1. What is the Order of Volatility?
2. Why is RAM considered volatile evidence?
3. List five examples of volatile data.
4. What is the difference between volatile and non-volatile evidence?
5. Why can rebooting a compromised system affect an investigation?
6. What factors should investigators consider before shutting down a compromised system?
7. Why are active network connections important during an investigation?
8. What are some common mistakes investigators make when handling volatile evidence?

---

# Practical Exercise

A security analyst reports that a Windows server is communicating with an unknown external IP address.

Before taking any containment action, create a list of the evidence you would prioritize collecting.

For each item, explain **why** it should be collected before shutting down or rebooting the server.

The goal of this exercise is to practice applying the Order of Volatility to a realistic incident response scenario.

---

# What's Next?

In the next chapter, we will study the **Incident Response Lifecycle**, exploring the structured process organizations use to prepare for, detect, contain, eradicate, recover from, and learn from cybersecurity incidents. This lifecycle forms the operational backbone of every successful DFIR investigation.