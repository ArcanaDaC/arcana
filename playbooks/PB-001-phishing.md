# PB-001: Phishing & Credential Theft

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-001: Phishing & Credential Theft | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |

## 1. Purpose & Scope

- **Purpose:**
  
  This playbook outlines the end-to-end response process for phishing incidents, including credential harvesting, malicious attachments, and business email compromise (BEC). It is designed to rapidly determine if an email is malicious, contain impacted users and accounts, identify scope across the organisation, and prevent follow-on compromise (account takeover, malware, data exfiltration).

- **Scope:**
  
  Applies to all phishing incidents reported or detected across the organisation, including user-reported emails, email security tooling alerts, and downstream indicators of phishing-driven compromise. Covers all users, endpoints, and identity systems within the organisation.

## 2. Incident Identification & Criteria

**Incident Type:** Phishing & Credential Theft

**Trigger Conditions:**
- User reports a suspicious email
- Email security tooling alert (SEG, Defender, Proofpoint, etc.)
- Detection of known phishing indicators (IOCs)
- Reports of credential harvesting pages
- Suspicious inbox rules or login activity following an email

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Single user report, no interaction confirmed |
| Sev 2 | User clicked link or opened attachment |
| Sev 1 | Credentials submitted or malware executed |
| Sev 0 | Widespread phishing campaign or confirmed org-wide compromise |

## 3. Roles & Responsibilities
- **Incident Commander:** Coordinates and leads the response to the security incident; drives decisions and timelines; ensures communications, containment, and remediation actions are executed.
- **Incident Response Analyst:** Performs deep analysis of email artifacts, URLs, attachments, and endpoint telemetry where interaction is confirmed.
- **Communications Lead:** Manages internal and external communications, user notifications, and stakeholder updates.
- **Other Roles:**
  - **Identity & Access Team:** Supports account lockdown, session revocation, and MFA re-registration.
  - **Email Platform Team:** Assists with tenant-wide email removal and gateway rule deployment.

## 4. Initial Actions
#### Immediate Steps:
- Perform Email Header Analysis & extract urls and attachments:
  - 📘 [RB-TRIAGE-001: Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)
  >**Decision Point**
    > - If benign → close with documentation
    > - If suspicious/malicious → continue
- Analyse extracted URLs and attachments to determine intent and capability.
  - 📘 [RB-ANALYSIS-001: URL Detonation & Analysis](../runbooks/analysis/RB-ANALYSIS-001-url-analysis.md)


## 5. Investigation & Analysis
- Determine if any users had clicked the phishing link
  - 📘 [RB-ANALYSIS-012: Phishing Interaction Validation](../runbooks/analysis/RB-ANALYSIS-012-phishing-interaction-validation.md)
  - If so, did any users:
    - Submit credentials? 
      - If yes, check for any suspicious login activity immediately following the email delivery or credential submission.
    - Download and execute a malicious file?
  > **Decision Point:**
  > - Credential harvesting identified (and suspicious login activity observed) → Incorporate and execute the Analysis, Containment, Eradication, and Recovery steps of [PB-004: Account Takeover](PB-004-account-takeover.md) concurrently alongside this playbook. 
  > - Malware delivery identified → Incorporate and execute the Analysis, Containment, Eradication, and Recovery steps of [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) concurrently alongside this playbook. 
- Hunt for similar phishing emails to identify additional compromised accounts. 
  - 📘 [RB-001.5: Phishing Retro Hunt](../runbooks/analysis/RB-001.5-phishing-retro-hunt.md)
## 6. Containment, Eradication & Recovery

- **Containment Actions:**
  - 📘 [RB-001.4: Account Lockdown (IdP/SSO)](../runbooks/contain/RB-001.4-account-lockdown.md)
    - Disable or lock affected accounts 
    - Revoke active sessions and tokens of affected accounts
    - Reset password
    - Enforce MFA re-registration → 📘 [RB-004.4: MFA Reset & Validation](../runbooks/contain/RB-004.4-mfa-reset-validation.md)

- **Eradication Steps:**
  - 📘 [RB-001.6: Email Removal & Blocking](../runbooks/contain/RB-001.6-email-removal-blocking.md)
    - Remove phishing emails from all inboxes (tenant-wide)
    - Block sender and domain at email gateway
    - Block malicious URLs at email gateway, proxy, and DNS
    - Deploy detection rules to identify future variants

- **Recovery Steps:**
  - Restore account access for affected users once containment is confirmed
  
## 7. Communication & Escalation

- **Internal Communication:**
  - Notify affected users 
    - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)
  - Issue org-wide advisory if campaign scope is broad

- **External Communication:**
  - If customer impact suspected/confirmed, engage Legal/Privacy for regulatory assessment.
    - 📘 [SOP-003:  Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
  - Notify customers, regulators, or partners if credential data or personal information is confirmed exposed
  - Coordinate with Legal before any external notification

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Credential theft confirmed | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Malware execution confirmed | [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) |


## 8. Post-Incident Activitie
- **Lessons Learned:**
  - Schedule and conduct a Post-Incident Review (PIR)
  - Document what went well and what needs improvement
  - Identify detection gaps (email filtering, proxy rules, IdP alerts)
  - Review user awareness training effectiveness

- **Documentation Updates:**
  - Update this playbook if response steps need revision
  - Update linked runbooks with any new techniques or tooling

## 9. References & Linked Resources

- **Runbooks:**
  - [RB-001.1: Email Triage & Header Analysis](../runbooks/triage/RB-001.1-email-triage-header-analysis.md)
  - [RB-001.2: URL Detonation & Analysis](../runbooks/analysis/RB-001.2-url-analysis.md)
  - [RB-001.3: Credential Exposure Validation](../runbooks/triage/RB-001.3-credential-check.md)
  - [RB-001.4: Account Lockdown (IdP/SSO)](../runbooks/contain/RB-001.4-account-lockdown.md)
  - [RB-001.5: Phishing Retro Hunt](../runbooks/analysis/RB-001.5-phishing-retro-hunt.md)
  - [RB-001.6: Email Removal & Blocking](../runbooks/contain/RB-001.6-email-removal-blocking.md)
  - [RB-004.3: Session Token Revocation](../runbooks/contain/RB-004.3-session-token-revocation.md)
  - [RB-004.4: MFA Reset & Validation](../runbooks/contain/RB-004.4-mfa-reset-validation.md)

- **SOPs:**
  - [SOP-001: Paging an Engineering Team's On-Call](../sops/SOP-001-paging-engineering-oncall.md)
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **Knowledge Base Articles:**
  - [KB: Email Header Analysis Guide] ← link when available
  - [KB: Phishing Detection Patterns] ← link when available

- **MITRE ATT&CK:**
  - [T1566 — Phishing](https://attack.mitre.org/techniques/T1566/)
  - [T1204 — User Execution](https://attack.mitre.org/techniques/T1204/)

## 10. Appendices

- **Automation Opportunities:**
  - Auto-extract URLs and attachments from reported emails
  - Auto-detonate links in sandbox on receipt
  - Auto-search across tenant for matching IOCs (retro hunt)
  - Auto-remove confirmed phishing emails from all inboxes
  - Auto-disable accounts upon confirmed credential submission

- **Key Notes:**
  - Always assume credential reuse risk if credentials were exposed — check for reuse across other services
  - Prioritise session/token revocation over password reset alone — password resets do not invalidate active sessions
  - Retro hunting is critical — phishing campaigns are rarely isolated to a single user

- **Contact List:**
  - [Enter key personnel and escalation contacts]

---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
