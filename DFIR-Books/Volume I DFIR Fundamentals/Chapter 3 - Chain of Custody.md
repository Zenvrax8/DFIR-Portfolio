# Chapter 3 – Chain of Custody

> **Learning Objectives**
>
> By the end of this chapter, you will understand:
>
> - What Chain of Custody (CoC) is
> - Why it is one of the most important principles in digital forensics
> - How evidence is tracked from collection to presentation
> - What information should be recorded in a Chain of Custody
> - How improper handling can compromise an investigation
> - Best practices for maintaining the integrity of evidence

---

# 1. Introduction

Imagine a police officer finds a knife at a crime scene.

The knife is believed to be the murder weapon.

Now imagine the officer places it on a table without recording who found it, when it was collected, or where it was stored.

Later, several people handle the knife.

No one knows:

- Who touched it
- Whether it was replaced
- Whether it was cleaned
- Whether fingerprints were contaminated

Could that knife still be trusted as evidence?

Probably not.

The same principle applies to digital evidence.

If investigators cannot prove that digital evidence remained unchanged and under proper control, its reliability may be questioned.

This documented history is known as the **Chain of Custody**.

---

# 2. What is Chain of Custody?

**Chain of Custody (CoC)** is the documented and chronological record that shows:

- Who collected the evidence
- When it was collected
- Where it was collected
- How it was collected
- Who handled it afterward
- Where it was stored
- Every transfer of possession
- When it was presented during the investigation or legal proceedings

Simply put,

> **Chain of Custody is the complete history of evidence from collection to final disposition.**

---

# 3. Why is Chain of Custody Important?

Digital evidence is extremely easy to modify.

Opening a file, changing a timestamp, or accidentally deleting data can alter evidence.

Without proper documentation, an investigator cannot prove that the evidence remained unchanged.

A strong Chain of Custody ensures:

- Evidence remains trustworthy.
- Every action is documented.
- Investigators can explain who handled the evidence.
- The investigation can withstand legal and organizational scrutiny.

Remember:

> **If the integrity of the evidence is questioned, the conclusions drawn from it may also be questioned.**

---

# 4. The Lifecycle of Evidence

Every piece of evidence follows a predictable journey.

```text
Discovery
      ↓
Collection
      ↓
Documentation
      ↓
Packaging
      ↓
Transportation
      ↓
Storage
      ↓
Analysis
      ↓
Reporting
      ↓
Archiving or Disposal
```

Each step must be documented.

If even one transfer is missing, the Chain of Custody becomes incomplete.

---

# 5. Information Recorded in a Chain of Custody

A Chain of Custody record should include:

| Field | Description |
|--------|-------------|
| Evidence ID | Unique identifier assigned to the evidence |
| Description | What was collected |
| Date and Time | When it was collected |
| Location | Where it was collected |
| Collector | Person who collected the evidence |
| Collection Method | How the evidence was acquired |
| Hash Value | Integrity verification (e.g., SHA-256) |
| Storage Location | Where the evidence is stored |
| Transfers | Every person who receives or returns the evidence |
| Purpose | Why the evidence was transferred |

Good documentation leaves no unanswered questions.

---

# 6. Example of a Chain of Custody Record

| Time | Action | Person |
|------|--------|--------|
| 09:10 | Laptop seized from employee desk | Investigator A |
| 09:20 | Evidence bag sealed and labeled | Investigator A |
| 09:45 | SHA-256 hash calculated | Investigator A |
| 10:15 | Evidence transferred to forensic laboratory | Investigator B |
| 11:00 | Forensic image created | Investigator B |
| 11:45 | Original device placed in secure evidence locker | Investigator B |

This creates a complete timeline showing how the evidence was handled.

---

# 7. Physical vs Digital Evidence

Although the principles are the same, the handling differs.

| Physical Evidence | Digital Evidence |
|-------------------|------------------|
| Knife | Hard Drive |
| Fingerprints | Hash Values |
| Evidence Bag | Forensic Image |
| Evidence Locker | Secure Evidence Repository |
| Police Log | Chain of Custody Log |

In both cases, the objective is the same:

**Protect the evidence from unauthorized modification.**

---

# 8. Chain of Custody in Digital Forensics

Suppose investigators seize a suspect's laptop.

The recommended process is:

1. Photograph the device.
2. Record its condition.
3. Assign an evidence ID.
4. Label the device.
5. Calculate a cryptographic hash (when appropriate).
6. Create a forensic image.
7. Verify the forensic image using hash values.
8. Store the original device securely.
9. Perform analysis on the forensic copy—not the original evidence.

This approach preserves the original evidence while allowing investigators to conduct their analysis safely.

---

# 9. Common Mistakes

New investigators often make mistakes that weaken the Chain of Custody.

Examples include:

- Failing to document evidence collection.
- Using the original evidence for analysis.
- Forgetting to calculate hash values.
- Allowing unauthorized access.
- Poor labeling.
- Storing evidence in unsecured locations.
- Missing transfer records.
- Incomplete documentation.

Even small mistakes can reduce confidence in the investigation.

---

# 10. Best Practices

To maintain a strong Chain of Custody:

- Assign a unique evidence identifier.
- Record every action immediately.
- Use tamper-evident packaging where applicable.
- Restrict access to authorized personnel.
- Store evidence securely.
- Calculate and verify cryptographic hashes.
- Analyze forensic copies instead of originals.
- Maintain accurate timestamps.
- Keep documentation clear and complete.

Consistency is more important than complexity.

---

# 11. Real-World Example

A ransomware attack affects a company's file server.

Investigators seize the affected server's hard drive.

Instead of examining the original drive directly, they:

- Create a forensic image.
- Calculate the SHA-256 hash of the original drive.
- Calculate the SHA-256 hash of the forensic image.
- Confirm that both hash values match.
- Store the original drive in a secure evidence locker.
- Conduct all analysis on the forensic image.

Months later, management asks whether the evidence was modified.

The investigators demonstrate:

- The Chain of Custody documentation.
- Matching hash values.
- Evidence transfer records.
- Secure storage logs.

Because every step was documented, the organization can trust the investigation.

---

# Key Terms

| Term | Meaning |
|------|---------|
| Chain of Custody (CoC) | A documented record of who handled evidence and when |
| Evidence ID | A unique identifier assigned to evidence |
| Forensic Image | An exact bit-for-bit copy of digital media |
| Hash Value | A cryptographic fingerprint used to verify integrity |
| Integrity | Assurance that evidence has not changed |
| Evidence Locker | A secure location used to store original evidence |

---

# Chapter Summary

In this chapter, you learned:

- What Chain of Custody is
- Why documentation is essential
- How evidence moves through its lifecycle
- What information should be recorded
- Common mistakes that can compromise investigations
- Best practices for preserving the integrity of digital evidence

Chain of Custody is not simply paperwork—it is the foundation of trust in every digital forensic investigation. Without it, even accurate technical findings can be challenged because the evidence itself may no longer be considered reliable.

---

# Review Questions

1. What is a Chain of Custody?
2. Why is it important in digital forensics?
3. What information should be recorded in a Chain of Custody log?
4. Why should investigators analyze forensic images instead of original evidence?
5. What role do cryptographic hash values play?
6. List five common Chain of Custody mistakes.
7. What could happen if evidence transfers are not documented?
8. How does a Chain of Custody help establish trust in an investigation?

---

# Practical Exercise

Imagine you are assigned to collect a company laptop after a suspected insider data theft.

Without performing any technical analysis, create a simple Chain of Custody record that includes:

- Evidence ID
- Device description
- Date and time of collection
- Collection location
- Name of the collector
- Storage location
- A log of any transfers of the evidence

This exercise is designed to help you think about documentation before analysis.

---

# What's Next?

In the next chapter, we will explore **Order of Volatility (OoV)**—a core DFIR principle that helps investigators decide **what evidence to collect first** before it disappears.