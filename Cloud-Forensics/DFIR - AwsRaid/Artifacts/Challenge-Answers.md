# Challenge Answers

## Purpose

This document contains the validated answers to the AWSRaid CyberDefenders challenge questions.

The answers were obtained through analysis of AWS CloudTrail logs using Splunk and serve as a quick reference for validating the investigation findings documented in the main report.

> **Note:** Detailed analysis, supporting evidence, Splunk queries, and screenshots are documented separately within this repository.

---

| ID | Question | Answer |
|----|----------|--------|
| Q1 | Knowing which user account was compromised is essential for understanding the attacker's initial entry point into the environment. What is the username of the compromised user? | `helpdesk.luke` |
| Q2 | We must investigate the events following the initial compromise to understand the attacker's motives. What is the timestamp for the first access to an S3 object by the attacker? | `2023-11-02 09:55:53 UTC` |
| Q3 | Among the S3 buckets accessed by the attacker, one contains a DWG file. What is the name of this bucket? | `product-designs-repository31183937` |
| Q4 | We've identified changes to a bucket's configuration that allowed public access, a significant security concern. What is the name of this particular S3 bucket? | `backup-and-restore98825501` |
| Q5 | Creating a new user account is a common tactic attackers use to establish persistence in a compromised environment. What is the username of the account created by the attacker? | `marketing.mark` |
| Q6 | Following account creation, the attacker added the account to a specific group. What is the name of the group to which the account was added? | `Admins` |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Evidence/Splunk-Queries.md`
- `Evidence/Timeline-Evidence.md`