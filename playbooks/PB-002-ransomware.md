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
- **Incident Responder/Forensic Analyst:** Performs forensic analysis of impacted hosts, ransomware payload analysis, identifies patient zero, maps the attack timeline, and preserves evidence.
- **Other Roles:**
  - **Identity & Access Team:** Supports Active Directory containment, privileged account review, session revocation, and credential resets.
  - **Network/Infrastructure Team:** Executes network segmentation, host isolation, and protects critical infrastructure.
  - **Backup & Recovery Team:** Validates backup integrity, isolates backup infrastructure, and coordinates restoration.
  - **Legal & Compliance:** Assesses regulatory obligations, breach notification requirements, and ransom payment considerations.
  - **Executive Leadership / Crisis Management:** Approves major business decisions, authorises external communications, and coordinates with law enforcement where required.

## 4. Initial Actions

- **Immediate Steps:**
  - Perform rapid containment & segmentation - isolate affected systems and disable lateral movement pathways (restrict SMB, remote admin protocols)
    - 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
  -  Notify Incident Response leadership and assign roles
  - Preserve volatile evidence where feasible (avoid additional system shutdowns or reboots unless required)
    - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
  - Identify critical business systems impacted
  - Freeze non-essential administrative changes

  > **Decision Point:**
  > - If ransomware propagation continues → expand containment scope and escalate to crisis response / major incident management ([PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)).

## 5. Investigation & Analysis

- **Evidence Collection:**
  - For all newly identified infected hosts:
      - collect the following host telemetry over the incident window:
        - Process execution - focus on encryption binaries, backup/shadow-copy deletion and unexpected use of admin/archive tools (e.g tar, zip, WinRar)
        - File system events - mass writes/renames, ransom note creation, backup/shadow deletion
        - Script & interpreter activity - encoded/obfuscated PowerShell, bash, zsh, python; LOLBins
        - Authentication / logon - lateral movement over RDP, SSH, SMB
        - Persistence - scheduled tasks, cron, services/daemons, launch agents, autoruns
        - 📘 [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md) 
      - capture a full memory snapshot to preserve volatile artefacts before any reboot, reimage, or shutdown
        - 📘 [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
- **Analysis Steps:**
  -  Identify patient zero, initial access vector, propagation path, and dwell time
      - 📘 [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
  > **Decision Point:**
  > For each identified initial access vector, run the post-detection phases (Analysis → Recovery) of the relevant playbook concurrently alongside this one:
	> - Phishing → [PB-001: Phishing & Credential Theft](PB-001-phishing.md)
	> - Account takeover → [PB-004: Account Takeover](PB-004-account-takeover.md)
	> - Zero-day exploitation → [PB-018: Zero-Day Response](PB-018-zero-day-response.md)
	> - Known/patched vulnerability exploited → [PB-017: Vulnerability Response](PB-017-vulnerability-response.md)
	-  Assess encryption scope, impacted systems, encrypted file shares, business impact, and backup exposure
		- 📘 [RB-ANALYSIS-004: Ransomware Encryption Scope Assessment](../runbooks/analysis/RB-ANALYSIS-004-ransomware-encryption-scope-assessment.md)
    > **Decision Point:**
    > - If backup compromise identified → immediate executive escalation.
	-  Analyse ransomware payload and behaviour (family, encryption behaviour, persistence, capabilities, exfiltration)
		- 📘 [RB-ANALYSIS-013: Ransomware Payload Analysis](../runbooks/analysis/RB-ANALYSIS-013-ransomware-payload-analysis.md)
	> **Decision Point:**
	> - If data exfiltration identified → run the post-detection phases (Analysis → Recovery) of [PB-005: Data Exfiltration](PB-005-data-exfiltration.md).
	-  Map threat actor TTPs, correlate with known ransomware groups, and update detections/threat intelligence
		- 📘 [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)
		-  Document findings, timeline of compromise, and indicators of compromise (IOCs)

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
    -  Isolate impacted hosts and segment impacted networks. Restrict SMB and remote admin protocols, prevent additional propagation, protect critical infrastructure
		- 📘 [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
  - **Long-term (identity & directory) containment:**
    -  Review privileged account activity, disable compromised accounts, protect identity infrastructure
		- 📘 [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
		- 📘 [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
    > **Decision Point:**
    > - If Domain Admin compromise confirmed → immediate enterprise-wide escalation.

- **Eradication and Recovery Steps:**
	- Validate backup integrity, isolation, immutable storage integrity, and recovery viability
    	- 📘 [RB-ANALYSIS-017: Backup Integrity & Recovery Viability Assessment](../runbooks/analysis/RB-ANALYSIS-017-backup-integrity-recovery-viability-assessment.md)
    > **Decision Point:**
    > - If backups unavailable or compromised → escalate severity immediately.
	- Prioritise and coordinate phased system restoration
		- 📘 [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md) - for sequencing, prioritisation, and cross-team coordination
	- Rebuild impacted hosts from known-good images and validate before reconnection
		- 📘 [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md) - for per-host rebuild, hardening, and validation
	- Restore user access in a controlled manner
		- 📘 [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
	- Monitor for reinfection and reintroduce systems gradually
    > **Decision Point:**
    > - If reinfection activity observed → halt restoration activities immediately and return to containment.


## 7. Communication & Escalation

- **Internal Communication:**
	-  Notify executive leadership and affected business units
	-  Provide regular incident updates to leadership and impacted teams
	-  Issue org-wide advisory if propagation is broad or critical services are impacted

- **External Communication:**
	-  Engage Legal/Privacy to assess regulatory and breach notification obligations
	-  Notify customers, regulators, partners, cyber insurance, and law enforcement (if required) as directed by Legal
	-  Coordinate all external messaging with Communications Lead and Legal
		- 📘 [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
		- 📘 [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **Escalation Criteria:**

| Condition | Escalate To |
  |-----------|-------------|
  | Phishing identified as initial access vector | [PB-001: Phishing & Credential Theft](PB-001-phishing.md) |
  | Account takeover identified as initial access vector | [PB-004: Account Takeover](PB-004-account-takeover.md) |
  | Zero-day vulnerability exploited as initial access vector | [PB-018: Zero-Day Response](PB-018-zero-day-response.md) |
  | Known/patched vulnerability exploited as initial access vector | [PB-017: Vulnerability Response](PB-017-vulnerability-response.md) |
  | Data exfiltration confirmed | [PB-005: Data Exfiltration](PB-005-data-exfiltration.md) |
  | Enterprise-wide propagation, hypervisor or backup compromise | [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md) / Executive escalation |

## 8. Post-Incident Activities

- **Lessons Learned:**
  -  Schedule and conduct a Post-Incident Review (PIR)
  -  Document what went well and what needs improvement
  -  Review control failures (detection, segmentation, privileged access, backup protection)
  -  Identify and close detection gaps

- **Documentation Updates:**
  -  Update this playbook, linked runbooks, and KB articles to reflect lessons learned
  -  Update detections and threat intelligence based on observed TTPs
  -  Harden segmentation, privileged access, and backup protections
		- 📘 [RB-POST-001: Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

## 9. References & Linked Resources

- **Playbooks:**
  - [PB-001: Phishing & Credential Theft](PB-001-phishing.md)
  - [PB-004: Account Takeover](PB-004-account-takeover.md)
  - [PB-005: Data Exfiltration](PB-005-data-exfiltration.md)
  - [PB-017: Vulnerability Response](PB-017-vulnerability-response.md)
  - [PB-018: Zero-Day Response](PB-018-zero-day-response.md)
  - [PB-020: Major Security Incident Management](PB-020-major-security-incident-management.md)

- **Runbooks:**
  - [RB-CONTAIN-002: Rapid Containment & Network Segmentation](../runbooks/contain/RB-CONTAIN-002-rapid-containment-network-segmentation.md)
  - [RB-CONTAIN-003: Active Directory Containment](../runbooks/contain/RB-CONTAIN-003-active-directory-containment.md)
  - [RB-CONTAIN-005: Session Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)
  - [RB-ANALYSIS-003: Identify Patient Zero](../runbooks/analysis/RB-ANALYSIS-003-identify-patient-zero.md)
  - [RB-ANALYSIS-004: Ransomware Encryption Scope Assessment](../runbooks/analysis/RB-ANALYSIS-004-ransomware-encryption-scope-assessment.md)
  - [RB-ANALYSIS-005: Threat Actor TTP Mapping](../runbooks/analysis/RB-ANALYSIS-005-threat-actor-ttp-mapping.md)
  - [RB-ANALYSIS-013: Ransomware Payload Analysis](../runbooks/analysis/RB-ANALYSIS-013-ransomware-payload-analysis.md)
  - [RB-ANALYSIS-017: Backup Integrity & Recovery Viability Assessment](../runbooks/analysis/RB-ANALYSIS-017-backup-integrity-recovery-viability-assessment.md)
  - [RB-EVIDENCE-001: Memory Acquisition](../runbooks/evidence/RB-EVIDENCE-001-memory-acquisition.md)
  - [RB-EVIDENCE-002: Host-Based Log Acquisition](../runbooks/evidence/RB-EVIDENCE-002-host-log-acquisition.md)
  - [RB-RECOVERY-001: Recovery & Restoration Coordination](../runbooks/recovery/RB-RECOVERY-001-recovery-restoration-coordination.md)
  - [RB-RECOVERY-002: Clean System Rebuild](../runbooks/recovery/RB-RECOVERY-002-clean-system-rebuild.md)
  - [RB-RECOVERY-003: User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)
  - [RB-POST-001: Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

- **SOPs:**
  - [SOP-003: Escalation, Legal & Executive Communications](../sops/SOP-003-escalation-legal-executive-comms.md)
  - [SOP-004: User Notification](../sops/SOP-004-user-notification.md)

- **Knowledge Base Articles:**
  -  Link to ransomware-specific KB articles (e.g., known ransomware family write-ups, decryptor references, PIRs)

## 10. Appendices



## Contributor

**Vishal Thakur**
GitHub: https://github.com/malienist

**Jayden Vo**
GitHub: https://github.com/jayden-vo

Contributed to the Arcana Incident Response Documentation Framework.
