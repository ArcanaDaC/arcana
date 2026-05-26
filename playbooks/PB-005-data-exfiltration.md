# PB-005: Data Exfiltration

## Overview

This playbook outlines the response process for suspected or confirmed data exfiltration incidents involving unauthorised access, staging, transfer, or exposure of organisational data.

This playbook is intended for:
- Data theft incidents
- Large outbound transfers
- Cloud storage abuse
- Insider-driven exfiltration
- SaaS data extraction
- Sensitive file exposure
- Staged data collection activity

---

## Status

Live

---

## Warning

Do NOT assume exfiltration is complete or isolated until:
- Data staging activity has been investigated
- Adjacent systems and accounts have been reviewed
- Cloud and SaaS access has been validated
- Outbound transfer paths have been identified

Attackers frequently maintain persistence after initial exfiltration.

---

## Immediate Emergency Actions

1. Contain active exfiltration channels immediately
2. Isolate impacted accounts or systems where required
3. Preserve logs and volatile evidence
4. Identify sensitive data exposure scope
5. Protect backup and archival systems
6. Notify Incident Response leadership
7. Engage legal/compliance teams if regulated data involved

---

## Linked Runbooks

- [RB-005.1 Exfiltration Alert Triage](../runbooks/data-exfiltration/RB-005.1-exfiltration-alert-triage.md)
- [RB-005.2 Outbound Traffic Analysis](../runbooks/data-exfiltration/RB-005.2-outbound-traffic-analysis.md)
- [RB-005.3 Data Staging Investigation](../runbooks/data-exfiltration/RB-005.3-data-staging-investigation.md)
- [RB-005.4 Cloud Storage & SaaS Review](../runbooks/data-exfiltration/RB-005.4-cloud-storage-saas-review.md)
- [RB-005.5 Sensitive Data Impact Assessment](../runbooks/data-exfiltration/RB-005.5-sensitive-data-impact-assessment.md)
- [RB-005.6 Account & Endpoint Containment](../runbooks/data-exfiltration/RB-005.6-account-endpoint-containment.md)
- [RB-005.7 Exfiltration Scope Expansion Hunt](../runbooks/data-exfiltration/RB-005.7-exfiltration-scope-expansion-hunt.md)
- [RB-005.8 Regulatory & Legal Coordination](../runbooks/data-exfiltration/RB-005.8-regulatory-legal-coordination.md)
- [RB-005.9 Recovery & Exposure Mitigation](../runbooks/data-exfiltration/RB-005.9-recovery-exposure-mitigation.md)
- [RB-005.10 Post-Incident Hardening](../runbooks/data-exfiltration/RB-005.10-post-incident-hardening.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- Large outbound transfer detected
- Unusual cloud upload activity identified
- Sensitive file access anomalies detected
- DLP alert triggered
- Suspicious archive creation activity observed
- Unauthorised SaaS sharing identified
- Insider threat indicators observed
- Threat actor staging behaviour identified

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev3 | Suspicious transfer activity with no confirmed exposure |
| Sev2 | Confirmed exfiltration of limited data |
| Sev1 | Sensitive or regulated data confirmed exposed |
| Sev0 | Large-scale data theft or critical business impact |

---

## Objectives

- Stop ongoing exfiltration activity
- Identify impacted data
- Determine exposure scope
- Identify attacker access paths
- Preserve forensic evidence
- Coordinate legal/regulatory response
- Prevent repeat exposure

---

## Required Inputs

- DLP telemetry
- Proxy and firewall logs
- Cloud audit logs
- SaaS audit telemetry
- Endpoint telemetry
- Authentication logs
- File access telemetry
- Threat intelligence

---

## Playbook Workflow

---

### 1. Initial Exfiltration Alert Triage

Runbook:
- [RB-005.1 Exfiltration Alert Triage](../runbooks/data-exfiltration/RB-005.1-exfiltration-alert-triage.md)

Actions:
- Validate alert legitimacy
- Identify impacted systems/accounts
- Assess transfer characteristics
- Review alert telemetry
- Determine urgency

Decision Point:
- If false positive suspected:
  - Validate before containment

---

### 2. Outbound Traffic Analysis

Runbook:
- [RB-005.2 Outbound Traffic Analysis](../runbooks/data-exfiltration/RB-005.2-outbound-traffic-analysis.md)

Actions:
- Review outbound transfers
- Identify external destinations
- Assess transfer volume
- Review transfer protocols
- Identify encrypted transfer channels

Decision Point:
- If active exfiltration ongoing:
  - Escalate containment immediately

---

### 3. Data Staging Investigation

Runbook:
- [RB-005.3 Data Staging Investigation](../runbooks/data-exfiltration/RB-005.3-data-staging-investigation.md)

Actions:
- Identify archive creation activity
- Review staging directories
- Assess temporary file usage
- Review compression activity
- Identify pre-exfiltration behaviour

---

### 4. Cloud Storage & SaaS Review

Runbook:
- [RB-005.4 Cloud Storage & SaaS Review](../runbooks/data-exfiltration/RB-005.4-cloud-storage-saas-review.md)

Actions:
- Review cloud storage uploads
- Assess SaaS sharing activity
- Identify public exposure
- Review external collaboration
- Assess OAuth abuse

Decision Point:
- If tenant-wide SaaS abuse identified:
  - Expand scope investigation

---

### 5. Sensitive Data Impact Assessment

Runbook:
- [RB-005.5 Sensitive Data Impact Assessment](../runbooks/data-exfiltration/RB-005.5-sensitive-data-impact-assessment.md)

Actions:
- Identify impacted datasets
- Assess regulated data exposure
- Review intellectual property exposure
- Determine business impact
- Classify sensitivity levels

Decision Point:
- If regulated data identified:
  - Escalate to legal/compliance immediately

---

### 6. Account & Endpoint Containment

Runbook:
- [RB-005.6 Account & Endpoint Containment](../runbooks/data-exfiltration/RB-005.6-account-endpoint-containment.md)

Actions:
- Disable compromised accounts
- Isolate impacted endpoints
- Revoke sessions and tokens
- Restrict outbound access
- Preserve forensic evidence

Decision Point:
- If privileged access involved:
  - Escalate to:
    - [PB-009 Privilege Escalation](../playbooks/PB-009-privilege-escalation.md)

---

### 7. Exfiltration Scope Expansion Hunt

Runbook:
- [RB-005.7 Exfiltration Scope Expansion Hunt](../runbooks/data-exfiltration/RB-005.7-exfiltration-scope-expansion-hunt.md)

Actions:
- Hunt for related activity
- Identify additional impacted systems
- Review adjacent accounts
- Assess historical transfer activity
- Expand telemetry review

---

### 8. Regulatory & Legal Coordination

Runbook:
- [RB-005.8 Regulatory & Legal Coordination](../runbooks/data-exfiltration/RB-005.8-regulatory-legal-coordination.md)

Actions:
- Assess notification obligations
- Coordinate legal review
- Prepare stakeholder communications
- Review contractual obligations
- Coordinate regulatory engagement

---

### 9. Recovery & Exposure Mitigation

Runbook:
- [RB-005.9 Recovery & Exposure Mitigation](../runbooks/data-exfiltration/RB-005.9-recovery-exposure-mitigation.md)

Actions:
- Remove exposed access paths
- Reset credentials
- Harden access controls
- Remove public exposure
- Monitor for follow-on abuse

---

### 10. Post-Incident Hardening

Runbook:
- [RB-005.10 Post-Incident Hardening](../runbooks/data-exfiltration/RB-005.10-post-incident-hardening.md)

Actions:
- Improve DLP coverage
- Enhance monitoring
- Harden SaaS sharing controls
- Improve outbound filtering
- Review data governance controls

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Privileged access abuse | PB-009 Privilege Escalation |
| Insider activity identified | PB-006 Insider Threat |
| Cloud tenant compromise | PB-007 Cloud Compromise |
| Malware-assisted exfiltration | PB-003 Endpoint Malware |
| Ransomware-linked exfiltration | PB-002 Ransomware |

---

## Outputs

- Exfiltration timeline
- Impacted data inventory
- Exposure assessment
- Containment status
- Regulatory assessment
- Recovery status
- Hardening recommendations

---

## Common Failure Modes

- Focusing only on outbound traffic
- Ignoring staging behaviour
- Missing SaaS exposure
- Delayed legal escalation
- Failing to review historical exfiltration activity

---

## Automation Opportunities

- Automated DLP enrichment
- Outbound transfer anomaly detection
- SaaS exposure monitoring
- Data classification mapping
- Automated scope hunting
- Regulatory notification workflows

---

## Related

- PB-002 Ransomware
- PB-003 Endpoint Malware
- PB-004 Account Takeover
- PB-006 Insider Threat
- PB-007 Cloud Compromise
- PB-009 Privilege Escalation

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
