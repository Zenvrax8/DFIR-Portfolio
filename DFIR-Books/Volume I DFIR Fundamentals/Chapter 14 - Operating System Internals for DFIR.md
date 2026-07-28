# Chapter 14 – Operating System Internals for DFIR

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What an operating system is
> - The major components of an operating system
> - How processes, memory, files, and users interact
> - Why operating system internals matter during forensic investigations
> - How attackers abuse operating system components
> - Common mistakes investigators make
> - Best practices for interpreting operating system evidence

---

# 1. Introduction

Imagine a large office building.

The building contains:

- Employees
- Managers
- Security guards
- Filing cabinets
- Meeting rooms
- Electricity
- Elevators

Without someone coordinating everything, the building would quickly become chaotic.

The **operating system (OS)** plays the same role inside a computer.

It manages hardware, software, users, memory, storage, and communication between applications.

Every action performed on a computer passes through the operating system in some way.

For a DFIR investigator, understanding how an operating system works is essential because most digital evidence originates from it.

---

# 2. What is an Operating System?

An **operating system** is software that manages computer hardware and provides services for applications and users.

It acts as the bridge between:

- Hardware
- Applications
- Users

Without an operating system:

- Programs cannot run.
- Files cannot be managed.
- Memory cannot be allocated.
- Devices cannot communicate effectively.

Common operating systems include:

- Microsoft Windows
- Linux
- macOS

Although they differ internally, they perform many of the same core functions.

---

# 3. Core Responsibilities of an Operating System

Every operating system performs several key tasks.

### Process Management

The OS starts, stops, schedules, and monitors running programs.

Examples:

- Opening a web browser
- Launching Microsoft Word
- Running antivirus software

Each running program becomes a **process**.

---

### Memory Management

The operating system allocates RAM to processes.

It ensures that multiple applications can run at the same time without interfering with one another.

Investigators often analyze memory management during memory forensics.

---

### File Management

The OS works with the file system to:

- Create files
- Delete files
- Read files
- Write files
- Control permissions

Many forensic artifacts are generated during these operations.

---

### User Management

The operating system authenticates users and controls access to resources.

Examples include:

- User accounts
- Groups
- Password policies
- Permissions

Unauthorized account creation is often an indicator of compromise.

---

### Device Management

The OS communicates with hardware such as:

- Keyboards
- USB drives
- Printers
- Network adapters
- Storage devices

Connecting external devices often creates forensic artifacts.

---

# 4. Understanding Processes

A **process** is a running instance of a program.

For example:

```text
Program on Disk
      │
      ▼
User Opens It
      │
      ▼
Running Process
```

Every process has information such as:

- Process ID (PID)
- Parent Process ID (PPID)
- Start time
- Memory usage
- Executable path
- User account

Investigators analyze these details to detect suspicious activity.

---

# 5. Parent and Child Processes

Processes often create other processes.

Example:

```text
explorer.exe
      │
      └── cmd.exe
              │
              └── powershell.exe
```

This relationship is called a **process tree**.

Unusual parent-child relationships can indicate malicious behavior.

Example:

```
winword.exe
      │
      └── powershell.exe
```

This may suggest a malicious Microsoft Word document launched PowerShell.

---

# 6. Memory and Processes

Every running process occupies memory.

Memory contains:

- Program instructions
- Variables
- Loaded DLLs
- Network information
- Temporary data

When a process ends, much of this information disappears.

This is why memory acquisition is critical during live investigations.

---

# 7. Users and Permissions

Operating systems enforce permissions to control access.

Examples include:

- Standard users
- Administrators
- Service accounts
- System accounts

Attackers frequently attempt to:

- Escalate privileges
- Create new administrator accounts
- Steal credentials
- Disable security controls

Understanding permissions helps investigators identify unauthorized actions.

---

# 8. Operating System Events

Operating systems constantly record activity.

Examples include:

- User logins
- Application launches
- Service installations
- Driver loading
- USB connections
- Scheduled task creation
- System startup and shutdown

These records become valuable forensic evidence.

---

# 9. How Attackers Abuse the Operating System

Attackers often misuse legitimate operating system features.

Examples include:

- Launching PowerShell scripts
- Creating scheduled tasks
- Adding administrator accounts
- Modifying registry settings
- Installing malicious services
- Injecting code into legitimate processes

Many attacks rely on built-in operating system functionality rather than custom malware.

---

# 10. Real-World Example

An organization detects unusual outbound network traffic.

During the investigation, analysts discover:

- `winword.exe` launched `powershell.exe`.
- PowerShell downloaded a malicious script.
- The script created a scheduled task for persistence.
- A new local administrator account was created.
- The malware communicated with an external server.

By understanding operating system internals, investigators reconstructed the entire attack chain.

---

# 11. Common Mistakes

New investigators often:

- Focus only on files while ignoring running processes.
- Overlook parent-child process relationships.
- Ignore user permissions.
- Fail to correlate operating system events.
- Assume every running process is legitimate.
- Ignore service and scheduled task activity.

These mistakes may allow attacker activity to go unnoticed.

---

# 12. Best Practices

Professional investigators should:

- Understand normal operating system behavior.
- Analyze process trees.
- Verify user account activity.
- Review system logs.
- Correlate operating system events with other artifacts.
- Document every finding.

Understanding how an operating system normally behaves makes abnormal behavior easier to identify.

---

# Remember This

- The operating system manages hardware, software, memory, files, and users.
- Every running application becomes a process.
- Processes have parent-child relationships that can reveal attacker activity.
- Most forensic evidence originates from operating system activity.
- Attackers frequently abuse legitimate operating system features.
- Understanding normal behavior is the key to detecting abnormal behavior.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Operating System (OS) | Software that manages hardware and provides services to applications |
| Process | A running instance of a program |
| PID | Process Identifier assigned to a running process |
| PPID | Parent Process Identifier |
| Process Tree | A hierarchy showing parent and child processes |
| Privilege Escalation | Gaining higher access rights than originally granted |

---

# Chapter Summary

In this chapter, you learned:

- What an operating system is
- The major responsibilities of an operating system
- How processes, memory, users, and files interact
- Why operating system internals are important in DFIR
- How attackers abuse legitimate operating system features
- Best practices for analyzing operating system evidence

A DFIR investigator does not need to know every detail of an operating system's implementation, but they must understand how the operating system manages processes, memory, users, and files. This knowledge forms the foundation for identifying suspicious behavior and interpreting forensic evidence accurately.

---

# Review Questions

1. What is the primary role of an operating system?
2. What is a process?
3. What is the difference between a PID and a PPID?
4. Why are process trees valuable during an investigation?
5. How do attackers commonly abuse operating system features?
6. Why is understanding user permissions important in DFIR?
7. What types of operating system events are useful during an investigation?
8. How does understanding normal system behavior help identify malicious activity?

---

# Practical Exercise

A Windows workstation is suspected of being compromised through a malicious document.

Develop an investigation plan by answering:

- Which operating system components would you examine first?
- Which process relationships would you investigate?
- Which user accounts and permissions would you review?
- Which operating system events would you correlate?
- How would you distinguish normal activity from suspicious behavior?

Your objective is to demonstrate how operating system internals support a structured digital forensic investigation.

---

# What's Next?

In the next chapter, we will compare **Windows, Linux, and macOS** from a DFIR perspective, highlighting their architectural differences, common forensic artifacts, and the unique challenges each platform presents during an investigation.