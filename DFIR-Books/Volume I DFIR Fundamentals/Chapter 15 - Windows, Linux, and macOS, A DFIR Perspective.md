# Chapter 15 – Windows, Linux, and macOS: A DFIR Perspective

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - The similarities and differences between Windows, Linux, and macOS
> - Where digital evidence is commonly stored on each operating system
> - The most important forensic artifacts for each platform
> - Common attack techniques targeting each operating system
> - Challenges investigators face when analyzing different operating systems
> - Best practices for cross-platform investigations

---

# 1. Introduction

Imagine three different cities.

Each city has:

- Roads
- Buildings
- Hospitals
- Police stations
- Schools

Although they all serve the same purpose, their layouts are completely different.

A visitor cannot assume that every city is organized in the same way.

Operating systems are similar.

Windows, Linux, and macOS all allow users to:

- Store files
- Run applications
- Connect to networks
- Create user accounts
- Access the internet

However, they organize data differently.

For a DFIR investigator, understanding these differences is essential for locating evidence quickly and accurately.

---

# 2. Common Goals of Every Operating System

Regardless of platform, every operating system must:

- Manage files and storage
- Allocate memory
- Run processes
- Authenticate users
- Control permissions
- Communicate over networks
- Record system events

These common functions generate digital evidence.

The difference lies in **how** and **where** each operating system stores that evidence.

---

# 3. Windows from a DFIR Perspective

Windows is the most common operating system encountered in enterprise investigations.

### Common Sources of Evidence

- Windows Event Logs
- Windows Registry
- Prefetch
- Amcache
- Shimcache
- UserAssist
- Jump Lists
- LNK (Shortcut) Files
- ShellBags
- SRUM Database
- Recycle Bin
- Browser History
- NTFS Metadata

### Common Attack Techniques

- PowerShell abuse
- Scheduled Tasks
- Registry Run Keys
- Service creation
- Credential dumping
- Remote Desktop Protocol (RDP)
- Office macro attacks

Because Windows creates many forensic artifacts automatically, it often provides investigators with a rich source of evidence.

---

# 4. Linux from a DFIR Perspective

Linux is widely used for:

- Web servers
- Cloud infrastructure
- Containers
- Databases
- Enterprise services

### Common Sources of Evidence

- System logs
- Authentication logs
- Bash history
- Cron jobs
- SSH configuration
- Package manager logs
- Process information
- File permissions
- Journal logs (systemd)

### Common Attack Techniques

- SSH brute-force attacks
- Privilege escalation
- Cron job persistence
- Malicious shell scripts
- Web shell deployment
- Misconfigured services

Linux investigations often rely heavily on log analysis and command-line artifacts.

---

# 5. macOS from a DFIR Perspective

macOS is commonly encountered in:

- Corporate executive devices
- Creative industries
- Personal laptops
- Mobile application development

### Common Sources of Evidence

- Unified Logs
- Spotlight database
- Safari history
- LaunchAgents
- LaunchDaemons
- Keychain
- APFS metadata
- User preferences
- Application logs

### Common Attack Techniques

- Malicious LaunchAgents
- Credential theft
- Browser compromise
- Persistence using LaunchDaemons
- Abuse of AppleScript
- Malicious applications

Although macOS has fewer enterprise deployments than Windows, it remains an important platform in many investigations.

---

# 6. Comparing the Three Operating Systems

| Feature | Windows | Linux | macOS |
|---------|----------|--------|--------|
| Primary File Systems | NTFS, FAT32, exFAT | EXT4, XFS, Btrfs | APFS, HFS+ |
| Typical Environment | Enterprise desktops and servers | Servers, cloud, containers | Corporate and personal workstations |
| Key Logs | Event Logs | Syslog / Journal Logs | Unified Logs |
| Common Persistence | Registry, Services, Scheduled Tasks | Cron Jobs, Services | LaunchAgents, LaunchDaemons |
| Popular Investigation Focus | Registry, Event Logs, User Artifacts | Logs, Permissions, Shell Activity | Unified Logs, APFS, Keychain |

Each platform requires different investigative techniques.

---

# 7. Cross-Platform Investigations

Modern organizations rarely use only one operating system.

A single incident may involve:

- A Windows workstation
- A Linux web server
- A macOS executive laptop
- Cloud infrastructure

Investigators must correlate evidence across all of these systems.

For example:

- A phishing email is opened on Windows.
- Stolen credentials are used to access a Linux server.
- Sensitive files are downloaded to a macOS laptop.

Understanding each operating system allows investigators to reconstruct the complete attack.

---

# 8. Challenges in Cross-Platform DFIR

Investigators commonly encounter challenges such as:

- Different file systems
- Different timestamp formats
- Different logging mechanisms
- Different authentication methods
- Different persistence techniques
- Different command-line tools

Despite these differences, the investigative process remains the same:

1. Collect evidence.
2. Preserve integrity.
3. Correlate artifacts.
4. Reconstruct the timeline.
5. Report findings.

---

# 9. Real-World Example

An organization experiences a ransomware attack.

The investigation reveals:

- A Windows workstation received a phishing email.
- Stolen credentials were used to access a Linux file server through SSH.
- Confidential documents were copied to a macOS laptop belonging to a contractor.
- The ransomware later encrypted Windows file shares.

By combining evidence from all three operating systems, investigators identified the complete attack path and determined how the compromise spread through the environment.

---

# 10. Common Mistakes

New investigators often:

- Assume all operating systems store evidence in the same locations.
- Focus only on Windows systems.
- Ignore Linux server logs.
- Overlook macOS artifacts.
- Fail to normalize timestamps across platforms.
- Use operating system-specific assumptions during analysis.

These mistakes can leave important evidence undiscovered.

---

# 11. Best Practices

Professional investigators should:

- Learn the forensic strengths of each operating system.
- Understand where evidence is stored on each platform.
- Correlate evidence across systems.
- Normalize timestamps before building timelines.
- Preserve evidence using platform-appropriate acquisition methods.
- Keep platform-specific documentation during investigations.

Strong investigators adapt their techniques to the operating system they are examining.

---

# Remember This

- Windows, Linux, and macOS perform similar functions but store evidence differently.
- Windows investigations often focus on Registry, Event Logs, and user artifacts.
- Linux investigations rely heavily on logs, permissions, and shell history.
- macOS investigations commonly examine Unified Logs, APFS, and LaunchAgents.
- Modern investigations frequently involve multiple operating systems.
- The investigative methodology remains consistent, even when the platforms differ.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Windows Event Logs | Windows logging system that records operating system and application events |
| Windows Registry | Hierarchical database storing Windows configuration settings |
| Syslog | Standard logging system used by many Linux distributions |
| Unified Logs | Centralized logging framework used by macOS |
| LaunchAgent | A macOS mechanism for automatically starting user-level programs |
| Cron Job | A scheduled task commonly used on Linux systems |

---

# Chapter Summary

In this chapter, you learned:

- The major similarities and differences between Windows, Linux, and macOS
- Where investigators commonly find digital evidence on each platform
- Common attack and persistence techniques
- Challenges associated with cross-platform investigations
- Best practices for analyzing evidence across multiple operating systems

Successful DFIR investigators understand that while every operating system has unique artifacts and behaviors, the core investigative principles remain the same: preserve evidence, analyze artifacts, correlate findings, and reconstruct events based on reliable evidence.

---

# Review Questions

1. Why do Windows, Linux, and macOS require different forensic approaches?
2. Name five common Windows forensic artifacts.
3. Which Linux artifacts are useful for investigating user activity?
4. What are LaunchAgents, and why are they important on macOS?
5. Why are timestamp differences important in cross-platform investigations?
6. What challenges do investigators face when analyzing multiple operating systems?
7. Why is artifact correlation important in a cross-platform investigation?
8. What investigative principles remain the same regardless of operating system?

---

# Practical Exercise

A multinational company reports a suspected compromise involving:

- A Windows employee workstation
- A Linux web server
- A macOS executive laptop

Create an investigation strategy by answering:

- Which artifacts would you collect from each operating system?
- How would you preserve evidence from each platform?
- How would you correlate timestamps across all three systems?
- Which indicators would help you determine whether the incidents are related?
- How would you present your findings in a unified investigation report?

Your objective is to demonstrate how a DFIR investigator approaches incidents that span multiple operating systems.

---

# What's Next?

In the next chapter, we will explore **Common Sources of Digital Evidence**, examining where investigators collect evidence—from disks, memory, logs, cloud platforms, mobile devices, and networks—and how each source contributes to a complete forensic investigation.