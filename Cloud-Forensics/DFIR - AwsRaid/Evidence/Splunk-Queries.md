# Investigation Queries

## Purpose

This document contains the Splunk Search Processing Language (SPL) queries used throughout the AWSRaid investigation.

The queries are organized according to the investigation workflow and can be used to reproduce the findings, validate evidence, and reconstruct the attack timeline from AWS CloudTrail logs.

> **Platform:** Splunk  
> **Log Source:** AWS CloudTrail

---

# Phase 1 – Environment Familiarization

## Query 1 – Identify Available Event Types

**Purpose**

Identify all CloudTrail event types present within the dataset.

```spl
* | stats count by eventName
```

**Expected Output**

- CloudTrail Event Names
- Event Count

**Investigation Result**

Used to understand the overall activity within the AWS environment and identify security-relevant events for further analysis.

---

## Query 2 – Identify IAM Users

**Purpose**

Identify all IAM users observed in the CloudTrail logs.

```spl
* | stats count by userIdentity.userName
```

**Expected Output**

- IAM Username
- Event Count

**Investigation Result**

Identified the IAM users present in the investigation dataset and assisted in determining the compromised account.

---

## Query 3 – Identify Source IP Addresses

**Purpose**

Identify all source IP addresses interacting with the AWS environment.

```spl
* | stats count by sourceIPAddress
```

**Expected Output**

- Source IP Address
- Event Count

**Investigation Result**

Helped identify external IP addresses associated with attacker activity.

---

# Phase 2 – Initial Access

## Query 4 – Console Login Events

**Purpose**

Identify successful and failed AWS Management Console authentication events.

```spl
eventName=ConsoleLogin
| table _time userIdentity.userName sourceIPAddress responseElements.ConsoleLogin additionalEventData.MFAUsed
| sort _time
```

**Expected Output**

- Timestamp
- IAM Username
- Source IP
- Login Status
- MFA Usage

**Investigation Result**

Confirmed successful authentication using the compromised IAM account `helpdesk.luke`.

---

# Phase 3 – Reconnaissance

## Query 5 – AWS Environment Reconnaissance

**Purpose**

Identify reconnaissance activities performed after successful authentication.

```spl
userIdentity.userName="helpdesk.luke"
(eventName=Describe* OR eventName=List* OR eventName=Get*)
| table _time eventName sourceIPAddress
| sort _time
```

**Expected Output**

- Timestamp
- API Name
- Source IP

**Investigation Result**

Confirmed that the attacker enumerated AWS services, IAM resources, policies, groups, users, and S3 resources prior to further malicious activity.

---

# Phase 4 – Data Collection

## Query 6 – Amazon S3 Object Access

**Purpose**

Identify S3 objects accessed by the attacker.

```spl
userIdentity.userName="helpdesk.luke"
eventName=GetObject
| table _time requestParameters.bucketName requestParameters.key sourceIPAddress
| sort _time
```

**Expected Output**

- Timestamp
- Bucket Name
- Object Name
- Source IP

**Investigation Result**

Confirmed access to multiple S3 objects including engineering files, customer backups, contracts, and business data.

---

# Phase 5 – Cloud Configuration Changes

## Query 7 – S3 Bucket Security Configuration

**Purpose**

Identify modifications to Amazon S3 bucket security settings.

```spl
eventName=PutBucketPublicAccessBlock
| table _time userIdentity.userName requestParameters.bucketName sourceIPAddress
```

**Expected Output**

- Timestamp
- IAM User
- Bucket Name
- Source IP

**Investigation Result**

Confirmed unauthorized modification of the Public Access Block configuration for an Amazon S3 bucket.

---

# Phase 6 – Persistence

## Query 8 – IAM User Creation

**Purpose**

Identify newly created IAM user accounts.

```spl
eventName=CreateUser
| table _time userIdentity.userName requestParameters.userName sourceIPAddress
```

**Expected Output**

- Timestamp
- Acting User
- Created User
- Source IP

**Investigation Result**

Confirmed that the compromised account created the persistence account `marketing.mark`.

---

## Query 9 – IAM Login Profile Creation

**Purpose**

Identify console login profile creation for newly created IAM users.

```spl
eventName=CreateLoginProfile
| table _time userIdentity.userName requestParameters.userName sourceIPAddress
```

**Expected Output**

- Timestamp
- Acting User
- Target User
- Source IP

**Investigation Result**

Confirmed that a console login profile was created for the attacker-controlled persistence account.

---

# Phase 7 – Privilege Escalation

## Query 10 – IAM Group Membership

**Purpose**

Identify users added to privileged IAM groups.

```spl
eventName=AddUserToGroup
| table _time userIdentity.userName requestParameters.userName requestParameters.groupName sourceIPAddress
```

**Expected Output**

- Timestamp
- Acting User
- Target User
- IAM Group
- Source IP

**Investigation Result**

Confirmed that the persistence account `marketing.mark` was added to the `Admins` IAM group.

---

## Query 11 – IAM Policy Assignment

**Purpose**

Identify IAM policies attached during the attack.

```spl
eventName=AttachUserPolicy
| table _time userIdentity.userName requestParameters.userName requestParameters.policyArn sourceIPAddress
```

**Expected Output**

- Timestamp
- Acting User
- Target User
- Policy ARN
- Source IP

**Investigation Result**

Confirmed that IAM policies were attached to strengthen the privileges of the persistence account.

---

# Phase 8 – Timeline Reconstruction

## Query 12 – Complete Attack Timeline

**Purpose**

Reconstruct the complete sequence of attacker activities.

```spl
userIdentity.userName="helpdesk.luke"
| table _time eventName eventSource sourceIPAddress requestParameters.bucketName requestParameters.key
| sort _time
```

**Expected Output**

- Timestamp
- Event Name
- AWS Service
- Source IP
- Bucket Name
- Object Name

**Investigation Result**

Provided a chronological reconstruction of the attack from initial authentication through reconnaissance, data collection, cloud configuration changes, persistence establishment, and privilege escalation.

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/Indicators-of-Compromise.md`
- `Artifacts/MITRE-ATTACK-Mapping.md`
- `Evidence/Timeline-Evidence.md`