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
- Conduct a phishing retro hunt to determine full campaign scope and identify additional compromised accounts 
  - 📘 [RB-ANALYSIS-002: Phishing Retro Hunt](../runbooks/analysis/RB-ANALYSIS-002-phishing-retro-hunt.md)
## 6. Containment, Eradication & Recovery

- **Containment Actions:**
  - 📘 [RB-CONTAIN-001 Account Lockdown (IdP/SSO)](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
    - Disable or lock affected accounts 
    - Revoke active sessions and tokens of affected accounts
    - Reset password
    - Enforce MFA re-registration 

- **Eradication Steps:**
  - 📘 [RB-ERAD-001: Email Removal & Blocking](../runbooks/eradication/RB-ERAD-001-email-removal-blocking.md)
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
  - If privacy impact suspected/confirmed, engage Legal/Privacy for regulatory assessment.
  - Notify all required external parties (e.g. customers, regulators, partners) as directed by Legal
  - Coordinate with Legal before any external notification

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Credential theft confirmed + Suspicious Login Actiity Observed | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Malware execution confirmed | [PB-003: Endpoint Malware](PB-003-endpoint-malware.md) |


## 8. Post-Incident Activities
- **Lessons Learned:**
  - Schedule and conduct a Post-Incident Review (PIR)
  - Document what went well and what needs improvement
  - Identify detection gaps (email filtering, proxy rules, IdP alerts)
  - Review user awareness training effectiveness

- **Documentation Updates:**
  - Update this playbook if response steps need revision
  - Update linked runbooks with any new techniques or tooling

## 9. References & Linked Resources
- **Playbooks:**
  - [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
  - [PB-004: Account Takeover](PB-004-account-takeover.md)

- **Runbooks:**
  - [RB-TRIAGE-001: Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)
  - [RB-ANALYSIS-001: URL Detonation & Analysis](../runbooks/analysis/RB-ANALYSIS-001-url-analysis.md)
  - [RB-ANALYSIS-002: Phishing Retro Hunt](../runbooks/analysis/RB-ANALYSIS-002-phishing-retro-hunt.md)
  - [RB-ANALYSIS-012: Phishing Interaction Validation](../runbooks/analysis/RB-ANALYSIS-012-phishing-interaction-validation.md)
  - [RB-CONTAIN-001: Account Lockdown (IdP/SSO)](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - [RB-ERAD-001: Email Removal & Blocking](../runbooks/eradication/RB-ERAD-001-email-removal-blocking.md)

- **SOPs:**
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

## 10. Appendices
---

## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
