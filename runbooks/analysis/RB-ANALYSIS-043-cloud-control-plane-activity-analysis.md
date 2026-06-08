# RB-ANALYSIS-043: Cloud Control Plane Activity Analysis

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Cloud Control Plane Activity Analysis | [Enter date] |
| Version | v1.0 | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | Draft | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial version | [Enter date] |

## 1. Prerequisites
- The incident time window 
- A list of identities and resources known to be in scope from triage
- SIEM with cloud control plane logs indexed
- Cloud provider console (for cross-referencing resource state)

## 2. Step-by-Step Instructions

> **Common Failure Modes**
> - Investigating only the alerting identity - attackers commonly create new identities and roles to persist; the originating identity may stop being used early
> - Investigating only the alerting region - control plane activity is per-region; attackers pivot regions to evade detection
> - Trusting in-console state for "what exists" - if security logging was tampered with, the console may show only the post-attacker state, not the original

1. **Reconstruct the Identity Action Timeline**
    - Build a chronological list of every API call made by each in-scope identity (user, role, service account, workload identity)
    - For each call: timestamp, source IP, source region, user agent, target service, action, target resource, result (success / failure)
    - Look for the first action that is anomalous for the identity (action type, region, IP, user agent)

2. **Identify IAM Changes**
    - List every identity / role / policy / access key / federation trust created, modified, or deleted in the incident window
    - For each, identify who made the change, when, and from where
    - Flag any change that grants broader access than the identity had before
    - Flag any creation of new identities or access keys not tied to a known change ticket

3. **Identify Resource Changes**
    - List every resource created, modified, or deleted in the incident window
    - Flag resources created in unusual regions, unusual sizes, or with unusual configurations (e.g. open security groups, public storage buckets, large compute)
    - Flag scheduled or recurring resources (functions with triggers, scheduled tasks, cron jobs) - common persistence

4. **Identify Security Service Tampering**
    - Check for actions that stop, suspend, or reduce coverage of:
      - Audit logging (CloudTrail, Azure Activity diagnostic settings, GCP audit sinks, OCI audit)
      - Security services (GuardDuty, Defender for Cloud, Security Command Center, Cloud Guard)
      - Detection / SIEM rules (Sentinel rule changes, EventBridge / Eventarc rule changes)
      - Log retention policies (reducing retention is a tamper signal)

5. **Identify Cross-Account / Cross-Tenant Activity**
    - List all assume-role / delegated-access / B2B activity in the window
    - Flag any role assumption involving an external account or tenant not on the known partner list
    - For each external entity, identify how the trust was established and whether it pre-dates the incident

6. **Identify Persistence Mechanisms**
    - New IAM users with long-lived access keys
    - New roles with permissive trust policies (especially with external account principals)
    - Federation trust modifications
    - Scheduled compute (Lambda triggers, scheduled tasks, cron jobs, recurring pipelines)
    - Container / image registry pushes to base images

7. **Identify Initial Access Vector**
    - Correlate the first anomalous identity action with the source IP / user agent / region
    - Map back to whether the identity was a human user, a workload identity, or a federated identity
    - Determine whether the credential was leaked, brute-forced, assumed via misconfigured trust, or used after legitimate identity compromise

8. **Document and Hand Off**
    - Record findings: identity timeline, IAM changes, resource changes, tampering, persistence, initial access vector
    - Hand off to the Incident Commander for containment / eradication planning
    - Update the incident record with all queries used

## 3. Post-Action

- Ensure findings are recorded in the incident record with linked log sources and query strings
- Confirm any persistence mechanisms identified are tracked through eradication

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo


Contributed to the Arcana Incident Response Documentation Framework.
