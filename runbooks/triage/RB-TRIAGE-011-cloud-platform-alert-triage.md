# RB-TRIAGE-011: Cloud Platform Alert Triage

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Cloud Platform Alert Triage | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Prerequisites

- An alert from a cloud-native security service (e.g. AWS GuardDuty, Microsoft Defender for Cloud, GCP Security Command Center, Oracle Cloud Guard, or equivalent)
- Read access to the cloud account / subscription / project / tenancy generating the alert
- Read access to the relevant cloud control plane audit log (CloudTrail, Azure Activity, GCP Admin Activity, Oracle Audit)
- Access to the SIEM where cloud telemetry is forwarded
- Cloud provider console or CLI for the impacted account
- Cloud-native security service console (the one that raised the alert)

## 2. Step-by-Step Instructions

> **Common Failure Modes**
> - Closing the alert before checking whether the activity is still ongoing
> - Treating an alert on one resource in isolation without checking adjacent resources sharing the same identity, role, or VPC
> - Assuming a benign-sounding alert (e.g. `Recon:EC2/Portscan`) is low-risk when it indicates active reconnaissance from an attacker-controlled workload

1. **Capture Alert Details**
    - Record alert ID, source service, severity, finding type, and timestamp
    - Record the impacted cloud account / subscription / project / tenancy
    - Record the impacted resource (instance ID, container/pod ID, function name, storage bucket, database)
    - Record the identity associated with the activity (user, role, service account, workload identity)
    - Record source IPs, regions, user agents, and target services involved

2. **Confirm the Alert Is Real**
    - Check whether the source IP / user agent / region matches known good infrastructure (CI/CD, jump hosts, automation)
    - Check whether the action is documented or expected (e.g. recent deployment, change ticket, scheduled job)
    - Check the cloud control plane log for the same actor performing similar activity in the period before the alert
    - If the activity is expected → close as benign, document the rationale, exit the runbook

3. **Determine Whether Activity Is Still Active**
    - Query the cloud control plane log for the alerting identity in the last 15 minutes
    - Query workload telemetry (EDR, OS logs forwarded to SIEM) for ongoing process / network activity

4. **Identify Scope of the Activity**
    - List every resource the alerting identity has touched in the incident window (control plane log)
    - List every region the activity has been observed in
    - List every other identity that may have been used from the same source IP / session

5. **Classify the Activity**
    - Map the alert to one of:
      - Workload behaviour anomaly (cryptomining, reverse shell, unexpected outbound)
      - Control plane abuse (IAM change, resource creation, security service tampering)
      - Credential abuse (use of a credential from a new region / source / user agent)
      - Reconnaissance (port scan, IMDS probing, listing buckets / roles)
      - Data access anomaly (unusual bucket / database access pattern)

## 3. Post-Action

- Ensure all alert details, queries used, and findings are recorded in the incident ticket

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
