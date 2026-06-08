# PB-011: Suspicious Execution

## Overview

This playbook outlines the response process for suspicious process execution activity that may indicate malware execution, attacker activity, script abuse, privilege escalation attempts, credential theft, or other malicious activity on an endpoint.

This playbook is frequently used as an initial investigative workflow before a specific incident type has been confirmed.

This playbook is intended for:

- Suspicious process execution
- PowerShell abuse
- LOLBin abuse
- Encoded command execution
- Script execution alerts
- Suspicious parent-child process relationships
- Unknown binary execution
- EDR behavioural detections
- Suspicious command-line activity

---

## Status

Live

---

## Warning

Do NOT assume suspicious execution represents malware until sufficient evidence exists.

Many modern attacks leverage legitimate tools and operating system binaries.

Likewise, do NOT assume activity is benign because:

- The process is signed
- The process completed successfully
- The user initiated execution
- Antivirus did not detect malware

Suspicious execution should be treated as a potential precursor to compromise until validated.

---

## Immediate Emergency Actions

1. Validate execution activity
2. Identify impacted endpoint and user
3. Preserve execution telemetry
4. Determine whether activity is ongoing
5. Review command-line activity
6. Assess attacker objectives
7. Escalate to related playbooks if compromise indicators are identified

---

## Linked Runbooks

### Triage

- [RB-TRIAGE-002 EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)

### Analysis

- [RB-ANALYSIS-006 Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)
- [RB-ANALYSIS-014 Malware Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-malware-persistence-mechanism-hunt.md)
- [RB-ANALYSIS-023 Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)
- [RB-ANALYSIS-024 LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)
- [RB-ANALYSIS-025 Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)
- [RB-ANALYSIS-026 User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)
- [RB-ANALYSIS-022 Exfiltration Scoping Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scoping-hunt.md)

### Containment

- [RB-CONTAIN-004 Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)

### Post-Incident

- [RB-POST-001 Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- Suspicious process execution detected
- Encoded PowerShell execution observed
- LOLBin abuse detected
- Suspicious script execution identified
- Unusual command-line arguments detected
- EDR behavioural alert triggered
- Suspicious binary execution identified
- Unsanctioned administrative tooling observed

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev3 | Suspicious execution requiring validation |
| Sev2 | Confirmed malicious or unauthorised execution on a single endpoint |
| Sev1 | Execution linked to attacker activity, persistence, or credential theft |
| Sev0 | Widespread malicious execution across multiple systems |

---

## Objectives

- Validate execution activity
- Identify execution source
- Determine attacker intent
- Assess compromise scope
- Preserve evidence
- Contain malicious activity
- Escalate appropriately

---

## Required Inputs

- EDR telemetry
- Process telemetry
- Command-line logs
- Endpoint logs
- Authentication logs
- Threat intelligence
- User activity records

---

## Playbook Workflow

### 1. Initial Alert Triage

Runbook:

- [RB-TRIAGE-002 EDR Alert Triage](../runbooks/triage/RB-TRIAGE-002-edr-alert-triage.md)

Actions:

- Validate detection
- Assess severity
- Identify endpoint
- Identify user context
- Determine urgency

---

### 2. Process Tree Analysis

Runbook:

- [RB-ANALYSIS-006 Process Tree Analysis](../runbooks/analysis/RB-ANALYSIS-006-process-tree-analysis.md)

Actions:

- Review process ancestry
- Review child processes
- Identify execution chain
- Assess suspicious relationships

---

### 3. Command-Line Analysis

Runbook:

- [RB-ANALYSIS-023 Command-Line Analysis](../runbooks/analysis/RB-ANALYSIS-023-command-line-analysis.md)

Actions:

- Review arguments
- Decode encoded commands
- Identify obfuscation
- Identify download cradles
- Identify suspicious switches

---

### 4. LOLBin Abuse Investigation

Runbook:

- [RB-ANALYSIS-024 LOLBin Abuse Investigation](../runbooks/analysis/RB-ANALYSIS-024-lolbin-abuse-investigation.md)

Actions:

- Review PowerShell usage
- Review Rundll32 activity
- Review Regsvr32 activity
- Review Mshta activity
- Review WMI execution

---

### 5. Script Execution Analysis

Runbook:

- [RB-ANALYSIS-025 Script Execution Analysis](../runbooks/analysis/RB-ANALYSIS-025-script-execution-analysis.md)

Actions:

- Review PowerShell scripts
- Review Python execution
- Review batch files
- Review VBS and JS execution
- Identify script origin

---

### 6. Persistence Investigation

Runbook:

- [RB-ANALYSIS-014 Malware Persistence Mechanism Hunt](../runbooks/analysis/RB-ANALYSIS-014-malware-persistence-mechanism-hunt.md)

Actions:

- Review startup locations
- Review scheduled tasks
- Review services
- Review registry persistence
- Review WMI persistence

---

### 7. User Activity Validation

Runbook:

- [RB-ANALYSIS-026 User Activity Validation](../runbooks/analysis/RB-ANALYSIS-026-user-activity-validation.md)

Actions:

- Determine whether activity was authorised
- Review change records
- Validate business purpose
- Assess administrative activity

---

### 8. Exfiltration Scoping Hunt

Runbook:

- [RB-ANALYSIS-022 Exfiltration Scoping Hunt](../runbooks/analysis/RB-ANALYSIS-022-exfiltration-scoping-hunt.md)

Actions:

- Hunt for identical binaries
- Hunt for identical command-lines
- Hunt for identical hashes
- Hunt for similar execution activity

---

### 9. Endpoint Containment

Runbook:

- [RB-CONTAIN-004 Host Isolation](../runbooks/contain/RB-CONTAIN-004-host-isolation.md)

Actions:

- Isolate host
- Restrict execution
- Preserve evidence
- Prevent additional activity

---

### 10. Post-Incident Hardening

Runbook:

- [RB-POST-001 Ransomware Post-Incident Hardening](../runbooks/post-incident/RB-POST-001-ransomware-post-incident-hardening.md)

Actions:

- Improve detections
- Improve logging
- Improve application controls
- Improve monitoring coverage

---

## Playbook Relationships

This playbook is commonly used as an entry point into broader investigations.

Execution of this playbook does not replace execution of other playbooks.

When evidence of another incident type is identified, the corresponding playbook should be activated and executed concurrently.

### Common Escalations

| Evidence Identified | Activate Playbook |
|---|---|
| Malware identified | PB-003 Endpoint Malware |
| Ransomware behaviour identified | PB-002 Ransomware |
| Credential theft identified | PB-004 Account Takeover |
| Data staging or exfiltration identified | PB-005 Data Exfiltration |
| Privilege escalation identified | PB-009 Privilege Escalation |
| Lateral movement identified | PB-010 Lateral Movement |
| Cloud abuse identified | PB-007 Cloud Compromise |

### Operational Guidance

When a related incident type is identified:

- Continue the current playbook where applicable
- Activate the related playbook
- Execute playbooks concurrently where investigative activities overlap
- Close playbooks independently once objectives are met

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Malware identified | PB-003 Endpoint Malware |
| Ransomware identified | PB-002 Ransomware |
| Credential theft identified | PB-004 Account Takeover |
| Data staging identified | PB-005 Data Exfiltration |
| Privilege escalation identified | PB-009 Privilege Escalation |
| Lateral movement identified | PB-010 Lateral Movement |
| Cloud abuse identified | PB-007 Cloud Compromise |

---

## Outputs

- Execution timeline
- Process analysis findings
- Command-line analysis findings
- Scope assessment
- Containment status
- Escalation decisions
- Hardening recommendations

---

## Common Failure Modes

- Assuming suspicious execution equals malware
- Ignoring legitimate tool abuse
- Missing persistence mechanisms
- Failing to assess execution scope
- Delaying escalation to related playbooks

---

## Automation Opportunities

- Process tree enrichment
- Command-line analysis
- LOLBin detection
- Execution anomaly detection
- Scope expansion hunting
- Automated containment

---

## Related

- PB-002 Ransomware
- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-005 Data Exfiltration
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation
- PB-010 Lateral Movement

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
