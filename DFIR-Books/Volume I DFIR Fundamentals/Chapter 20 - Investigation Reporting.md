# Chapter 20 – Investigation Reporting

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - Why investigation reporting is essential
> - The characteristics of a high-quality forensic report
> - The standard structure of a DFIR investigation report
> - How to document evidence objectively
> - Common reporting mistakes
> - Best practices for writing professional investigation reports

---

# 1. Introduction

Imagine two detectives investigate the same crime.

The first detective solves the case but writes only one sentence:

> "The suspect committed the crime."

The second detective writes:

- What happened
- When it happened
- How it happened
- Which evidence supports each conclusion
- What tools were used
- What limitations existed

Which report would a judge trust?

The second one.

In Digital Forensics and Incident Response, **an investigation is only as strong as the report that explains it**.

A technically correct investigation that is poorly documented may fail to convince management, legal teams, regulators, or a court.

---

# 2. What is an Investigation Report?

An **investigation report** is a structured document that records:

- The purpose of the investigation
- The evidence collected
- The investigative process
- The findings
- The conclusions
- The recommendations

Its purpose is to communicate facts clearly and accurately.

A report should allow another qualified investigator to understand what was done and why.

---

# 3. Why Reporting Matters

Investigation reports are used by many different audiences.

Examples include:

- Incident response teams
- Security operations teams
- Management
- Legal counsel
- Human resources
- Compliance teams
- Law enforcement
- Courts

Each audience depends on the report to make informed decisions.

---

# 4. Characteristics of a Good Report

A professional DFIR report should be:

### Accurate

Only include findings supported by evidence.

---

### Objective

Present facts without personal opinions or assumptions.

---

### Clear

Avoid unnecessary jargon where possible.

Explain technical concepts when writing for non-technical readers.

---

### Complete

Document all significant evidence, methods, findings, and limitations.

---

### Reproducible

Another qualified investigator should be able to repeat your process using your documentation.

---

# 5. Standard Report Structure

Although formats vary, most professional reports contain similar sections.

### Executive Summary

A high-level overview of the incident.

---

### Scope

What systems, users, or evidence were included?

---

### Investigation Objectives

What questions was the investigation intended to answer?

---

### Methodology

Describe:

- Acquisition methods
- Analysis techniques
- Tools used
- Validation methods

---

### Evidence Collected

Document:

- Evidence sources
- Acquisition dates
- Hash values
- Storage locations
- Chain of Custody information

---

### Findings

Present factual observations supported by evidence.

---

### Timeline

Chronologically reconstruct the incident.

---

### Indicators

Include:

- IOCs
- IOAs
- TTPs
- MITRE ATT&CK mapping (if applicable)

---

### Conclusions

Explain what the evidence demonstrates.

Avoid speculation.

---

### Recommendations

Suggest actions that may reduce the likelihood or impact of similar incidents in the future.

---

# 6. Facts vs Opinions

One of the most important skills in reporting is distinguishing between observations and conclusions.

Example:

❌ Incorrect:

> "The employee intentionally stole confidential files."

✔ Better:

> "The investigation found that the employee copied confidential files to a removable USB device at 22:14. The investigation did not assess the employee's intent."

Investigators report evidence—not motives unless supported by evidence.

---

# 7. Supporting Every Conclusion

Every significant conclusion should be supported by evidence.

Example:

| Finding | Supporting Evidence |
|----------|---------------------|
| Malware executed | EDR alert, Event Logs, Prefetch |
| Data exfiltration occurred | Firewall logs, Proxy logs, Cloud audit logs |
| Persistence established | Scheduled Task, Registry Run Key |

A report is stronger when every conclusion can be traced back to supporting evidence.

---

# 8. Documentation During the Investigation

Reporting does not begin after analysis.

Professional investigators document throughout the investigation.

Examples include:

- Commands executed
- Screenshots
- Tool versions
- Hash values
- Timestamps
- Notes
- Observations
- Unexpected findings

Good notes become the foundation of a good report.

---

# 9. Real-World Example

A company suspects ransomware.

The DFIR team:

- Acquires memory and disk images.
- Calculates SHA-256 hashes.
- Documents every acquisition step.
- Captures screenshots of suspicious processes.
- Records command output.
- Builds a detailed timeline.
- Maps attacker activity to MITRE ATT&CK.

When management requests a briefing, the team can explain exactly:

- How the attack began.
- Which systems were affected.
- What evidence supports each conclusion.
- What remediation actions are recommended.

Because documentation was maintained throughout the investigation, reporting is efficient and defensible.

---

# 10. Common Mistakes

New investigators often:

- Write conclusions without evidence.
- Mix facts with opinions.
- Omit important timestamps.
- Forget tool versions.
- Ignore investigation limitations.
- Use inconsistent terminology.
- Wait until the end to begin documenting.

These mistakes reduce the credibility of the report.

---

# 11. Best Practices

Professional investigators should:

- Begin documenting immediately.
- Record every significant action.
- Preserve screenshots and command output.
- Reference supporting evidence for each conclusion.
- Use consistent terminology.
- Write clearly for the intended audience.
- Review the report before submission.

A well-written report is clear, factual, organized, and supported by evidence.

---

# Remember This

- Reporting begins when the investigation begins.
- Every conclusion must be supported by evidence.
- Separate facts from opinions.
- Write for your intended audience.
- Good notes produce good reports.
- A report should allow another investigator to reproduce your work.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Executive Summary | A concise overview of the investigation and its findings |
| Scope | The boundaries of the investigation |
| Methodology | The processes, tools, and techniques used during the investigation |
| Finding | A factual observation supported by evidence |
| Conclusion | An evidence-based interpretation of the findings |
| Recommendation | A suggested action to improve security or reduce future risk |

---

# Chapter Summary

In this chapter, you learned:

- Why investigation reporting is essential
- The characteristics of a professional forensic report
- The standard structure of a DFIR report
- How to distinguish facts from opinions
- Why documentation should occur throughout the investigation
- Best practices for producing accurate and defensible reports

An investigation report is more than a summary of technical findings—it is the official record of the investigation. Clear, objective, and evidence-based reporting enables technical teams, management, legal professionals, and other stakeholders to understand the incident and make informed decisions.

---

# Review Questions

1. Why is investigation reporting important?
2. What are the characteristics of a high-quality forensic report?
3. Why should facts and opinions be separated?
4. What sections are commonly included in a DFIR report?
5. Why should every conclusion be supported by evidence?
6. Why is documentation during the investigation important?
7. Who are the typical audiences for a forensic report?
8. What are some common reporting mistakes?

---

# Practical Exercise

You have completed a forensic investigation into a phishing attack that resulted in unauthorized access to confidential company data.

Create the outline of a professional investigation report by identifying:

- The sections you would include.
- The evidence supporting each major finding.
- The timeline of the incident.
- The IOCs, IOAs, and TTPs you would document.
- The recommendations you would provide to management.

Your objective is to produce a report structure that is clear, objective, evidence-based, and suitable for both technical and non-technical audiences.

---

# What's Next?

In the next chapter, we will explore **Legal and Ethical Considerations in DFIR**, where you will learn how laws, organizational policies, privacy requirements, and ethical responsibilities influence every stage of a digital forensic investigation.