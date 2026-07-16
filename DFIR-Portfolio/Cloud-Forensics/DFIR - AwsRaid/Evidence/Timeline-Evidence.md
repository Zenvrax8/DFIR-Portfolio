# Timeline Evidence

## Purpose

This document contains the evidence used to reconstruct the attack timeline during the AWSRaid investigation.

The timeline was built by correlating AWS CloudTrail events using Splunk and arranging the observed attacker activities in chronological order.

> **Primary Data Source:** AWS CloudTrail  
> **Analysis Platform:** Splunk

---

# Timeline Reconstruction Methodology

The attack timeline was reconstructed using the following investigative process:

1. Identify successful AWS Management Console authentication events.
2. Determine the compromised IAM account.
3. Identify reconnaissance activity performed immediately after authentication.
4. Track access to Amazon S3 buckets and objects.
5. Identify unauthorized cloud configuration changes.
6. Investigate IAM administrative actions.
7. Identify persistence mechanisms.
8. Identify privilege escalation activities.
9. Correlate all events chronologically to reconstruct the complete attack sequence.

---

# Timeline Evidence Summary

| Time (UTC) | Event | Evidence | Investigation Significance |
|------------|-------|----------|----------------------------|
| 2023-11-02 09:37:23 | ConsoleLogin | Successful login using `helpdesk.luke` | Confirmed initial access to the AWS environment. |
| 2023-11-02 09:37:24 | Discovery | `Describe*`, `List*`, `Get*` API calls | Confirmed reconnaissance activities. |
| 2023-11-02 09:55:53 | GetObject | First S3 object access (`prototype.obj`) | Beginning of data collection. |
| 2023-11-02 09:58:01 | PutBucketPublicAccessBlock | Bucket configuration modified | Unauthorized cloud security configuration change. |
| 2023-11-02 09:59:33 | CreateUser | Created `marketing.mark` | Persistence established. |
| 2023-11-02 09:59:XX | CreateLoginProfile | Login profile created | Enabled interactive console access. |
| 2023-11-02 09:59:XX | AddUserToGroup | Added to `Admins` | Privilege escalation. |
| 2023-11-02 10:00:XX | AttachUserPolicy | IAM policy attached | Reinforced privileged persistence. |

---

# Evidence Sources

The timeline was reconstructed using the following CloudTrail events:

- `ConsoleLogin`
- `DescribeRegions`
- `DescribeOrganization`
- `ListUsers`
- `ListGroups`
- `ListPolicies`
- `ListBuckets`
- `GetObject`
- `PutBucketPublicAccessBlock`
- `CreateUser`
- `CreateLoginProfile`
- `AddUserToGroup`
- `AttachUserPolicy`

---

# Related Documents

- `README.md` — Complete Investigation Report
- `Evidence/Splunk-Queries.md`
- `Artifacts/Indicators-of-Compromise.md`
- `Artifacts/MITRE-ATTACK-Mapping.md`