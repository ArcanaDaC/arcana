# PB-007: Cloud Compromise

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-007: Cloud Compromise | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |


## 1. Purpose & Scope

- **Purpose:**

  To describe the incident response steps for a compromise of cloud infrastructure - covering analysis & triage, containment, eradication, recovery, and post-incident activities. The objective is to evict the attacker from the cloud environment, determine what cloud resources, data, and identities they reached, restore secure operation, and harden the cloud estate against repeat compromise.

- **Scope:**

  Applies to compromise of cloud infrastructure across any cloud provider (AWS, Azure, GCP, Oracle, or other), including:
  - Cloud workload compromise (VMs, containers, Kubernetes pods, serverless functions)
  - Cloud control plane abuse (unauthorised API activity, IAM/role manipulation, security service tampering)
  - Cloud storage / database compromise (S3, Azure Blob, GCS, RDS, Cosmos DB, BigQuery)
  - Cloud-native lateral movement (IMDS abuse, role chaining, cross-account/cross-tenant access)
  - Infrastructure-as-code (IaC) / CI/CD pipeline compromise affecting cloud deployment
  - Exposed cloud credentials, API keys, or instance metadata

  Out of scope (handled by dedicated playbooks):
  - Compromise of cloud identities themselves (IdP, federated identity) → [PB-019: Cloud Identity Compromise](PB-019-cloud-identity-compromise.md)
  - Compromise of a user/service/bot account → [PB-004: Account Takeover](PB-004-account-takeover.md)


## 2. Incident Identification & Criteria

**Incident Type:** Cloud Compromise

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- Cloud-native security alert (GuardDuty, Defender for Cloud, GCP Security Command Center, Oracle Cloud Guard, or equivalent)
- Unauthorised cloud API activity detected (unfamiliar regions, unusual user agents, unexpected services)
- Unauthorised IAM activity (new role / policy / user / access key created or modified)
- Cloud workload behaving anomalously (unexpected outbound traffic, cryptomining, foreign region activity)
- Cloud security service disabled or tampered with (logging stopped, detections silenced, retention reduced)
- Exposed cloud credential or access key identified (public repo, paste site, threat intel)
- Public exposure of a cloud resource detected (open storage bucket, exposed database, exposed management interface)
- Anomalous activity from a cloud workload identity or instance role
- Third-party notification of compromised cloud infrastructure

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Confirmed compromise of a single non-production cloud workload, no data or control plane impact |
| Sev 2 | Confirmed compromise of a production cloud workload, or unauthorised cloud control plane activity with limited scope |
| Sev 1 | Compromise of a privileged cloud role, multiple cloud workloads, or cloud storage containing sensitive data |
| Sev 0 | Cloud tenant-wide / account-wide compromise, compromise of cloud admin identities, or tampering of cloud logging / security infrastructure |


## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates and leads the response; drives decisions and timelines; ensures containment, communications, and remediation actions are executed.
- **Communications Lead:** Manages internal and external communications, executive updates, customer/regulator notifications, and stakeholder messaging.
- **Incident Responder / Forensic Analyst:** Performs the forensic investigation - analyses cloud control plane activity, reconstructs attacker actions in the cloud, determines scope of compromise, preserves evidence, and identifies root cause.
- **Other Roles:**
  - **Cloud Security / Platform Team:** Executes cloud-side containment, snapshots, IAM rollback, infrastructure-as-code changes, and resource quarantine.
  - **Identity & Access (IAM) Team:** Locks down compromised identities and roles, revokes sessions and access keys, and rotates credentials used by cloud workloads.
  - **Network Team:** Implements cloud egress filtering, blocks outbound destinations, and adjusts security groups / NSGs / firewall rules.
  - **Application / Workload Owners:** Authorise workload isolation or replacement; validate restored services.
  - **DevOps / SRE / Platform Engineering:** Rebuilds workloads from known-good infrastructure-as-code; rotates pipeline credentials.
  - **Legal & Compliance:** Assesses regulatory and breach notification obligations; owns external notification decisions.
  - **Cloud Provider Support / TAM:** Engaged for provider-side investigation, log retrieval, or account-level intervention.


## 4. Initial Actions

- **Immediate Steps:**
  - Triage the originating alert to validate it represents real compromise
    - 📘 [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md) - for cloud-native security alerts
    - 📘 [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md) - if alert came from EDR on a cloud workload
    - 📘 [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md) - if alert relates to a workload identity / role
  - Identify the cloud account / subscription / project / tenancy impacted
  - Identify the specific cloud resources involved (workload IDs, role / policy ARNs, storage buckets, databases)
  - Determine whether the activity is currently in progress or historical
  - Notify Incident Commander and Cloud Security / Platform Team

  > **Decision Point:**
  > - Active attacker actions in progress → Proceed immediately to Containment
  > - Historical activity only → Continue to Investigation & Analysis

  > **Warning:** Do NOT terminate or delete cloud workloads before snapshots are taken - termination destroys volatile evidence (memory, ephemeral disks, network state).


## 5. Investigation & Analysis

- **Evidence Collection:**
  - Collect cloud control plane logs for the incident window
    - 📘 [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
  - Snapshot impacted cloud workloads (instance disks, volumes, container filesystems) before any termination or rebuild
    - 📘 [RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition](../runbooks/evidence/RB-EVIDENCE-005-cloud-workload-snapshot-acquisition.md)
  - For impacted workloads, collect host-side telemetry covering the incident window
    - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
  - For impacted cloud / workload identities, collect identity and authentication telemetry
    - 📘 [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)

- **Analysis Steps:**
  - Reconstruct attacker activity in the cloud control plane (API calls, IAM changes, resource creation, security service tampering) and identify the initial access vector
    - 📘 [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
  - Analyse authentication activity for the impacted identities and workload roles
    - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
  - Review privileged access usage and any privilege escalation paths exercised
    - 📘 [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
  - Analyse outbound traffic from impacted workloads (C2, data exfiltration, cryptomining)
    - 📘 [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
  - Review cloud storage and SaaS access for data exposure
    - 📘 [RB-ANALYSIS-020: Cloud Storage / SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
  - Identify any additional cloud / workload identities compromised
    - 📘 [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

  > **Decision Point:** Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
  > - Compromised user / service / bot account → [PB-004: Account Takeover](PB-004-account-takeover.md)
  > - Compromised cloud / workload identity → [PB-019: Cloud Identity Compromise](PB-019-cloud-identity-compromise.md)
  > - Zero-day exploitation → [PB-018: Zero-Day Response](PB-018-zero-day-response.md)
  > - Malware deployed on a cloud workload → [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
  > - Ransomware activity observed → [PB-002: Ransomware](PB-002-ransomware.md)
  > - Data exfiltration confirmed → [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)


## 6. Containment, Eradication & Recovery

- **Containment Actions:**
  - Isolate impacted cloud workloads (apply quarantine security group / NSG, suspend instance, detach from load balancers)
    - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
  - Revoke compromised cloud credentials, API keys, and instance role sessions
    - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - Lock down compromised cloud identities and remove attacker-created identities, roles, and access keys
    - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - Block outbound destinations used by the attacker (egress rules, firewall, WAF)
    - 📘 [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
  - Re-enable any cloud logging / security services the attacker disabled or tampered with

- **Eradication Steps:**
  - Roll back attacker-created IAM resources (roles, policies, users, access keys, trust relationships)
  - Roll back attacker-created infrastructure (instances, security groups, networking, scheduled functions)
  - Remove attacker persistence in compute (cron, systemd units, container images, Lambda triggers, scheduled tasks)
  - Rotate all credentials and secrets accessible from impacted workloads (instance role credentials, environment variables, secrets manager entries, hardcoded credentials)
  - Restrict or rotate any cloud admin credentials used during the incident window
  - Patch the vulnerability or misconfiguration that enabled initial access

- **Recovery Steps:**
  - Rebuild impacted workloads from known-good infrastructure-as-code or images, not in-place clean-up
    - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
  - Coordinate phased restoration of cloud services and validate before reconnection
    - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
  - Validate cloud logging, alerting, and security services are fully restored and reporting
  - Monitor for reuse of attacker indicators (IPs, ASNs, user agents, tool signatures) across the cloud estate

  > **Warning:** Do NOT restore services to production until:
  > - All attacker-created IAM resources have been removed
  > - All credentials exposed to the attacker have been rotated
  > - Cloud logging and security services are confirmed restored
  > - The initial access vector has been remediated
  > - No additional compromised cloud identities or workloads have been identified


## 7. Communication & Escalation

- **Internal Communication:**
  - Notify Cloud Security / Platform Team immediately on confirmation
  - Notify application / workload owners before isolation actions that affect their services
    - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)
  - Notify executive leadership for Sev 1 and Sev 0 incidents
  - Page on-call per organisational SOP
    - 📘 [SOP-001: Paging Engineering On-Call](../sops/SOP-001-paging-engineering-oncall.md)

- **External Communication:**
  - Engage Legal and Compliance if regulated data may be exposed
  - Engage cloud provider support / TAM for provider-side investigation, log access, or account-level intervention
  - Notify customers, regulators, or partners as directed by Legal
    - 📘 [SOP-003: Escalation to Legal & Executive Comms](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Compromised cloud / workload identity | [PB-019: Cloud Identity Compromise](PB-019-cloud-identity-compromise.md) |
  | Compromised user / service / bot account identified as initial access vector | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Zero-day exploitation identified as initial access vector | [PB-018: Zero-Day Response](PB-018-zero-day-response.md) |
  | Malware deployed on a cloud workload | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
  | Ransomware activity observed | [PB-002: Ransomware](PB-002-ransomware.md) |
  | Data exfiltration confirmed | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
  | Cloud tenant-wide compromise, cloud admin compromise, or logging infrastructure compromise | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) / Executive escalation |


## 8. Post-Incident Activities

- **Lessons Learned:**
  - Conduct a Post-Incident Review (PIR)
  - Document what worked, what didn't, and what needs improvement
  - Capture cloud-specific gaps (detection coverage, IAM hygiene, logging retention, IaC drift)

- **Hardening & Documentation Updates:**
  - Tighten IAM policies, remove unused roles and access keys, enforce least privilege
  - Enforce MFA for all human cloud admins and break-glass procedures for non-human roles
  - Enable cloud-native security baselines (GuardDuty, Defender for Cloud, GCP SCC, Oracle Cloud Guard) across all accounts / subscriptions / projects / tenancies
  - Enforce IMDSv2 (or equivalent) where applicable; restrict workload metadata access
  - Ensure cloud logging is centralised, retained, and tamper-resistant
  - Update IaC templates and pipelines to prevent recurrence
  - Update detection rules, playbooks, runbooks, and KB articles as needed


## 9. References & Linked Resources

- **Playbooks:**
  - [PB-002: Ransomware](PB-002-ransomware.md)
  - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
  - [PB-004: Account Takeover](PB-004-account-takeover.md)
  - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
  - [PB-018: Zero-Day Response](PB-018-zero-day-response.md)
  - [PB-019: Cloud Identity Compromise](PB-019-cloud-identity-compromise.md)
  - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
  - [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
  - [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
  - [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
  - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
  - [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
  - [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
  - [RB-EVIDENCE-005: Cloud Workload Snapshot Acquisition](../runbooks/evidence/RB-EVIDENCE-005-cloud-workload-snapshot-acquisition.md)
  - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
  - [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
  - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
  - [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
  - [RB-ANALYSIS-020: Cloud Storage / SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
  - [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
  - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
  - [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
  - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
  - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)

- **SOPs:**
  - [SOP-001: Paging Engineering On-Call](../sops/SOP-001-paging-engineering-oncall.md)
  - [SOP-003: Escalation to Legal & Executive Comms](../sops/SOP-003-escalation-legal-executive-comms.md)
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)


## 10. Appendices

- **Contact List:**
  - Cloud Security / Platform Team on-call
  - Cloud provider account TAM / support
  - Identity & Access (IAM) Team
  - Legal & Compliance
  - Executive escalation chain

- **Templates:**
  - Incident log template
  - Cloud evidence preservation checklist (control plane logs, workload snapshots, identity logs)

- **Process Flowchart:**
  - Cloud compromise response workflow

---

## Contributor

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
