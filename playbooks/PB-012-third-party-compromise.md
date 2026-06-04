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

- RB-TRIAGE-004 Third-Party Notification Validation *(To Be Created)*

### Analysis

- RB-ANALYSIS-027 Third-Party Exposure Assessment
- RB-ANALYSIS-028 Supply Chain Impact Analysis
- RB-ANALYSIS-007 Authentication Log Analysis
- RB-ANALYSIS-009 Privileged Access Assessment
- RB-ANALYSIS-011 Identify Additional Compromised Accounts

### Containment

- RB-CONTAIN-001 Account Lockdown
- RB-CONTAIN-005 Session & Token Revocation
- RB-CONTAIN-008 Third-Party Access Restriction

### Recovery

- RB-RECOVERY-005 Third-Party Trust Restoration

### Post-Incident

- RB-POST-002 Regulatory & Legal Coordination

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

### 1. Validate Third-Party Compromise Notification

Runbook:

- RB-TRIAGE-004 Third-Party Notification Validation *(To Be Created)*

Actions:

- Validate notification legitimacy
- Verify reporting source
- Identify affected vendor, supplier, or service provider
- Determine whether the organisation uses the affected product or service
- Collect vendor advisories, CVEs, and technical references
- Determine whether compromise is confirmed, suspected, or under investigation
- Identify affected products, versions, and services
- Identify internal business owners
- Establish communication channels with the vendor

Decision Point:

If the organisation does not use the affected vendor or service:

- Document findings
- Downgrade severity or close investigation

If the organisation uses the affected vendor or service:

- Proceed to Exposure Assessment

---

### 2. Assess Third-Party Exposure

Runbook:

- RB-ANALYSIS-027 Third-Party Exposure Assessment

Actions:

- Review vendor access
- Review service accounts
- Review API integrations
- Review SaaS integrations
- Review federated identity relationships
- Review trust relationships
- Review data access

---

### 3. Perform Supply Chain Impact Analysis

Runbook:

- RB-ANALYSIS-028 Supply Chain Impact Analysis

Actions:

- Identify affected products and versions
- Identify impacted assets
- Review deployment footprint
- Review vulnerable dependencies
- Review downstream dependencies
- Assess potential attack paths

Decision Point:

If vulnerable products are deployed:

- Continue investigation

If vulnerable products are not deployed:

- Document findings
- Reduce severity as appropriate

---

### 4. Review Authentication Activity

Runbook:

- RB-ANALYSIS-007 Authentication Log Analysis

Actions:

- Review vendor account activity
- Review privileged logins
- Review service account usage
- Review API authentication
- Review federated authentication activity

---

### 5. Assess Privileged Access

Runbook:

- RB-ANALYSIS-009 Privileged Access Assessment

Actions:

- Review privileged vendor access
- Review administrative permissions
- Review privileged service accounts
- Review delegated administration

Decision Point:

If privileged access exposure exists:

- Escalate severity
- Accelerate containment activities

---

### 6. Identify Additional Exposure

Runbook:

- RB-ANALYSIS-011 Identify Additional Compromised Accounts

Actions:

- Review related accounts
- Review delegated access
- Review service account activity
- Expand investigation scope

---

### 7. Restrict Third-Party Access

Runbooks:

- RB-CONTAIN-001 Account Lockdown
- RB-CONTAIN-005 Session & Token Revocation
- RB-CONTAIN-008 Third-Party Access Restriction

Actions:

- Disable vendor accounts
- Revoke sessions
- Revoke tokens
- Disable integrations
- Restrict trust relationships
- Restrict privileged access

---

### 8. Assess Data Exposure & Secondary Impact

Actions:

- Review accessed resources
- Review file access
- Review SaaS activity
- Review cloud activity
- Review audit logs

Decision Point:

If evidence of data exposure exists:

Activate:

- PB-005 Data Exfiltration

If evidence of credential compromise exists:

Activate:

- PB-004 Account Takeover

If evidence of cloud compromise exists:

Activate:

- PB-007 Cloud Compromise

---

### 9. Restore Trusted Access

Runbook:

- RB-RECOVERY-005 Third-Party Trust Restoration

Actions:

- Validate vendor remediation
- Rotate credentials
- Restore approved integrations
- Restore trust relationships
- Validate monitoring controls
- Validate business functionality

---

### 10. Regulatory & Legal Coordination

Runbook:

- RB-POST-002 Regulatory & Legal Coordination

Actions:

- Assess notification obligations
- Coordinate legal review
- Coordinate executive communications
- Document lessons learned
- Review vendor risk posture

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
