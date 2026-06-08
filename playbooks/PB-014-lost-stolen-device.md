# PB-014: Lost & Stolen Device

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-014: Lost & Stolen Device | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | Initial creation | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

    Provide a structured response for lost, misplaced, or stolen organisational devices. Use this playbook to validate the report, assess device and data exposure, contain access, coordinate device recovery or replacement, and restore the user safely.

- **Scope:**

    Applies to corporate-owned or managed laptops, desktops, mobile phones, tablets, removable media, and other endpoints that may contain organisational data or provide access to organisational systems.

## 2. Incident Identification & Criteria

**Incident Type:** Lost & Stolen Device

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- User, manager, physical security, asset management, or law enforcement reports a lost or stolen organisational device
- Managed device reports unexpected location, tampering, jailbreak/rooting, or suspicious check-in activity
- Device containing organisational data, credentials, certificates, or privileged access is unaccounted for
- Recovered device shows signs of unauthorised access, tampering, malware, or policy bypass

**Severity Levels:**

| Severity | Description |
|----------|-------------|
| Sev 3 | Device misplaced or recovered quickly; encryption and management controls appear intact |
| Sev 2 | Device remains missing or stolen; encryption and management controls are confirmed |
| Sev 1 | Device may expose sensitive data, credentials, privileged access, or critical business systems |
| Sev 0 | Device theft is targeted, linked to active compromise, or creates major business/customer impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Sets severity, coordinates response, approves containment, and owns escalation decisions.
- **Incident Responder / Forensic Analyst:** Validates the report, assesses exposure, reviews activity, and preserves evidence.
- **Communications Lead:** Coordinates affected-user, management, legal, and stakeholder communications.
- **Other Roles:**
    - **Endpoint / MDM Team:** Confirms device posture and performs remote lock, wipe, or access removal.
    - **Identity & Access Team:** Locks accounts, revokes sessions, resets credentials, and validates safe access restoration.
    - **Physical Security / Asset Management:** Supports theft reporting, asset tracking, recovery, chain of custody, and replacement.
    - **Legal / Compliance:** Assesses sensitive data exposure, law enforcement coordination, regulatory obligations, and customer impact.
    - **User's Manager:** Supports employee verification, business continuity, and replacement device coordination.

## 4. Initial Actions

- **Immediate Steps:**
    - Verify the employee and collect the report details before making high-impact access or device changes.
        - 📘 [SOP-006: Employee Verification During a Security Incident](../sops/SOP-006-employee-verification.md)
    - Validate device ownership, assigned user, device type, asset ID, last known location, last seen time, and loss/theft circumstances.
        - 📘 [RB-TRIAGE-006: Lost & Stolen Device Validation](../runbooks/triage/RB-TRIAGE-006-lost-stolen-device-validation.md)
    - Start the incident record and preserve available MDM, EDR, IdP, VPN, SIEM, and asset inventory telemetry.
    - Notify Incident Commander, endpoint/MDM team, identity team, asset management, and physical security as required.
        - 📘 [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)

    > **Decision Point:**
    > - If the device is recovered quickly and no exposure is identified → document evidence and close or downgrade.
    > - If the device remains missing, stolen, tampered with, or untrusted → continue investigation and containment.
    > - If suspicious account, device, or network activity is observed → begin containment in parallel.

## 5. Investigation & Analysis

- **Evidence Collection:**
    - Collect host, MDM, EDR, asset, location, and endpoint telemetry for the missing device.
        - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
    - Collect identity, authentication, VPN, session, MFA, and device-trust telemetry for the assigned user.
        - 📘 [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
    - Document device owner, asset identifiers, last known activity, security controls, accessible data, credentials, and containment actions.

- **Analysis Steps:**
    - Validate device management, encryption, EDR, compliance, remote lock/wipe capability, and last check-in status.
        - 📘 [RB-ANALYSIS-032: Device Security Posture Assessment](../runbooks/analysis/RB-ANALYSIS-032-device-security-posture-assessment.md)
    - Assess local data, cached data, synced files, credentials, certificates, tokens, and business data exposure.
        - 📘 [RB-ANALYSIS-033: Device Data Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-033-device-data-exposure-assessment.md)
    - Review authentication activity, MFA events, VPN use, device trust, and geographic anomalies for the assigned user.
        - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - Review user, endpoint, network, file access, and authentication activity associated with the missing device.
        - 📘 [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)

    > **Decision Point:**
    > Run the post-detection phases (Analysis → Recovery) of any relevant sibling playbook concurrently alongside this one based on what was observed:
    > - If account compromise or credential abuse is suspected or identified → execute [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently.
    > - If data exposure, staging, or exfiltration is suspected or identified → execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) concurrently.
    > - If malware or suspicious execution is suspected or identified → execute [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) or [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) concurrently.
    > - If privilege escalation is suspected or identified → execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) concurrently.
    > - If lateral movement is suspected or identified → execute [PB-010: Lateral Movement](PB-010-lateral-movement.md) concurrently.
    > - If targeted theft, insider involvement, or physical access abuse is suspected → execute [PB-006: Insider Threat](PB-006-insider-threat.md) concurrently.

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
    - Lock affected accounts, reset credentials where needed, and revoke active sessions, tokens, VPN sessions, and device trust.
        - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
        - 📘 [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - Remotely lock or wipe the missing device when approved and technically available.
        - 📘 [RB-CONTAIN-011: Remote Device Lock & Wipe](../runbooks/contain/RB-CONTAIN-011-remote-device-lock-wipe.md)
    - Remove device registrations, certificates, conditional access trust, managed app access, and endpoint management access for untrusted devices.

- **Eradication Steps:**
    - Remove cached access, stale device objects, certificates, local admin rights, and device trust relationships.
    - Rotate exposed credentials, certificates, tokens, API keys, or secrets identified during exposure analysis.
    - Treat recovered devices as untrusted until inspected, rebuilt, or re-enrolled according to endpoint standards.

- **Recovery Steps:**
    - Verify the employee before restoring access, issuing replacement hardware, or re-enrolling MFA.
        - 📘 [SOP-006: Employee Verification During a Security Incident](../sops/SOP-006-employee-verification.md)
    - Restore user access only after containment is complete and account/device integrity is validated.
        - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
    - Provision a replacement device, enforce security baseline, validate encryption/EDR/MDM, and update asset inventory.

## 7. Communication & Escalation

- **Internal Communication:**
    - Notify security leadership, endpoint/MDM team, identity team, physical security, asset management, user manager, and affected business stakeholders.
    - Notify the affected user with required actions after verification.
        - 📘 [SOP-004: User Notification During a Security Incident](../sops/SOP-004-user-notification.md)
    - Use geo handoff when the incident spans response shifts.
        - 📘 [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)

- **External Communication:**
    - Coordinate legal, law enforcement, customer, regulator, and executive communications through approved escalation processes.
        - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)

- **Escalation Criteria:**

    | Condition | Escalate To |
    |-----------|-------------|
    | Account compromise or credential abuse suspected or identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
    | Sensitive data exposure, staging, or exfiltration suspected or identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
    | Malware or suspicious execution suspected or identified | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) / [PB-011: Suspicious Execution](PB-011-suspicious-execution.md) |
    | Privilege escalation suspected or identified | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
    | Lateral movement suspected or identified | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
    | Targeted theft, insider involvement, or physical access abuse suspected | [PB-006: Insider Threat](PB-006-insider-threat.md) |
    | Major business/customer impact or regulated data exposure | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
    - Conduct a PIR covering reporting speed, employee verification, device posture, lock/wipe timing, access containment, data exposure, communications, and replacement workflow.
    - Review device encryption, MDM/EDR coverage, asset tracking, conditional access, remote wipe readiness, and user reporting guidance.

- **Documentation Updates:**
    - Update asset inventory, device recovery records, lost-device procedures, endpoint baselines, detection content, and this playbook as needed.

## 9. References & Linked Resources

- **Playbooks:**
    - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
    - [PB-004: Account Takeover](PB-004-account-takeover.md)
    - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
    - [PB-006: Insider Threat](PB-006-insider-threat.md)
    - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
    - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
    - [PB-011: Suspicious Execution](PB-011-suspicious-execution.md)
    - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
    - [RB-TRIAGE-006: Lost & Stolen Device Validation](../runbooks/triage/RB-TRIAGE-006-lost-stolen-device-validation.md)
    - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
    - [RB-EVIDENCE-003: Identity & Authentication Log Acquisition](../runbooks/evidence/RB-EVIDENCE-003-identity-log-acquisition.md)
    - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
    - [RB-ANALYSIS-026: User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
    - [RB-ANALYSIS-032: Device Security Posture Assessment](../runbooks/analysis/RB-ANALYSIS-032-device-security-posture-assessment.md)
    - [RB-ANALYSIS-033: Device Data Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-033-device-data-exposure-assessment.md)
    - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - [RB-CONTAIN-005: Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    - [RB-CONTAIN-011: Remote Device Lock & Wipe](../runbooks/contain/RB-CONTAIN-011-remote-device-lock-wipe.md)
    - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- **SOPs:**
    - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
    - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
    - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - [SOP-004: User Notification During a Security Incident](../sops/SOP-004-user-notification.md)
    - [SOP-006: Employee Verification During a Security Incident](../sops/SOP-006-employee-verification.md)

## 10. Appendices

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
