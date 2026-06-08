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

- Incident Responder / Forensic Analyst: Performs forensic investigation, determines exfiltration scope, preserves evidence, reconstructs the attack timeline, and identifies root cause.

- **Communications Lead:** Coordinates internal and external communications, executive updates, and stakeholder notifications.

- **Other Roles:**
	- **Identity & Access (IAM) Team:** Locks down compromised accounts, revokes sessions/tokens, and rotates credentials.
	- **Cloud Security Team:** Investigates and remediates exfiltration via cloud storage, SaaS, and cloud workloads.
	- **Data Owners:** Assess data sensitivity, regulatory classification, and business impact.
	- **Legal & Compliance:** Assesses regulatory and breach notification obligations; owns external notification decisions.
	- **HR / People Team:** Engaged where insider activity is suspected or out-of-band user contact is required.

## 4. Initial Actions

- **Immediate Steps:**
  - Triage the originating alert or report to validate it represents real exfiltration activity
    - 📘 [RB-TRIAGE-010: Suspected Data Loss Triage](../runbooks/triage/RB-TRIAGE-010-suspected-data-loss-triage.md)
  - Determine whether exfiltration is currently active (e.g. traffic to known C2 / suspicious domain, uploads to personal cloud storage)
  - Determine what type and volume of data is being exfiltrated (sensitive file names/paths, large size, high file count)
  - Identify the account(s) and host(s) being used to perform the exfiltration

  > **Decision Point:**
  > - Active exfiltration identified → Proceed immediately to Containment actions
  > - Historical exfiltration only → Continue Investigation & Analysis

## 5. Investigation & Analysis

- **Determine Exfiltration Scope:**
  - Review outbound traffic patterns
    - 📘 [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
  - Investigate data staging activity
    - 📘 [RB-ANALYSIS-019: Data Staging Investigation](../runbooks/analysis/RB-ANALYSIS-019-data-staging-investigation.md)
  - Review cloud storage and SaaS activity
    - 📘 [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
  - Identify impacted data and business impact
    - 📘 [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)
  - Hunt for additional exfiltration
    - 📘 [RB-ANALYSIS-022: Exfiltration Scoping Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scoping-hunt.md)
  - Review authentication activity
    - 📘 [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
  - Identify additional compromised accounts
    - 📘 [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

  
  > **Decision Point:**
  > For each identified initial access vector, run the post-detection phases (Analysis → Recovery) of the relevant playbook concurrently alongside this one:
  > - Phishing → [PB-001: Phishing & Credential Theft](PB-001-phishing.md)
  > - Account takeover → [PB-004: Account Takeover](PB-004-account-takeover.md)
  > - Endpoint malware → [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
  > - Ransomware activity observed alongside exfil → [PB-002: Ransomware](PB-002-ransomware.md)
  > - Active exploitation → [PB-015: Active Exploitation](PB-015-active-exploitation.md)
  > - Zero-day exploitation → [PB-018: Zero-Day Response](PB-018-zero-day-response.md)

## 6. Containment, Eradication & Recovery

- **Containment Actions:**
  - Disable compromised accounts, revoke active sessions, reset credentials, and enforce MFA re-registration
    - 📘 [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - Isolate impacted systems
    - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
  - Revoke active tokens and sessions
    - 📘 [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - Block active exfiltration channels, restrict outbound communications, and block identified destinations
    - 📘 [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)

- **Eradication Steps:**
  - Remove attacker access mechanisms
  - Remove malicious tooling used for collection or transfer
  - Remove unauthorised SaaS sharing configurations
  - Remove unauthorised cloud storage access

- **Recovery Steps:**
  - Restore legitimate user access
    - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
  - Validate corrective actions
  - Restore normal business operations
  - Monitor for recurring activity

## 7. Communication & Escalation

- **Internal Communication:**
  - Notify leadership and affected business units
  - Provide regular incident updates
  - Engage data owners for impact assessment

- **External Communication:**
  - Engage Legal and Compliance if regulated data is involved
  - Notify customers, regulators, or partners as directed by Legal
  - Coordinate all external communication through approved channels

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Phishing identified as initial access vector | [PB-001: Phishing & Credential Theft](PB-001-phishing.md) |
  | Account takeover identified as initial access vector | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Endpoint malware identified as initial access vector | [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md) |
  | Ransomware activity observed alongside exfil (double extortion) | [PB-002: Ransomware](PB-002-ransomware.md) |
  | Active exploitation identified | [PB-015: Active Exploitation](PB-015-active-exploitation.md) |
  | Zero-day exploitation identified | [PB-018: Zero-Day Response](PB-018-zero-day-response.md) |
  | Insider activity identified | [PB-006: Insider Threat](PB-006-insider-threat.md) |

## 8. Post-Incident Activities

- **Lessons Learned:**
  - Schedule and conduct a Post-Incident Review (PIR)
  - Document timeline and root cause
  - Identify detection and response gaps
  - Assess effectiveness of containment actions
  - Review data governance controls

- **Documentation Updates:**
  - Update this playbook as required
  - Update associated runbooks
  - Update detection content and monitoring logic
  - Update data handling and governance procedures

## 9. References & Linked Resources

- **Playbooks:**
  - [PB-001: Phishing & Credential Theft](PB-001-phishing.md)
  - [PB-002: Ransomware](PB-002-ransomware.md)
  - [PB-003: Endpoint Malware Infection](PB-003-endpoint-malware.md)
  - [PB-004: Account Takeover](PB-004-account-takeover.md)
  - [PB-006: Insider Threat](PB-006-insider-threat.md)
  - [PB-015: Active Exploitation](PB-015-active-exploitation.md)
  - [PB-018: Zero-Day Response](PB-018-zero-day-response.md)

- **Runbooks:**
  - [RB-TRIAGE-010: Suspected Data Loss Triage](../runbooks/triage/RB-TRIAGE-010-suspected-data-loss-triage.md)
  - [RB-ANALYSIS-007: Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
  - [RB-ANALYSIS-011: Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)
  - [RB-ANALYSIS-018: Outbound Traffic Analysis](../runbooks/analysis/RB-ANALYSIS-018-outbound-traffic-analysis.md)
  - [RB-ANALYSIS-019: Data Staging Investigation](../runbooks/analysis/RB-ANALYSIS-019-data-staging-investigation.md)
  - [RB-ANALYSIS-020: Cloud Storage & SaaS Review](../runbooks/analysis/RB-ANALYSIS-020-cloud-storage-saas-review.md)
  - [RB-ANALYSIS-021: Sensitive Data Impact Assessment](../runbooks/analysis/RB-ANALYSIS-021-sensitive-data-impact-assessment.md)
  - [RB-ANALYSIS-022: Exfiltration Scoping Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scoping-hunt.md)
  - [RB-CONTAIN-001: Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
  - [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
  - [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - [RB-CONTAIN-007: Outbound Transfer Blocking](../runbooks/contain/RB-CONTAIN-007-outbound-transfer-blocking.md)
  - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

## 10. Appendices

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

**Jayden Vo**  
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.

