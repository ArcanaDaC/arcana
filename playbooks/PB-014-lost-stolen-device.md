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

  This playbook outlines the response process for lost, misplaced, or stolen corporate devices. It is designed to assess risk, determine exposure, protect organisational data, contain potential compromise, and coordinate recovery activities.

- **Scope:**

  Applies to all corporate-owned or managed devices, including laptops, desktops, mobile phones, tablets, removable storage devices, and other endpoints containing organisational data.

## 2. Incident Identification & Criteria

**Incident Type:** Lost & Stolen Device

**Trigger Conditions:**

- User reports a lost corporate device
- User reports a stolen corporate device
- Device fails to check in with management platforms
- Physical security reports theft of corporate equipment
- Law enforcement notification received
- Device located in unexpected geographic location
- Device tampering suspected

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Device lost with no indication of unauthorised access |
| Sev 2 | Device stolen or location unknown, encryption confirmed |
| Sev 1 | Device stolen and contains sensitive data or privileged access |
| Sev 0 | Device theft linked to targeted attack, active compromise, or significant business impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates response activities and escalation decisions.

- **Technical Lead:** Coordinates investigation, containment, and recovery activities.

- **Communications Lead:** Coordinates stakeholder communications and user notifications.

- **Forensic Analyst:** Performs forensic review and evidence preservation where required.

- **Other Roles:**
  - Endpoint Management Team
  - Identity & Access Team
  - Physical Security Team
  - Legal & Compliance
  - Asset Management Team

## 4. Initial Actions

### Immediate Steps

- Obtain details of the missing device
- Identify assigned user
- Determine device type and ownership
- Determine last known location and time
- Determine whether the device is lost or stolen
- Start incident documentation
- Notify Incident Commander

### Runbooks

- [RB-TRIAGE-004: Lost & Stolen Device Validation](../runbooks/triage/RB-TRIAGE-004-lost-stolen-device-validation.md)

> **Decision Point**
>
> - Device recovered quickly and no exposure identified → Close incident with documentation
> - Device remains missing or stolen → Continue investigation and containment

## 5. Investigation & Analysis

### Determine Risk and Exposure

- Validate device management status
  - [RB-ANALYSIS-023: Device Security Posture Assessment](../runbooks/analysis/RB-ANALYSIS-023-device-security-posture-assessment.md)

- Determine data exposure risk
  - [RB-ANALYSIS-024: Device Data Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-024-device-data-exposure-assessment.md)

- Review authentication activity
  - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)

- Identify additional compromised accounts
  - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

> **Decision Point**
>
> - Suspicious authentication activity identified → Execute [PB-004: Account Takeover](PB-004-account-takeover.md)
> - Evidence of malware identified → Execute [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
> - Sensitive data exposure identified → Execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)

## 6. Containment, Eradication & Recovery

### Containment Actions

- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - Disable affected accounts where required
  - Revoke active sessions
  - Reset credentials

- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - Revoke active sessions and tokens

- [RB-CONTAIN-008: Remote Device Lock & Wipe](../runbooks/contain/RB-CONTAIN-008-remote-device-lock-wipe.md)
  - Lock device remotely
  - Wipe device where appropriate
  - Remove corporate access

### Eradication Steps

- Remove device trust relationships
- Remove device certificates
- Remove device registrations
- Remove cached access where possible

### Recovery Steps

- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- Provision replacement device
- Restore user access
- Validate security controls on replacement device
- Return user to normal operations

## 7. Communication & Escalation

### Internal Communication

- Notify management
- Notify Physical Security
- Notify Asset Management
- Notify affected business units where required

### External Communication

- Coordinate with Legal and Compliance if sensitive data may be exposed
- Coordinate with law enforcement where theft has occurred
- Notify external parties only as directed by Legal

### Escalation Criteria

| Condition | Escalate To |
|-----------|-------------|
| Suspicious authentication activity identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
| Malware identified on device | [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) |
| Sensitive data exposure identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
| Targeted theft suspected | [PB-006: Insider Threat](PB-006-insider-threat.md) |

## 8. Post-Incident Activities

### Lessons Learned

- Schedule and conduct a Post-Incident Review (PIR)
- Review effectiveness of device security controls
- Review effectiveness of asset tracking controls
- Identify process improvements

### Documentation Updates

- Update asset inventory records
- Update this playbook if required
- Update associated runbooks
- Document lessons learned

## 9. References & Linked Resources

### Playbooks

- [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
- [PB-004: Account Takeover](PB-004-account-takeover.md)
- [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
- [PB-006: Insider Threat](PB-006-insider-threat.md)

### Runbooks

- [RB-TRIAGE-004: Lost & Stolen Device Validation](../runbooks/triage/RB-TRIAGE-004-lost-stolen-device-validation.md)
- [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
- [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
- [RB-ANALYSIS-023: Device Security Posture Assessment](../runbooks/analysis/RB-ANALYSIS-023-device-security-posture-assessment.md)
- [RB-ANALYSIS-024: Device Data Exposure Assessment](../runbooks/analysis/RB-ANALYSIS-024-device-data-exposure-assessment.md)
- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
- [RB-CONTAIN-008: Remote Device Lock & Wipe](../runbooks/contain/RB-CONTAIN-008-remote-device-lock-wipe.md)
- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

## 10. Appendices

### Contact List

- Incident Response Team
- Endpoint Management Team
- Physical Security Team
- Asset Management Team
- Legal & Compliance

### Templates

- Lost Device Reporting Form
- Device Recovery Checklist
- Incident Timeline Template

### Process Flowchart

Device Reported Missing → Validation → Risk Assessment → Containment → Recovery → Post-Incident Review

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
