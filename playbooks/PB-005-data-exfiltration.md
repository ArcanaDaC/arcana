# PB-005: Data Exfiltration

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-005: Data Exfiltration | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

  This playbook outlines the end-to-end response process for suspected or confirmed data exfiltration incidents involving unauthorised access, collection, staging, transfer, theft, or exposure of organisational data. It is designed to identify impacted data, determine exposure scope, contain active exfiltration activity, preserve evidence, and coordinate legal, regulatory, and business response activities.

- **Scope:**

  Applies to all suspected or confirmed data exfiltration incidents across the organisation, including insider threats, external compromises, cloud and SaaS abuse, unauthorised file transfers, sensitive data exposure, and threat actor collection activities.

## 2. Incident Identification & Criteria

**Incident Type:** Data Exfiltration

**Trigger Conditions:**

- DLP alert generated
- Large outbound transfer detected
- Unusual cloud upload activity identified
- Suspicious archive creation activity detected
- Sensitive file access anomalies observed
- Unauthorised SaaS sharing identified
- Insider threat indicators observed
- Threat actor collection behaviour identified
- Third-party notification of exposed data received

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Suspicious transfer activity with no confirmed exposure |
| Sev 2 | Confirmed exfiltration of limited data |
| Sev 1 | Confirmed exfiltration of sensitive, confidential, or regulated data |
| Sev 0 | Large-scale data theft, public exposure, or critical business impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates and leads the incident response effort, approves containment actions, and manages escalation decisions.

- **Technical Lead:** Directs investigative activities, determines scope, and coordinates technical response actions.

- **Communications Lead:** Coordinates internal and external communications, executive updates, and stakeholder notifications.

- **Forensic Analyst:** Conducts forensic investigation, evidence preservation, timeline reconstruction, and root cause analysis.

- **Other Roles:**
  - Identity & Access Team
  - Cloud Security Team
  - Legal & Compliance
  - Data Owners
  - Business Stakeholders

## 4. Initial Actions

### Immediate Steps

- Determine whether exfiltration activity is currently ongoing
- Preserve logs and evidence immediately
- Identify affected systems, users, and datasets
- Notify Incident Commander
- Start incident documentation and timeline
- Assign investigation and containment responsibilities

### Runbooks

- [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
- [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)

> **Decision Point**
>
> - Active exfiltration identified → Proceed immediately to Containment actions
> - Historical exfiltration only → Continue Investigation & Analysis

## 5. Investigation & Analysis

### Determine Exfiltration Scope

- Review outbound traffic patterns
  - [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)

- Investigate data staging activity
  - [RB-ANALYSIS-019: Data Staging Investigation](../runbooks/analysis/RB-ANALYSIS-019-data-staging-investigation.md)

- Review cloud storage and SaaS activity
  - [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)

- Identify impacted data and business impact
  - [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)

- Hunt for additional affected systems and accounts
  - [RB-ANALYSIS-022: Exfiltration Scope Expansion Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scope-expansion-hunt.md)

- Review authentication activity
  - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)

- Identify additional compromised accounts
  - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

> **Decision Point**
>
> - Privileged account abuse identified → Execute [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
> - Cloud tenant compromise identified → Execute [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
> - Insider activity identified → Execute [PB-006: Insider Threat](PB-006-insider-threat.md)

## 6. Containment, Eradication & Recovery

### Containment Actions

- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - Disable compromised accounts
  - Revoke active sessions
  - Reset credentials
  - Enforce MFA re-registration

- [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
  - Isolate impacted systems

- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - Revoke active tokens and sessions

- [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
  - Block active exfiltration channels
  - Restrict outbound communications
  - Block identified destinations

### Eradication Steps

- Remove attacker access mechanisms
- Remove malicious tooling used for collection or transfer
- Remove unauthorised SaaS sharing configurations
- Remove unauthorised cloud storage access

### Recovery Steps

- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- Restore legitimate user access
- Validate corrective actions
- Restore normal business operations
- Monitor for recurring activity

## 7. Communication & Escalation

### Internal Communication

- Notify leadership and affected business units
- Provide regular incident updates
- Engage data owners for impact assessment

### External Communication

- Engage Legal and Compliance if regulated data is involved
- Notify customers, regulators, or partners as directed by Legal
- Coordinate all external communication through approved channels

### Escalation Criteria

| Condition | Escalate To |
|-----------|-------------|
| Insider activity identified | [PB-006: Insider Threat](PB-006-insider-threat.md) |
| Cloud tenant compromise | [PB-007: Cloud Compromise](PB-007-cloud-compromise.md) |
| Privileged account abuse | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
| Malware-assisted exfiltration | [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) |
| Ransomware-linked exfiltration | [PB-002: Ransomware](PB-002-ransomware.md) |

## 8. Post-Incident Activities

### Lessons Learned

- Schedule and conduct a Post-Incident Review (PIR)
- Document timeline and root cause
- Identify detection and response gaps
- Assess effectiveness of containment actions
- Review data governance controls

### Documentation Updates

- Update this playbook as required
- Update associated runbooks
- Update detection content and monitoring logic
- Update data handling and governance procedures

## 9. References & Linked Resources

### Playbooks

- [PB-002: Ransomware](PB-002-ransomware.md)
- [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
- [PB-006: Insider Threat](PB-006-insider-threat.md)
- [PB-007: Cloud Compromise](PB-007-cloud-compromise.md)
- [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)

### Runbooks

- [RB-TRIAGE-002: EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)
- [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
- [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
- [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
- [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
- [RB-ANALYSIS-019: Data Staging Investigation](../runbooks/analysis/RB-ANALYSIS-019-data-staging-investigation.md)
- [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
- [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)
- [RB-ANALYSIS-022: Exfiltration Scope Expansion Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scope-expansion-hunt.md)
- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
- [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
- [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

## 10. Appendices

### Contact List

- Incident Response Team
- Legal & Compliance
- Cloud Security Team
- Identity & Access Team
- Executive Stakeholders

### Templates

- Incident Timeline Template
- Regulatory Notification Template
- Evidence Collection Template

### Process Flowchart

Data Exfiltration Detection → Investigation & Analysis → Containment → Eradication → Recovery → Post-Incident Review

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**  
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.

