# PB-016: Business Email Compromise

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-016: Business Email Compromise | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**

  This playbook outlines the response process for Business Email Compromise (BEC) incidents involving compromised email accounts, executive impersonation, fraudulent payment requests, vendor impersonation, payroll fraud, and other financially motivated email-based attacks. The objective is to rapidly identify compromised accounts, contain attacker access, prevent financial loss, and assess potential data exposure.

- **Scope:**

  Applies to all BEC incidents involving organisational email systems, collaboration platforms, executive accounts, finance personnel, vendors, customers, and third-party communications.

## 2. Incident Identification & Criteria

**Incident Type:** Business Email Compromise

**Trigger Conditions:**

- User reports suspicious executive email
- User reports suspicious payment request
- Vendor reports unusual communication
- Mailbox compromise detected
- MFA fatigue activity detected
- Suspicious inbox rule creation detected
- Suspicious OAuth application activity detected
- Financial institution notification received
- Fraudulent payment identified
- Threat intelligence notification received

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Suspected BEC attempt with no confirmed compromise |
| Sev 2 | Confirmed account compromise with limited impact |
| Sev 1 | Confirmed BEC with fraudulent activity or sensitive data exposure |
| Sev 0 | Significant financial loss, executive compromise, or widespread organisational impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates incident response activities and escalation decisions.

- **Technical Lead:** Directs investigation, containment, eradication, and recovery activities.

- **Communications Lead:** Coordinates stakeholder communications and executive updates.

- **Forensic Analyst:** Conducts mailbox, authentication, and activity analysis.

- **Other Roles:**
  - Identity & Access Management Team
  - Email Administration Team
  - Finance Team
  - Legal & Compliance
  - Human Resources
  - Vendor Management Team

## 4. Initial Actions

### Immediate Steps

- Identify affected mailbox or user
- Determine whether compromise is active
- Notify Incident Commander
- Preserve evidence
- Start incident documentation
- Assign investigation responsibilities

### Runbooks

- [RB-TRIAGE-001: Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)
- [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
- [RB-TRIAGE-008: Business Email Compromise Validation](../runbooks/triage/RB-TRIAGE-008-business-email-compromise-validation.md)

> **Decision Point**
>
> - No account compromise identified → Continue monitoring and user awareness activities
> - Account compromise confirmed → Continue investigation and containment

## 5. Investigation & Analysis

### Determine Scope and Impact

- Analyse mailbox compromise activity
  - [RB-ANALYSIS-036: Mailbox Compromise Investigation](../runbooks/analysis/RB-ANALYSIS-036-mailbox-compromise-investigation.md)

- Review authentication activity
  - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)

- Identify additional compromised accounts
  - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

- Investigate email forwarding and inbox rules
  - [RB-ANALYSIS-037: Mail Forwarding & Inbox Rule Analysis](../runbooks/analysis/RB-ANALYSIS-037-mail-forwarding-inbox-rule-analysis.md)

- Investigate financial fraud exposure
  - [RB-ANALYSIS-038: Financial Fraud Impact Assessment](../runbooks/analysis/RB-ANALYSIS-038-financial-fraud-impact-assessment.md)

> **Decision Point**
>
> - Additional account compromise identified → Execute [PB-004: Account Takeover](PB-004-account-takeover.md)
> - Data exposure identified → Execute [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
> - Insider involvement suspected → Execute [PB-006: Insider Threat](PB-006-insider-threat.md)

## 6. Containment, Eradication & Recovery

### Containment Actions

- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)

- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)

- [RB-CONTAIN-013: BEC Mailbox Containment](../runbooks/contain/RB-CONTAIN-013-bec-mailbox-containment.md)

### Eradication Steps

- Remove attacker persistence mechanisms
- Remove malicious inbox rules
- Remove unauthorised forwarding rules
- Remove unauthorised OAuth applications
- Reset compromised credentials

### Recovery Steps

- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- Restore mailbox security settings
- Validate MFA enrollment
- Restore normal business communications
- Monitor for recurring compromise activity

## 7. Communication & Escalation

### Internal Communication

- Notify leadership
- Notify Finance Team
- Notify Email Administration Team
- Notify affected business units

### External Communication

- Notify vendors if fraudulent communications occurred
- Coordinate with financial institutions if required
- Coordinate with Legal and Compliance where appropriate

### Escalation Criteria

| Condition | Escalate To |
|-----------|-------------|
| Additional account compromise identified | [PB-004: Account Takeover](PB-004-account-takeover.md) |
| Data exposure identified | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
| Insider involvement suspected | [PB-006: Insider Threat](PB-006-insider-threat.md) |
| Malware identified | [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) |

## 8. Post-Incident Activities

### Lessons Learned

- Schedule and conduct a Post-Incident Review (PIR)
- Review email security controls
- Review MFA effectiveness
- Review payment verification processes
- Review vendor communication procedures

### Documentation Updates

- Update detections
- Update playbooks and runbooks
- Update awareness material
- Document lessons learned

## 9. References & Linked Resources

### Playbooks

- [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
- [PB-004: Account Takeover](PB-004-account-takeover.md)
- [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
- [PB-006: Insider Threat](PB-006-insider-threat.md)

### Runbooks

- [RB-TRIAGE-001: Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)
- [RB-TRIAGE-003: Identity Alert Triage](../runbooks/triage/RB-TRIAGE-003-identity-alert-triage.md)
- [RB-TRIAGE-008: Business Email Compromise Validation](../runbooks/triage/RB-TRIAGE-008-business-email-compromise-validation.md)
- [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
- [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
- [RB-ANALYSIS-036: Mailbox Compromise Investigation](../runbooks/analysis/RB-ANALYSIS-036-mailbox-compromise-investigation.md)
- [RB-ANALYSIS-037: Mail Forwarding & Inbox Rule Analysis](../runbooks/analysis/RB-ANALYSIS-037-mail-forwarding-inbox-rule-analysis.md)
- [RB-ANALYSIS-038: Financial Fraud Impact Assessment](../runbooks/analysis/RB-ANALYSIS-038-financial-fraud-impact-assessment.md)
- [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
- [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
- [RB-CONTAIN-013: BEC Mailbox Containment](../runbooks/contain/RB-CONTAIN-013-bec-mailbox-containment.md)
- [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

## 10. Appendices

### Contact List

- Incident Response Team
- Email Administration Team
- Identity & Access Team
- Finance Team
- Legal & Compliance

### Templates

- BEC Investigation Template
- Financial Fraud Assessment Template
- Incident Timeline Template

### Process Flowchart

BEC Alert → Validation → Investigation → Containment → Recovery → Post-Incident Review

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
