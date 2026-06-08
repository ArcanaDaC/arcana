# PB-009: Privilege Escalation

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-009: Privilege Escalation | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    This playbook defines the response workflow for suspected or confirmed privilege escalation, including unauthorised elevation from standard user to administrator, abuse of privileged roles, local privilege escalation on endpoints, directory privilege escalation, cloud IAM escalation, service account abuse, and administrative policy tampering.

- **Scope:**

    Applies to privilege escalation activity across endpoints, servers, identity providers, Active Directory, cloud platforms, SaaS applications, and administrative tooling. This playbook should be run alongside related playbooks when escalation is part of account takeover, malware, lateral movement, cloud compromise, or data exfiltration.

## 2. Incident Identification & Criteria

**Incident Type:** Privilege Escalation

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- New or unexpected privileged role assignment
- User added to local admin, Domain Admin, cloud admin, SaaS admin, or other sensitive group
- Privileged session from an unusual source, device, region, or user agent
- UAC bypass, token impersonation, credential dumping, or privilege abuse alert
- Service account, workload identity, OAuth app, or API key granted excessive permissions
- IAM policy, group policy, conditional access, MFA, logging, or security control modified without approval
- Privileged tool execution from an unexpected endpoint or account
- Exploit activity resulting in higher privileges

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Suspicious privilege-related activity requiring validation; no confirmed unauthorised access |
| Sev 2 | Confirmed unauthorised privilege escalation for a single account, host, role, or application with limited scope |
| Sev 1 | Privileged account, service account, cloud role, or directory group abused across critical systems or multiple assets |
| Sev 0 | Domain-wide, tenant-wide, cloud account-wide, security tooling, or identity infrastructure compromise |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates response, approves containment timing, manages severity, and owns escalation decisions.
- **Incident Responder / Forensic Analyst:** Validates escalation activity, reconstructs the timeline, identifies affected accounts/assets, and preserves evidence.
- **Communications Lead:** Coordinates stakeholder updates and affected-user communications.
- **Other Roles:**
    - **Identity & Access Team:** Reviews role assignments, sessions, MFA, tokens, service accounts, and directory integrity.
    - **Endpoint / Platform Team:** Supports host evidence collection, isolation, rebuild, and endpoint control validation.
    - **Cloud Security / Platform Team:** Reviews cloud IAM, control plane activity, workload identities, and cloud containment actions.
    - **Application / Service Owners:** Validate whether privileged actions were authorised and support safe rollback.
    - **Legal & Compliance:** Assesses external notification requirements if sensitive data, regulated systems, or customers are affected.

## 4. Initial Actions

- **Immediate Steps:**
    - Validate the alert source and affected identity, host, role, or service.
        - 📘 [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
        - 📘 [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
        - 📘 [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
    - Identify the privilege gained, source account, target system, timestamp, and whether activity is ongoing.
    - Notify the Incident Commander and engage identity, platform, or cloud owners as required.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If the activity is approved and expected → document rationale and close.
    > - If unauthorised, suspicious, or unresolved → continue investigation and containment.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Collect identity, session, MFA, role assignment, audit, endpoint, and cloud control plane logs for the incident window.
        - 📘 [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
        - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
        - 📘 [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - Capture memory where credential theft, token theft, LSASS access, or in-memory tooling is suspected.
        - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)

- **Analysis Steps:**
    - Assess current and historical privileged access exposure.
        - 📘 [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - Analyse authentication activity, MFA events, sessions, and privileged logons.
        - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - Review process trees, commands, LOLBins, and scripts involved in escalation attempts.
        - 📘 [RB-ANALYSIS-006: Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)
        - 📘 [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
        - 📘 [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
        - 📘 [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - Validate whether the activity was authorised by the user, system owner, or change record.
        - 📘 [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - Identify additional compromised accounts, shared indicators, inherited privileges, and adjacent administrative relationships.
        - 📘 [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
    - For cloud privilege escalation, reconstruct IAM, resource, region, and security-service activity.
        - 📘 [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
    - Where exploit activity produced elevated access, verify exploitation and affected assets.
        - 📘 [RB-ANALYSIS-041: Exploitation Verification](../runbooks/analysis/RB-ANALYSIS-041-exploitation-verification.md)
        - 📘 [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If account compromise is confirmed → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - If malware is suspected or identified → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) concurrently.
    > - If lateral movement is identified → execute [PB-010: Lateral Movement](PB-010-lateral-movement.md) concurrently.
    > - If suspicious process/script execution is the primary signal → execute [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) concurrently.
    > - If cloud compromise is suspected or identified → execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Disable or lock compromised accounts and remove unauthorised privileged assignments.
        - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - Revoke sessions, OAuth tokens, API tokens, refresh tokens, VPN sessions, and persistent sessions.
        - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - Reset MFA where factor registration, trusted devices, or MFA bypass is suspected.
        - 📘 [RB-CONTAIN-006: MFA Reset & Validation](../runbooks/contain/RB-CONTAIN-006-mfa-reset-validation.md)
    - Contain directory-level risk where privileged Active Directory or domain control is affected.
        - 📘 [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
    - Isolate hosts or cloud workloads used to obtain or exercise elevated access.
        - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
        - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)

- **Eradication Steps:**
    - Remove unauthorised accounts, groups, roles, access keys, service principals, OAuth grants, policies, scheduled tasks, services, and persistence mechanisms.
    - Restore IAM, directory, conditional access, MFA, logging, and security control configurations to approved baselines.
    - Rotate credentials, secrets, certificates, API keys, and service account credentials that could have been exposed.

- **Recovery Steps:**
    - Restore user or administrative access only after containment and access integrity are validated.
        - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
    - Rebuild or re-provision compromised systems where escalation involved host compromise or persistence.
        - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - Coordinate staged recovery for identity, cloud, or critical infrastructure impact.
        - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, identity owners, system owners, cloud/platform owners, and impacted business teams.
    - Use geo handoff for incidents spanning shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - Notify affected users when credentials, MFA, or access restoration actions are required.
        - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **External Communication:**
    - Engage Legal/Privacy if privileged access reached customer data, regulated data, production systems, or third-party environments.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Compromised account caused escalation | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Lateral movement observed | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
    | Suspicious execution, LOLBin, or script abuse observed | [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) |
    | Malware suspected or identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
    | Cloud compromise suspected or identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Sensitive data access or exfiltration identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Domain-wide, tenant-wide, or security tooling compromise | [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a Post-Incident Review (PIR)
    - Document what worked, what didn't, and what needs improvement
    - Review least privilege, just-in-time access, service account scope, and administrative segmentation.

- **Documentation Updates:**
    - Update this playbook, related runbooks, detections, access review procedures, and hardening guidance based on findings.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-019: Major Security Incident Management](PB-019-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
    - [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
    - [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
    - [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
    - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
    - [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
    - [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
    - [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
    - [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
    - [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)
    - [RB-ANALYSIS-041: Exploitation Verification](../runbooks/analysis/RB-ANALYSIS-041-exploitation-verification.md)
    - [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
    - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
    - [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - [RB-CONTAIN-006: MFA Reset & Validation](../runbooks/contain/RB-CONTAIN-006-mfa-reset-validation.md)
    - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

## 10. Appendices

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
