# PB-010: Lateral Movement

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-010: Lateral Movement | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    This playbook defines the response workflow for suspected or confirmed lateral movement. It is used to identify how an attacker moved between systems, accounts, applications, cloud resources, or network segments; stop additional movement; preserve evidence; and coordinate recovery.

- **Scope:**

    Applies to lateral movement across endpoints, servers, Active Directory, identity providers, VPN, remote administration tooling, cloud workloads, cloud control planes, SaaS applications, and third-party access paths. This playbook should be executed alongside account takeover, privilege escalation, malware, ransomware, cloud compromise, or data exfiltration playbooks when those conditions are present.

## 2. Incident Identification & Criteria

**Incident Type:** Lateral Movement

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- Remote logon, RDP, SSH, SMB, WMI, WinRM, PsExec, or remote admin activity from an unusual source
- Same account authenticating to multiple systems in an abnormal pattern
- Privileged account use from a non-standard host or unexpected geography
- Administrative tooling, remote monitoring tooling, or dual-use tooling used without approval
- New service, scheduled task, remote command, or script execution on another host
- Cloud role chaining, cross-account access, workload identity pivoting, or cross-tenant access
- Malware, ransomware, or suspicious execution with propagation capability
- Shared credential, token, API key, or service account use across multiple assets

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Suspicious movement indicator requiring validation; no confirmed compromise beyond initial entity |
| Sev 2 | Confirmed movement to one additional non-critical host, account, or application |
| Sev 1 | Movement across multiple systems, privileged accounts, production services, or sensitive environments |
| Sev 0 | Enterprise-wide propagation, domain/tenant compromise, ransomware spread, or critical infrastructure impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates response, approves containment scope, sets severity, and owns escalation decisions.
- **Incident Responder / Forensic Analyst:** Reconstructs movement path, identifies affected assets/accounts, analyses remote execution, and preserves evidence.
- **Communications Lead:** Coordinates internal updates, affected-user communications, and executive messaging.
- **Other Roles:**
    - **Identity & Access Team:** Reviews authentication paths, privileged accounts, service accounts, sessions, MFA, and token abuse.
    - **Endpoint / Infrastructure Team:** Supports host isolation, segmentation, evidence collection, rebuild, and recovery validation.
    - **Network Team:** Restricts lateral protocols and validates segmentation controls.
    - **Cloud Security / Platform Team:** Reviews cloud role assumptions, workload pivots, and cloud containment actions.
    - **Application / Service Owners:** Validate whether observed administrative activity was authorised and support recovery.
    - **Legal & Compliance:** Engaged if movement resulted in data access, exfiltration, customer impact, or regulated system exposure.

## 4. Initial Actions

- **Immediate Steps:**
    - Validate the alert and identify the initial source, destination, account, protocol, tool, timestamp, and affected business service.
        - 📘 [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
        - 📘 [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
        - 📘 [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
    - Determine whether movement is ongoing.
    - Engage infrastructure, identity, and service owners when containment may disrupt production.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If active movement is ongoing → isolate affected systems and restrict lateral protocols immediately.
    > - If historical movement only → preserve evidence first, then proceed with scoped containment.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Collect endpoint process, command-line, service creation, scheduled task, authentication, VPN, network, cloud, and SaaS logs for each source and destination.
        - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
        - 📘 [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
        - 📘 [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - Capture memory where credential theft, in-memory tooling, token theft, or active malware is suspected.
        - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)

- **Analysis Steps:**
    - Identify patient zero, earliest suspicious activity, and the first confirmed movement event.
        - 📘 [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
    - Review authentication timelines, cross-system logons, shared credentials, MFA events, and session reuse.
        - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - Identify additional compromised accounts, shared indicators, and adjacent identities.
        - 📘 [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
    - Assess privileged account exposure and administrative session hopping.
        - 📘 [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - Analyse remote execution chains, command lines, LOLBins, and scripts used to move or execute on destination systems.
        - 📘 [RB-ANALYSIS-006: Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)
        - 📘 [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
        - 📘 [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
        - 📘 [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - Validate whether the activity was approved administration, automation, deployment, or security testing.
        - 📘 [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - For cloud movement, review role assumptions, cross-account activity, resource changes, and persistence.
        - 📘 [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
    - Build and maintain an affected asset inventory.
        - 📘 [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)
    - Map observed techniques and identify detection gaps.
        - 📘 [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If privilege escalation is identified → execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) concurrently.
    > - If malware or suspicious execution drove movement → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) or [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) concurrently.
    > - If ransomware propagation is observed → execute [PB-002: Ransomware](PB-002-ransomware.md) concurrently.
    > - If data access or staging occurred on destination systems → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Isolate affected hosts and restrict remote administration protocols.
        - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - Segment impacted networks and block lateral movement paths such as SMB, RDP, PsExec, WMI, WinRM, SSH, and remote admin shares.
        - 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
    - Lock compromised accounts and revoke active sessions/tokens.
        - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
        - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - If Active Directory or privileged groups are affected, disable compromised domain accounts, remove unauthorised group memberships, block suspicious administrative sessions, and preserve domain controller evidence before making broad changes.
        - 📘 [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
    - Isolate affected cloud workloads where movement involved workload identities or cloud-hosted systems.
        - 📘 [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)

- **Eradication Steps:**
    - Remove malicious services, scheduled tasks, remote access tooling, scripts, accounts, credentials, access keys, and persistence mechanisms.
    - Rotate credentials and secrets used during movement, including shared local admin passwords, service account credentials, API keys, and cloud access keys.
    - Restore approved network, IAM, directory, and host configurations.

- **Recovery Steps:**
    - Rebuild systems where integrity is uncertain or persistence was identified.
        - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - Coordinate phased restoration and reintroduction of segmented systems.
        - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - Restore user access only after credential, token, and MFA containment is complete.
        - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

    > **Decision Point:**
    > If new movement occurs after containment, expand scope, re-check privileged access, and return to Investigation & Analysis.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, infrastructure owners, identity teams, affected service owners, and business stakeholders.
    - Use geo handoff where the incident spans response shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - Notify affected users if account resets, MFA resets, or access restoration are required.
        - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **External Communication:**
    - Engage Legal/Privacy if lateral movement reached customer data, regulated systems, partner environments, or externally hosted infrastructure.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Privilege escalation identified | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
    | Malware or suspicious execution identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) / [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) |
    | Ransomware propagation observed | [PB-002: Ransomware](PB-002-ransomware.md) |
    | Account compromise or token reuse identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Cloud movement or control plane abuse identified | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
    | Data staging or exfiltration identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Enterprise-wide spread or critical infrastructure impact | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a Post-Incident Review (PIR)
    - Document what worked, what didn't, and what needs improvement

- **Documentation Updates:**
    - Update this playbook, detection logic, segmentation standards, remote administration controls, and linked runbooks where required.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-002: Ransomware](PB-002-ransomware.md)
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
    - [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
    - [RB-TRIAGE-011: Cloud Platform Alert Triage](../runbooks/triage/RB-TRIAGE-011-cloud-platform-alert-triage.md)
    - [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
    - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
    - [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
    - [RB-EVIDENCE-004: Cloud Control Plane Log Acquisition](../runbooks/evidence/RB-EVIDENCE-004-cloud-control-plane-log-acquisition.md)
    - [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
    - [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)
    - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - [RB-ANALYSIS-009: Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
    - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
    - [RB-ANALYSIS-023: Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
    - [RB-ANALYSIS-024: LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
    - [RB-ANALYSIS-025: Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
    - [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - [RB-ANALYSIS-035: Affected Asset Identification](../runbooks/analysis/RB-ANALYSIS-035-affected-asset-identification.md)
    - [RB-ANALYSIS-043: Cloud Control Plane Activity Analysis](../runbooks/analysis/RB-ANALYSIS-043-cloud-control-plane-activity-analysis.md)
    - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
    - [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
    - [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - [RB-CONTAIN-015: Cloud Workload Isolation](../runbooks/contain/RB-CONTAIN-015-cloud-workload-isolation.md)
    - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
    - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
    - [RB-POST-001: Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

## 10. Appendices

## Contributor

**Jayden Vo**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
