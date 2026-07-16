# Indicators of Compromise (IOCs)

## Purpose

This document summarizes the Indicators of Compromise (IOCs) identified during the AWSRaid investigation.

These indicators were extracted from AWS CloudTrail logs using Splunk and can assist with threat hunting, retrospective log analysis, and cloud security monitoring.

---

## IAM Users

| Indicator | Value | Description |
|-----------|-------|-------------|
| Compromised User | `helpdesk.luke` | IAM account used by the attacker following successful authentication. |
| Persistence User | `marketing.mark` | IAM account created to maintain long-term access. |

---

## Network Indicators

| Indicator | Description |
|-----------|-------------|
| `2.57.168.220` | Source IP used during successful AWS Console authentication. |
| `185.192.70.78` | Source IP associated with IAM persistence and privilege escalation activities. |

---

## Cloud Resources

### Amazon S3 Buckets

| Bucket Name |
|-------------|
| `product-designs-repository31183937` |
| `backup-and-restore98825501` |

### Accessed Objects

| Object Name |
|-------------|
| `prototype.obj` |
| `Product2_CAD_Designs.dwg` |
| `logo.png` |
| `Contract_Agreement.pdf` |
| `CustomerData_Backup_2023-11-01.zip` |
| `secrets_vault_dump.bak` |

---

## Privileged IAM Group

| Group |
|-------|
| `Admins` |

---

## Related Documents

- `README.md` — Complete Investigation Report
- `Artifacts/MITRE-ATTACK-Mapping.md`
- `Evidence/Timeline-Evidence.md`