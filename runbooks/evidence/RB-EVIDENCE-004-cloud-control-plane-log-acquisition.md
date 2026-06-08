# RB-EVIDENCE-004: Cloud Control Plane Log Acquisition

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Cloud Control Plane Log Acquisition | [Enter date] |
| Version | v1.0 | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | Draft | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |

## 1. Prerequisites

- Identifier of the impacted cloud account / subscription / project / tenancy
- The incident time window (start and end timestamps in UTC)
- Read access to the cloud control plane audit log (CloudTrail / Azure Activity / GCP Admin Activity / Oracle Audit)
- Read access to the SIEM where cloud telemetry is forwarded
- A dedicated forensic destination (account / project / region) for any exported logs
- Cloud provider console or CLI (AWS CLI, Azure CLI, gcloud, OCI CLI)
- SIEM query interface
- Hashing tool (e.g. `sha256sum`) for any exported log archives

## 2. Step-by-Step Instructions

> **Common Failure Modes**
> - Relying only on the cloud-native console UI (often shows recent activity only - true forensic source is the raw audit log or SIEM index)
> - Missing other-region activity - most providers log control plane activity per region; an attacker can pivot across regions and the home-region log won't show it
> - Missing org-level / management-account activity (AWS Organizations, Azure Management Groups, GCP Organization, OCI tenancy events) - these are separate logs from per-account activity
> - Forgetting data-plane events (e.g. S3 object access, KMS Decrypt calls) - these are off by default in some providers and must be specifically enabled / queried

1. **Validate Scope**
    - Confirm the impacted account / subscription / project / tenancy IDs
    - Confirm the incident time window (extend backward by at least 7 days from earliest indicator to capture pre-incident reconnaissance)
    - Identify all regions / locations in scope (attacker may have pivoted across regions)

2. **Collect Relevant Control Plane Activity**

   For each category relevant to the incident, prefer querying the SIEM where the data is already indexed; fall back to the provider-native log when needed.

   | Category | AWS | Azure | GCP | Oracle Cloud (OCI) |
   |---|---|---|---|---|
   | Management API calls | CloudTrail Management Events | Activity Log | Admin Activity audit log | Audit log (`audit.log`) |
   | Data plane API calls | CloudTrail Data Events (S3, KMS, Lambda) | Diagnostic Settings per-service | Data Access audit log | Audit log (data access events) |
   | IAM changes | CloudTrail (`iam:*`, `sts:AssumeRole`) | Activity Log + Entra ID audit (`Microsoft.Authorization`) | Admin Activity (`SetIamPolicy`) | Audit log (`identity:*`) |
   | Resource creation / modification | CloudTrail (`Run*`, `Create*`, `Modify*`, `Delete*`) | Activity Log | Admin Activity | Audit log |
   | Security service tampering | CloudTrail (`guardduty:*`, `cloudtrail:Stop*`, `config:*`) | Activity Log (Defender for Cloud, Sentinel changes) | Admin Activity (SCC mute/disable) | Audit log (Cloud Guard disable) |
   | Org / tenancy-level events | CloudTrail in management account | Management Group / Tenant Root activity | Organization audit log | Tenancy-level audit |
   | Cross-account / cross-tenant access | CloudTrail (`sts:AssumeRole`, external IDs) | Activity Log (Lighthouse, B2B) | Admin Activity (delegated access) | Audit log (cross-tenancy) |

3. **Run Targeted Queries**
    - Query by identity (user / role / service account / workload identity ARN)
    - Query by source IP / user agent / region
    - Query by event name patterns relevant to the incident (e.g. `iam:Create*`, `*:Delete*`, `*:StopLogging`)
    - For each query, record the query string, time range, and result count in the incident record

4. **Preserve Org-Wide and Management-Account Logs**
    - Retrieve the equivalent logs from the org / management / tenancy root (separate scope from individual accounts)
    - Confirm any centralised audit log archive (e.g. organisation-wide CloudTrail S3 bucket, central Log Analytics workspace) is intact and not tampered with

5. **Export and Hash Where Required for Chain of Custody**
    - If logs may be needed outside the SIEM (legal, regulator, external forensics), export the relevant slice as a single archive
    - SHA-256 the archive and record the hash
    - Transfer to the dedicated forensic destination

## 3. Post-Action

- Record query strings, time ranges, sources, and any export hashes in the incident ticket
- Confirm logging services and centralised archives are intact and were not tampered with during the incident window
---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
