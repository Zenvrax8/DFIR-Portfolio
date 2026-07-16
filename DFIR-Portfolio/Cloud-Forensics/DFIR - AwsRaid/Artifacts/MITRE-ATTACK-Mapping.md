# MITRE ATT&CK Mapping

## Purpose

This document maps the observed attacker activities to the MITRE ATT&CK framework based on evidence collected from AWS CloudTrail logs.

The mapping provides a standardized representation of attacker behavior and supports detection engineering, threat hunting, and incident response activities.

---

| ATT&CK Tactic | Technique | ATT&CK ID | Evidence | Justification |
|--------------|-----------|-----------|----------|---------------|
| Initial Access | Valid Accounts | T1078 | Successful `ConsoleLogin` using `helpdesk.luke` | The attacker authenticated using a legitimate IAM account. |
| Discovery | Cloud Service Discovery | T1526 | `DescribeRegions`, `DescribeOrganization` | AWS resources were enumerated to understand the cloud environment. |
| Discovery | Permission Groups Discovery | T1069 | `ListUsers`, `ListGroups`, `ListPolicies` | IAM users, groups, and policies were enumerated to identify privilege opportunities. |
| Collection | Data from Cloud Storage Object | T1530 | Multiple `GetObject` events | The attacker accessed several objects stored within Amazon S3 buckets. |
| Defense Evasion | Impair Defenses | T1562 | `PutBucketPublicAccessBlock` | Bucket security settings were modified, affecting the protection of cloud storage resources. |
| Persistence | Account Manipulation | T1098 | `CreateUser`, `CreateLoginProfile` | A new IAM account (`marketing.mark`) was created to maintain long-term access. |
| Privilege Escalation | Account Manipulation | T1098 | `AddUserToGroup`, `AttachUserPolicy` | Administrative privileges were assigned to the persistence account through group membership and IAM policies. |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/Indicators-of-Compromise.md`
- `Evidence/Timeline-Evidence.md`