# PB-002: Ransomware Incident Response

## Overview

This playbook outlines the response process for ransomware incidents, including containment, scoping, eradication, recovery, and post-incident hardening.

This playbook is intended for:
- Endpoint ransomware
- Server encryption events
- Hypervisor / ESXi ransomware
- Double extortion incidents
- Large-scale enterprise encryption activity

---

## Warning

Do NOT begin large-scale restoration activities until:

- Containment is verified
- Persistence mechanisms are identified
- Privileged access has been reviewed
- Propagation paths are understood
- Backup integrity is validated

Premature restoration may result in reinfection or repeated encryption.

---

## Immediate Emergency Actions

1. Isolate affected systems immediately
2. Disable lateral movement pathways where possible
3. Notify Incident Response leadership
4. Preserve volatile evidence where feasible
5. Prevent additional system shutdowns or reboots unless required
6. Identify critical business systems impacted
7. Freeze non-essential administrative changes

---

## Linked Runbooks

- [RB-002.1 Rapid Containment & Network Segmentation](../runbooks/ransomware/RB-002.1-rapid-containment-network-segmentation.md)
- [RB-002.2 Identify Patient Zero](../runbooks/ransomware/RB-002.2-identify-patient-zero.md)
- [RB-002.3 Encryption Scope Assessment](../runbooks/ransomware/RB-002.3-encryption-scope-assessment.md)
- [RB-002.4 Ransomware Payload Analysis](../runbooks/ransomware/RB-002.4-ransomware-payload-analysis.md)
- [RB-002.5 Backup Integrity Validation](../runbooks/ransomware/RB-002.5-backup-integrity-validation.md)
- [RB-002.6 Active Directory Containment](../runbooks/ransomware/RB-002.6-active-directory-containment.md)
- [RB-002.7 Escalation, Legal & Executive Communications](../runbooks/ransomware/RB-002.7-escalation-legal-executive-comms.md)
- [RB-002.8 Recovery & Restoration Coordination](../runbooks/ransomware/RB-002.8-recovery-restoration-coordination.md)
- [RB-002.9 Threat Actor TTP Mapping](../runbooks/ransomware/RB-002.9-threat-actor-ttp-mapping.md)
- [RB-002.10 Post-Incident Hardening](../runbooks/ransomware/RB-002.10-post-incident-hardening.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- Ransom note detected
- Sudden file extension changes observed
- EDR ransomware alert triggered
- Multiple systems simultaneously encrypted
- Backup deletion activity detected
- ESXi or hypervisor encryption identified
- Mass file rename/write activity detected

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev1 | Confirmed ransomware on isolated system |
| Sev0 | Enterprise-wide propagation or critical infrastructure impact |

---

## Objectives

- Stop ransomware propagation immediately
- Preserve forensic evidence
- Identify initial access vector
- Determine scope and business impact
- Protect backups and recovery systems
- Restore systems safely
- Prevent reinfection

---

## Required Inputs

- EDR telemetry
- SIEM logs
- Network telemetry
- User reports
- Ransom notes
- File hashes
- Active Directory logs
- Backup platform logs

---

## Playbook Workflow

---

### 1. Initial Containment

📘 Runbook: [RB-002.1 Rapid Containment & Network Segmentation](../runbooks/ransomware/RB-002.1-rapid-containment-network-segmentation.md)

Actions:
- Isolate impacted hosts
- Segment impacted networks
- Restrict SMB and remote admin protocols
- Prevent additional propagation
- Protect critical infrastructure

**Decision Point:**
- If ransomware propagation continues:
  - Expand containment scope
  - Escalate to crisis response

---

### 2. Identify Patient Zero

📘 Runbook: [RB-002.2 Identify Patient Zero](../runbooks/ransomware/RB-002.2-identify-patient-zero.md)

Actions:
- Identify earliest impacted host
- Determine initial access vector
- Review authentication activity
- Identify propagation path
- Assess attacker dwell time

**Decision Point:**
- If phishing identified:
  - Escalate to:
    - [PB-001 Phishing](../playbooks/PB-001-phishing.md)

---

### 3. Assess Encryption Scope

📘 Runbook: [RB-002.3 Encryption Scope Assessment](../runbooks/ransomware/RB-002.3-encryption-scope-assessment.md)

Actions:
- Identify impacted systems
- Determine encrypted file shares
- Assess business impact
- Identify critical infrastructure affected
- Review backup exposure

**Decision Point:**
- If backup compromise identified:
  - Immediate executive escalation

---

### 4. Analyse Ransomware Payload & Behaviour

📘 Runbook: [RB-002.4 Ransomware Payload Analysis](../runbooks/ransomware/RB-002.4-ransomware-payload-analysis.md)

Actions:
- Identify ransomware family
- Review encryption behaviour
- Identify persistence mechanisms
- Determine malware capabilities
- Assess exfiltration behaviour

**Decision Point:**
- If data exfiltration identified:
  - Escalate to:
    - [PB-005 Data Exfiltration](../playbooks/PB-005-data-exfiltration.md)

---

### 5. Validate Backup Integrity

📘 Runbook: [RB-002.5 Backup Integrity Validation](../runbooks/ransomware/RB-002.5-backup-integrity-validation.md)

Actions:
- Validate backup availability
- Confirm backup isolation
- Review immutable storage integrity
- Identify backup deletion attempts
- Determine recovery viability

**Decision Point:**
- If backups unavailable or compromised:
  - Escalate severity immediately

---

### 6. Active Directory & Identity Containment

📘 Runbook: [RB-002.6 Active Directory Containment](../runbooks/ransomware/RB-002.6-active-directory-containment.md)

Actions:
- Review privileged account activity
- Disable compromised accounts
- Identify persistence mechanisms
- Protect identity infrastructure
- Review lateral movement techniques

**Decision Point:**
- If Domain Admin compromise confirmed:
  - Immediate enterprise-wide escalation

---

### 7. Executive, Legal & Crisis Coordination

📘 Runbook: [RB-002.7 Escalation, Legal & Executive Communications](../runbooks/ransomware/RB-002.7-escalation-legal-executive-comms.md)

Actions:
- Notify executive leadership
- Engage legal/compliance teams
- Assess regulatory obligations
- Coordinate communications strategy
- Prepare stakeholder updates

---

### 8. Recovery & Restoration Coordination

📘 Runbook: [RB-002.8 Recovery & Restoration Coordination](../runbooks/ransomware/RB-002.8-recovery-restoration-coordination.md)

Actions:
- Prioritise system restoration
- Restore in controlled phases
- Validate restored systems
- Monitor for reinfection
- Reintroduce systems gradually

**Decision Point:**
- If reinfection activity observed:
  - Halt restoration activities immediately

---

### 9. Threat Actor TTP Mapping

📘 Runbook: [RB-002.9 Threat Actor TTP Mapping](../runbooks/ransomware/RB-002.9-threat-actor-ttp-mapping.md)

Actions:
- Identify threat actor indicators
- Map observed TTPs
- Correlate with known ransomware groups
- Identify infrastructure overlaps
- Update detections and threat intelligence

---

### 10. Post-Incident Hardening

📘 Runbook: [RB-002.10 Post-Incident Hardening](../runbooks/ransomware/RB-002.10-post-incident-hardening.md)

Actions:
- Review control failures
- Improve detections
- Harden segmentation
- Review privileged access
- Improve backup protections
- Document lessons learned

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Privileged account compromise | PB-009 Privilege Escalation |
| Data exfiltration confirmed | PB-005 Data Exfiltration |
| Malware propagation continues | Major Incident / Crisis Management |
| Hypervisor or backup compromise | Executive escalation |

---

## Outputs

- Containment status
- Impacted system inventory
- Timeline of compromise
- Recovery status
- Indicators of compromise (IOCs)
- Executive reporting
- PIR documentation

---

## Common Failure Modes

- Restoring systems before containment validation
- Leaving privileged sessions active
- Failing to isolate backup infrastructure
- Ignoring persistence mechanisms
- Reconnecting systems too early

---

## Automation Opportunities

- Automated host isolation
- Network segmentation workflows
- IOC-based detection sweeps
- Session revocation
- Backup integrity validation checks

---

## Related

- PB-001 Phishing
- PB-003 Endpoint Malware
- PB-005 Data Exfiltration
- PB-009 Privilege Escalation

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
