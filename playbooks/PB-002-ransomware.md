# PB-002: Ransomware Incident Response

## Document Control

| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | PB-002: Ransomware Incident Response | [Enter date] |
| Version | [Enter version number] | [Enter date] |
| Owner | [Enter owner/team] | [Enter date] |
| Status | [Draft/Approved/Retired] | [Enter date] |
| Next Review Date | [Enter next review date] | [Enter date] |
| Approvals | [Enter approver(s)] | [Enter date] |
| Change Summary | [Brief summary of changes] | [Enter date] |


## 1. Purpose & Scope

- **Purpose:**

  This playbook outlines the end-to-end response process for ransomware incidents, including containment, scoping, eradication, recovery, and post-incident hardening. 

- **Scope:**

  Applies to all ransomware-related incidents across the organisation, including:
  - Endpoint ransomware
  - Server encryption events
  - Hypervisor / ESXi ransomware
  - Double extortion incidents
  - Large-scale enterprise encryption activity


## 2. Incident Identification & Criteria

**Incident Type:** Ransomware

**Trigger Conditions:**

Initiate this playbook when any of the following occur:
- Ransom note detected
- Sudden file extension changes observed
- EDR ransomware alert triggered
- Multiple systems simultaneously encrypted
- Backup deletion activity detected
- ESXi or hypervisor encryption identified
- Mass file rename/write activity detected

**Severity Levels:**

| Severity | Description |
|----------|------------|
| Sev 3 | Suspected ransomware activity on a single endpoint, not yet confirmed |
| Sev 2 | Confirmed ransomware on a single isolated system with no observed propagation |
| Sev 1 | Confirmed ransomware impacting multiple systems or a business-critical service |
| Sev 0 | Enterprise-wide propagation, hypervisor/backup compromise, or critical infrastructure impact |

## 3. Roles & Responsibilities

- **Incident Commander:** Coordinates and leads the response to the ransomware incident; drives decisions and timelines; ensures containment, communications, and remediation actions are executed.
- **Communications Lead:** Manages internal and external communications, executive updates, customer/regulator notifications, and stakeholder messaging.
- **Forensic Analyst:** Performs forensic analysis of impacted hosts, ransomware payload analysis, identifies patient zero, maps the attack timeline, and preserves evidence.
- **Other Roles:**
  - **Identity & Access Team:** Supports Active Directory containment, privileged account review, session revocation, and credential resets.
  - **Network/Infrastructure Team:** Executes network segmentation, host isolation, and protects critical infrastructure.
  - **Backup & Recovery Team:** Validates backup integrity, isolates backup infrastructure, and coordinates restoration.
  - **Legal & Compliance:** Assesses regulatory obligations, breach notification requirements, and ransom payment considerations.
  - **Executive Leadership / Crisis Management:** Approves major business decisions, authorises external communications, and coordinates with law enforcement where required.

## 4. Initial Actions

- **Immediate Steps:**
  - Perform rapid containment & segmentation — isolate affected systems and disable lateral movement pathways (restrict SMB, remote admin protocols)
    - 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
  -  Notify Incident Response leadership and assign roles
  - Preserve volatile evidence where feasible (avoid additional system shutdowns or reboots unless required)
    - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
  - Identify critical business systems impacted
  - Freeze non-essential administrative changes

  > **Decision Point:**
  > - If ransomware propagation continues → expand containment scope and escalate to crisis response / major incident management ([PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)).

## 5. Investigation & Analysis

- **Required Inputs:**
  - EDR telemetry
  - SIEM logs
  - Network telemetry
  - User reports
  - Ransom notes
  - File hashes
  - Active Directory logs
  - Backup platform logs

- **Evidence Collection:**
  - [ ] Gather relevant logs, alerts, ransom notes, and forensic artifacts
  - [ ] Preserve evidence (chain of custody) including memory captures from impacted hosts
    - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
    - 📘 [RB-ANALYSIS-016: Memory Analysis](../runbooks/analysis/RB-ANALYSIS-016-memory-analysis.md)

- **Analysis Steps:**
  - [ ] Identify patient zero, initial access vector, propagation path, and dwell time
    - 📘 [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
    > **Decision Point:**
    > - If phishing identified as the initial access vector → incorporate and execute [PB-001: Phishing & Credential Theft](PB-001-phishing.md) concurrently alongside this playbook.
  - [ ] Assess encryption scope, impacted systems, encrypted file shares, business impact, and backup exposure
    - 📘 [RB-ANALYSIS-004: Encryption Scope Assessment](../runbooks/analysis/RB-ANALYSIS-004-encryption-scope-assessment.md)
    > **Decision Point:**
    > - If backup compromise identified → immediate executive escalation.
  - [ ] Analyse ransomware payload and behaviour (family, encryption behaviour, persistence, capabilities, exfiltration)
    - 📘 [RB-ANALYSIS-013: Ransomware Payload Analysis](../runbooks/analysis/RB-ANALYSIS-013-ransomware-payload-analysis.md)
    > **Decision Point:**
    > - If data exfiltration identified → escalate to [PB-005: Data Exfiltration](PB-005-data-exfiltration.md).
  - [ ] Map threat actor TTPs, correlate with known ransomware groups, and update detections/threat intelligence
    - 📘 [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)
  - [ ] Document findings, timeline of compromise, and indicators of compromise (IOCs)

## 6. Containment, Eradication & Recovery

  > **Warning:** Do NOT begin large-scale restoration activities until:
  > - Containment is verified
  > - Persistence mechanisms are identified
  > - Privileged access has been reviewed
  > - Propagation paths are understood
  > - Backup integrity is validated
  >
  > Premature restoration may result in reinfection or repeated encryption.

- **Containment Actions:**
  - **Short-term (immediate) containment:**
    - [ ] Isolate impacted hosts and segment impacted networks
      - 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
      - 📘 [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
    - [ ] Restrict SMB and remote admin protocols, prevent additional propagation, protect critical infrastructure
  - **Long-term (identity & directory) containment:**
    - [ ] Review privileged account activity, disable compromised accounts, protect identity infrastructure
      - 📘 [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
      - 📘 [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    > **Decision Point:**
    > - If Domain Admin compromise confirmed → immediate enterprise-wide escalation.

- **Eradication Steps:**
  - [ ] Remove malicious artifacts and ransomware payloads from impacted systems
    - 📘 [RB-ANALYSIS-013: Ransomware Payload Analysis](../runbooks/analysis/RB-ANALYSIS-013-ransomware-payload-analysis.md)
  - [ ] Hunt for and remove persistence mechanisms
    - 📘 [RB-ANALYSIS-014: Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-persistence-mechanism-hunt.md)
  - [ ] Patch vulnerabilities exploited during the intrusion

- **Recovery Steps:**
  - [ ] Validate backup integrity, isolation, immutable storage integrity, and recovery viability
    - 📘 [RB-ANALYSIS-017: Backup Integrity & Recovery Viability Assessment](../runbooks/analysis/RB-ANALYSIS-017-backup-integrity-recovery-viability-assessment.md)
    > **Decision Point:**
    > - If backups unavailable or compromised → escalate severity immediately.
  - [ ] Prioritise and coordinate phased system restoration; validate restored systems
    - 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
    - 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
  - [ ] Restore user access in a controlled manner
    - 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
  - [ ] Monitor for reinfection and reintroduce systems gradually
    > **Decision Point:**
    > - If reinfection activity observed → halt restoration activities immediately and return to containment.

## 7. Communication & Escalation

- **Internal Communication:**
  - [ ] Notify executive leadership and affected business units
  - [ ] Provide regular incident updates to leadership and impacted teams
  - [ ] Issue org-wide advisory if propagation is broad or critical services are impacted

- **External Communication:**
  - [ ] Engage Legal/Privacy to assess regulatory and breach notification obligations
  - [ ] Notify customers, regulators, partners, cyber insurance, and law enforcement (if required) as directed by Legal
  - [ ] Coordinate all external messaging with Communications Lead and Legal
    - 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
    - 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **Escalation Criteria:**

  | Condition | Escalate To |
  |-----------|-------------|
  | Phishing identified as initial access vector | [PB-001: Phishing & Credential Theft](PB-001-phishing.md) |
  | Data exfiltration confirmed | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
  | Privileged account compromise | [PB-009: Privilege Escalation](PB-009-privilege-escalation.md) |
  | Lateral movement observed across the estate | [PB-010: Lateral Movement](PB-010-lateral-movement.md) |
  | Enterprise-wide propagation, hypervisor or backup compromise | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) / Executive escalation |

## 8. Post-Incident Activities

- **Lessons Learned:**
  - [ ] Schedule and conduct a Post-Incident Review (PIR)
  - [ ] Document what went well and what needs improvement
  - [ ] Review control failures (detection, segmentation, privileged access, backup protection)
  - [ ] Identify and close detection gaps

- **Documentation Updates:**
  - [ ] Update this playbook, linked runbooks, and KB articles to reflect lessons learned
  - [ ] Update detections and threat intelligence based on observed TTPs
  - [ ] Harden segmentation, privileged access, and backup protections
    - 📘 [RB-POST-001: Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-post-incident-hardening.md)

## 9. References & Linked Resources

- **Playbooks:**
  - [PB-001: Phishing & Credential Theft](PB-001-phishing.md)
  - [PB-003: Endpoint Malware](PB-003-endpoint-malware.md)
  - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
  - [PB-009: Privilege Escalation](PB-009-privilege-escalation.md)
  - [PB-010: Lateral Movement](PB-010-lateral-movement.md)
  - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
  - [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
  - [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
  - [RB-CONTAIN-004: Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)
  - [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
  - [RB-ANALYSIS-004: Encryption Scope Assessment](../runbooks/analysis/RB-ANALYSIS-004-encryption-scope-assessment.md)
  - [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)
  - [RB-ANALYSIS-013: Ransomware Payload Analysis](../runbooks/analysis/RB-ANALYSIS-013-ransomware-payload-analysis.md)
  - [RB-ANALYSIS-014: Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-persistence-mechanism-hunt.md)
  - [RB-POST-001: Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-post-incident-hardening.md)
  - [RB-ANALYSIS-016: Memory Analysis](../runbooks/analysis/RB-ANALYSIS-016-memory-analysis.md)
  - [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
  - [RB-ANALYSIS-017: Backup Integrity & Recovery Viability Assessment](../runbooks/analysis/RB-ANALYSIS-017-backup-integrity-recovery-viability-assessment.md)
  - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
  - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
  - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

- **SOPs:**
  - [SOP-001: Paging Engineering On-Call](../sops/SOP-001-paging-engineering-oncall.md)
  - [SOP-002: Incident Handoff Between Geos](../sops/SOP-002-incident-handoff-between-geos.md)
  - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **Knowledge Base Articles:**
  - [ ] Link to ransomware-specific KB articles (e.g., known ransomware family write-ups, decryptor references, PIRs)

## 10. Appendices

- **Contact List:**
  - [ ] Incident Response leadership, on-call engineers, Legal/Privacy, Executive sponsors, cyber insurance, law enforcement liaison

- **Templates:**
  - [ ] Incident log, executive update template, customer/regulator notification templates, evidence collection forms

- **Process Flowchart:**
  - [ ] Visual diagram of the ransomware playbook workflow (containment → analysis → eradication → recovery → hardening)

- **Outputs:**
  - Containment status
  - Impacted system inventory
  - Timeline of compromise
  - Recovery status
  - Indicators of compromise (IOCs)
  - Executive reporting
  - PIR documentation

- **Common Failure Modes:**
  - Restoring systems before containment validation
  - Leaving privileged sessions active
  - Failing to isolate backup infrastructure
  - Ignoring persistence mechanisms
  - Reconnecting systems too early

- **Automation Opportunities:**
  - Automated host isolation
  - Network segmentation workflows
  - IOC-based detection sweeps
  - Session revocation
  - Backup integrity validation checks

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
