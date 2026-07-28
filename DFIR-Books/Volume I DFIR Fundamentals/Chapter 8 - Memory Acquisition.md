# Chapter 8 – Memory Acquisition

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What memory acquisition is
> - Why RAM is one of the most valuable sources of digital evidence
> - The difference between memory acquisition and disk acquisition
> - Types of memory acquisition
> - Common memory acquisition tools
> - Challenges and limitations of memory acquisition
> - Best practices for preserving volatile evidence

---

# 1. Introduction

Imagine reading a book while someone is writing new pages faster than you can read them.

Every second, words are added, removed, and rewritten.

If someone suddenly burns the book, everything written inside is lost forever.

This is similar to **Random Access Memory (RAM).**

RAM constantly changes while a computer is running.

Applications start and stop.

Users log in and out.

Network connections open and close.

Malware executes, injects code into processes, and sometimes disappears without ever touching the hard drive.

Unlike a hard drive, RAM is temporary.

Once power is removed, its contents are usually lost.

For this reason, memory acquisition is often one of the first actions performed during a live forensic investigation.

---

# 2. What is Memory Acquisition?

**Memory Acquisition** is the process of capturing the contents of a computer's physical memory (RAM) while the system is running.

The captured data is commonly referred to as a:

- Memory Image
- Memory Dump
- RAM Dump

This snapshot allows investigators to analyze the system's memory even after the computer has been powered off.

---

# 3. Why is Memory Acquisition Important?

Many attacks leave little or no evidence on disk.

Examples include:

- Fileless malware
- In-memory malware
- Process injection
- Credential theft
- Active Command and Control (C2) sessions
- Encryption keys stored only in RAM

Without a memory image, this evidence may disappear permanently.

Memory acquisition helps investigators preserve information that cannot usually be recovered later.

---

# 4. What Can Be Found in Memory?

A memory image may contain valuable evidence such as:

### Running Processes

Every active process loaded into memory.

Examples:

- explorer.exe
- chrome.exe
- powershell.exe
- suspicious malware processes

---

### Network Connections

Investigators can identify:

- Active TCP sessions
- Remote IP addresses
- Listening ports
- Established connections

---

### Loaded DLLs

Applications load Dynamic Link Libraries (DLLs) into memory.

Unexpected or malicious DLLs may indicate code injection or malware activity.

---

### User Credentials

Depending on the operating system and security configuration, memory may contain:

- Passwords
- Password hashes
- Authentication tokens
- Kerberos tickets

---

### Encryption Keys

Some encryption keys exist only while a system is running.

Capturing memory before shutdown may allow investigators to recover them.

---

### Command History

Memory may reveal:

- PowerShell commands
- Command Prompt history
- Scripts executed by attackers

---

### Clipboard Data

Temporary clipboard contents can include:

- Passwords
- Sensitive documents
- Cryptocurrency addresses
- Commands

---

# 5. Memory Acquisition vs Disk Acquisition

| Memory Acquisition | Disk Acquisition |
|--------------------|------------------|
| Captures RAM | Captures storage devices |
| Collects volatile evidence | Collects persistent evidence |
| Must be performed while the system is running | Can usually be performed after shutdown |
| Evidence disappears when power is lost | Evidence usually remains after shutdown |
| Useful for detecting active attacks | Useful for reconstructing historical activity |

Both acquisition methods complement each other.

A complete investigation often requires both.

---

# 6. Challenges of Memory Acquisition

Memory acquisition is more difficult than disk imaging because:

- RAM changes constantly.
- The acquisition tool itself modifies memory.
- Malware may detect forensic tools.
- Large memory sizes require more storage.
- Improper acquisition may interrupt critical processes.

No memory acquisition is completely "perfect."

The goal is to minimize changes while preserving as much evidence as possible.

---

# 7. Common Memory Acquisition Tools

Several tools are commonly used in DFIR.

Examples include:

| Tool | Purpose |
|------|---------|
| WinPmem | Windows memory acquisition |
| Magnet RAM Capture | Memory acquisition for Windows |
| Belkasoft RAM Capturer | Lightweight RAM acquisition |
| DumpIt | Simple memory acquisition utility |
| LiME | Memory acquisition for Linux |

Different organizations choose tools based on operating system, licensing, and investigation requirements.

---

# 8. General Memory Acquisition Process

A typical workflow is:

```text
Identify Running System
          ↓
Document Current State
          ↓
Prepare Acquisition Tool
          ↓
Acquire Memory
          ↓
Calculate Hash Values
          ↓
Verify Integrity
          ↓
Secure Memory Image
          ↓
Analyze the Memory Dump
```

Documentation is essential throughout the process.

---

# 9. Real-World Example

A financial institution detects suspicious outbound traffic from a Windows server.

The server remains online.

Instead of shutting it down immediately, investigators:

1. Record the current system time.
2. Acquire a full memory image.
3. Calculate the SHA-256 hash of the memory dump.
4. Capture active network connections.
5. Document logged-in users.
6. Preserve the evidence.
7. Begin analysis using a memory forensics framework.

The investigation later reveals a fileless malware implant that existed only in RAM.

Without memory acquisition, this evidence would have been lost.

---

# 10. Common Mistakes

New investigators often make mistakes such as:

- Powering off a system before acquiring memory.
- Ignoring the Order of Volatility.
- Forgetting to document acquisition details.
- Failing to verify hash values.
- Using untrusted acquisition tools.
- Assuming disk evidence contains everything.

These mistakes can permanently destroy valuable evidence.

---

# 11. Best Practices

Professional investigators should:

- Acquire memory before shutting down a compromised system whenever appropriate.
- Minimize interaction with the live system.
- Document every action performed.
- Record acquisition timestamps.
- Use trusted acquisition tools.
- Verify memory dumps using cryptographic hashes.
- Preserve the original memory image.
- Analyze copies whenever practical.

Following these practices improves the reliability and reproducibility of the investigation.

---

# Key Terms

| Term | Meaning |
|------|---------|
| RAM | Random Access Memory |
| Memory Acquisition | Capturing the contents of RAM for forensic analysis |
| Memory Image | A snapshot of physical memory at a specific point in time |
| Memory Dump | Another term for a captured memory image |
| Volatile Evidence | Evidence that may be lost when a system loses power |
| Fileless Malware | Malware that primarily operates in memory rather than on disk |

---

# Chapter Summary

In this chapter, you learned:

- What memory acquisition is
- Why RAM is one of the most valuable sources of digital evidence
- The types of information that can be recovered from memory
- The differences between memory and disk acquisition
- Common acquisition tools
- Challenges and best practices for preserving volatile evidence

Memory acquisition is a critical capability in modern DFIR because many advanced threats leave their most valuable evidence in RAM. Capturing memory before it is lost can provide investigators with insights that are unavailable from disk analysis alone.

---

# Review Questions

1. What is memory acquisition?
2. Why is RAM considered volatile evidence?
3. Name five types of evidence that may be found in memory.
4. How does memory acquisition differ from disk acquisition?
5. Why is timing important during memory acquisition?
6. What challenges make memory acquisition more difficult than disk imaging?
7. Name three commonly used memory acquisition tools.
8. Why is memory acquisition especially important when investigating fileless malware?

---

# Practical Exercise

You receive an alert that a Windows server is communicating with an unknown external IP address, and the server remains powered on.

Create a memory acquisition plan by answering the following:

- What evidence would you preserve before shutting down the server?
- Which memory acquisition tool would you choose?
- How would you verify the integrity of the memory image?
- What documentation would you record during the acquisition?
- What additional volatile evidence would you collect alongside the memory dump?

Design your response as though you are preparing to brief a senior DFIR investigator before beginning the acquisition.

---

# What's Next?

In the next chapter, we will explore **Live Response vs Dead Box Forensics**, learning when investigators should analyze a running system, when they should perform offline analysis, and the advantages, risks, and trade-offs of each approach.