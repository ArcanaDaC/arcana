# PB-012: Third-Party Compromise

## Overview

This playbook outlines the response process for security incidents involving vendors, suppliers, managed service providers, software providers, cloud service providers, and other third-party entities that may impact organisational security.

This playbook is intended for:

- Vendor compromise notifications
- Supply chain incidents
- SaaS provider compromise
- MSP compromise
- Software supply chain attacks
- Third-party credential exposure
- Partner environment compromise
- Dependency compromise
- Trusted relationship abuse

---

## Status

Live

---

## Warning

Do NOT assume a third-party compromise directly impacts your environment.

Likewise, do NOT assume no impact exists simply because no indicators have been identified.

Many supply chain incidents involve:

- Delayed attacker activity
- Credential abuse
- Software update abuse
- API compromise
- Trusted relationship exploitation
- Long-term persistence

Impact assessments must be evidence-based.

---

## Immediate Emergency Actions

1. Validate compromise notification
2. Identify impacted vendor relationships
3. Assess organisational exposure
4. Preserve relevant logs and evidence
5. Identify active integrations
6. Review privileged third-party access
7. Notify Incident Response leadership

---

## Linked Runbooks

### Triage

- [RB-TRIAGE-001 Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)

### Analysis

- [RB-ANALYSIS-007 Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)
- [RB-ANALYSIS-009 Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)
- [RB-ANALYSIS-011 Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

### Containment

- [RB-CONTAIN-001 Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
- [RB-CONTAIN-005 Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)

### Recovery

- [RB-RECOVERY-003 User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

### Post-Incident

- [RB-POST-002 Regulatory & Legal Coordination](../runbooks/post-incident/RB-POST-002-regulatory-legal-coordination.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- Vendor breach notification received
- SaaS provider compromise announced
- Supply chain compromise identified
- Third-party credentials exposed
- Managed service provider compromised
- Software dependency compromise identified
- Partner organisation reports breach
- Trusted integration abuse identified

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev3 | Third-party compromise with no confirmed organisational impact |
| Sev2 | Limited organisational exposure identified |
| Sev1 | Confirmed access, data exposure, or attacker activity |
| Sev0 | Widespread compromise impacting critical business operations |

---

## Objectives

- Validate third-party compromise
- Assess organisational exposure
- Identify impacted assets and identities
- Remove unnecessary trust relationships
- Contain active risk
- Recover securely
- Improve third-party risk posture

---

## Required Inputs

- Vendor notifications
- Authentication logs
- IAM logs
- SaaS audit logs
- Cloud audit logs
- Asset inventory
- Vendor inventory
- Third-party access records

---

## Playbook Workflow

### 1. Validate Third-Party Compromise

Runbook:

- [RB-TRIAGE-001 Email Triage & Header Analysis](../runbooks/triage/RB-TRIAGE-001-email-triage-header-analysis.md)

Actions:

- Validate notification legitimacy
- Verify reporting source
- Collect incident details
- Identify affected products and services

---

### 2. Assess Organisational Exposure

Runbook:

- [RB-ANALYSIS-009 Privileged Access Assessment](../runbooks/analysis/RB-ANALYSIS-009-privileged-access-assessment.md)

Actions:

- Review vendor access
- Review privileged access
- Review service accounts
- Review API integrations
- Review trust relationships

---

### 3. Authentication & Access Review

Runbook:

- [RB-ANALYSIS-007 Authentication Log Analysis](../runbooks/analysis/RB-ANALYSIS-007-authentication-log-analysis.md)

Actions:

- Review vendor account activity
- Review authentication anomalies
- Review session activity
- Review API access

---

### 4. Identify Additional Exposure

Runbook:

- [RB-ANALYSIS-011 Identify Additional Compromised Accounts](../runbooks/analysis/RB-ANALYSIS-011-identify-additional-compromised-accounts.md)

Actions:

- Review related accounts
- Review delegated access
- Review service account activity
- Expand investigation scope

---

### 5. Contain Third-Party Access

Runbooks:

- [RB-CONTAIN-001 Account Lockdown](../runbooks/contain/RB-CONTAIN-001-account-lockdown.md)
- [RB-CONTAIN-005 Session & Token Revocation](../runbooks/contain/RB-CONTAIN-005-session-token-revocation.md)

Actions:

- Disable accounts where required
- Revoke sessions
- Revoke tokens
- Restrict integrations
- Restrict privileged access

---

### 6. Assess Potential Data Exposure

Actions:

- Review accessed resources
- Review SaaS activity
- Review cloud activity
- Review file access
- Review audit logs

Decision Point:

If evidence of data exposure exists:

Activate:

- PB-005 Data Exfiltration

---

### 7. Assess Credential Exposure

Actions:

- Review exposed credentials
- Review service accounts
- Review API keys
- Review certificates

Decision Point:

If credential compromise exists:

Activate:

- PB-004 Account Takeover

---

### 8. Scope Expansion Investigation

Actions:

- Identify additional vendors
- Review related integrations
- Review trust relationships
- Assess downstream impact

---

### 9. Recovery & Restoration

Runbook:

- [RB-RECOVERY-003 User Recovery & Access Restoration](../runbooks/recovery/RB-RECOVERY-003-user-recovery-access-restoration.md)

Actions:

- Restore approved access
- Rotate credentials
- Re-enable services
- Validate security controls

---

### 10. Regulatory & Legal Coordination

Runbook:

- [RB-POST-002 Regulatory & Legal Coordination](../runbooks/post-incident/RB-POST-002-regulatory-legal-coordination.md)

Actions:

- Assess notification requirements
- Coordinate legal review
- Coordinate executive communications
- Document lessons learned

---

## Playbook Relationships

Third-party compromise incidents frequently evolve into other incident types.

Additional playbooks should be activated when evidence supports them.

### Common Escalations

| Evidence Identified | Activate Playbook |
|---|---|
| Account compromise | PB-004 Account Takeover |
| Data exposure | PB-005 Data Exfiltration |
| Cloud environment compromise | PB-007 Cloud Compromise |
| Malware activity | PB-003 Endpoint Malware |
| Privilege escalation | PB-009 Privilege Escalation |
| Lateral movement | PB-010 Lateral Movement |

### Operational Guidance

When additional evidence is identified:

- Continue the current playbook
- Activate related playbooks
- Execute playbooks concurrently where appropriate
- Close playbooks independently

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Credential compromise | PB-004 Account Takeover |
| Data exposure | PB-005 Data Exfiltration |
| Cloud compromise | PB-007 Cloud Compromise |
| Malware activity | PB-003 Endpoint Malware |
| Privilege escalation | PB-009 Privilege Escalation |
| Lateral movement | PB-010 Lateral Movement |

---

## Outputs

- Exposure assessment
- Impacted vendor inventory
- Impacted account inventory
- Containment actions
- Recovery actions
- Regulatory assessment
- Risk reduction recommendations

---

## Common Failure Modes

- Blindly trusting vendor notifications
- Failing to review service accounts
- Ignoring API integrations
- Missing delegated access relationships
- Failing to assess downstream impact

---

## Automation Opportunities

- Vendor inventory correlation
- Third-party access reviews
- API key inventory reviews
- Trust relationship mapping
- Exposure assessment automation

---

## Related

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
