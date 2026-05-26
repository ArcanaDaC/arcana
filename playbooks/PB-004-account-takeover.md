# PB-004: Account Takeover

## Overview

This playbook outlines the response process for account takeover (ATO) incidents involving compromised identities, session hijacking, credential abuse, MFA compromise, and unauthorised account activity.

This playbook is intended for:
- User account compromise
- Privileged account compromise
- Session hijacking
- MFA bypass or fatigue attacks
- OAuth token abuse
- Cloud identity abuse
- Credential stuffing activity

---

## Status

Placeholder

---

## Warning

Do NOT assume account compromise is limited to a single identity until:
- Session activity has been reviewed
- OAuth access has been validated
- Adjacent accounts have been investigated
- Lateral movement activity has been assessed

Identity compromise frequently results in broader environment access.

---

## Immediate Emergency Actions

1. Disable or restrict compromised accounts immediately
2. Revoke active sessions and tokens
3. Review privileged access exposure
4. Preserve authentication and session telemetry
5. Identify adjacent account compromise
6. Protect identity infrastructure
7. Notify Incident Response leadership if privileged access involved

---

## Linked Runbooks

- [RB-004.1 Identity Alert Triage](../runbooks/account-takeover/RB-004.1-identity-alert-triage.md)
- [RB-004.2 Authentication Log Analysis](../runbooks/account-takeover/RB-004.2-authentication-log-analysis.md)
- [RB-004.3 Session & Token Revocation](../runbooks/account-takeover/RB-004.3-session-token-revocation.md)
- [RB-004.4 MFA Reset & Validation](../runbooks/account-takeover/RB-004.4-mfa-reset-validation.md)
- [RB-004.5 OAuth & Application Consent Review](../runbooks/account-takeover/RB-004.5-oauth-application-consent-review.md)
- [RB-004.6 Privileged Access Assessment](../runbooks/account-takeover/RB-004.6-privileged-access-assessment.md)
- [RB-004.7 Credential Exposure Investigation](../runbooks/account-takeover/RB-004.7-credential-exposure-investigation.md)
- [RB-004.8 Adjacent Account Hunting](../runbooks/account-takeover/RB-004.8-adjacent-account-hunting.md)
- [RB-004.9 User Recovery & Access Restoration](../runbooks/account-takeover/RB-004.9-user-recovery-access-restoration.md)
- [RB-004.10 Post-Incident Identity Hardening](../runbooks/account-takeover/RB-004.10-post-incident-identity-hardening.md)

---

## Trigger Conditions

Initiate this playbook when any of the following occur:

- Suspicious login detected
- Impossible travel alert
- MFA fatigue or bypass alert
- OAuth abuse identified
- User reports suspicious account activity
- Session hijacking indicators observed
- Credential stuffing activity detected
- Privileged account anomalies identified

---

## Severity Guidelines

| Severity | Description |
|----------|------------|
| Sev3 | Suspicious login with no confirmed compromise |
| Sev2 | Confirmed compromise of standard user account |
| Sev1 | Privileged account compromise or lateral movement |
| Sev0 | Widespread identity compromise or IAM infrastructure impact |

---

## Objectives

- Contain compromised identities rapidly
- Revoke attacker access
- Identify persistence mechanisms
- Assess privilege exposure
- Determine compromise scope
- Restore secure user access
- Harden identity controls

---

## Required Inputs

- Authentication telemetry
- Identity provider logs
- MFA logs
- Session telemetry
- OAuth audit logs
- VPN telemetry
- EDR telemetry
- User reports

---

## Playbook Workflow

---

### 1. Initial Identity Alert Triage

Runbook:
- [RB-004.1 Identity Alert Triage](../runbooks/account-takeover/RB-004.1-identity-alert-triage.md)

Actions:
- Validate suspicious activity
- Identify impacted account
- Assess privilege level
- Review authentication anomalies
- Determine urgency

Decision Point:
- If false positive suspected:
  - Validate before containment

---

### 2. Authentication Log Analysis

Runbook:
- [RB-004.2 Authentication Log Analysis](../runbooks/account-takeover/RB-004.2-authentication-log-analysis.md)

Actions:
- Review login activity
- Identify suspicious IPs/devices
- Assess impossible travel
- Review MFA activity
- Build compromise timeline

Decision Point:
- If credential stuffing identified:
  - Expand scope investigation

---

### 3. Session & Token Revocation

Runbook:
- [RB-004.3 Session & Token Revocation](../runbooks/account-takeover/RB-004.3-session-token-revocation.md)

Actions:
- Revoke active sessions
- Revoke refresh tokens
- Invalidate OAuth tokens
- Terminate suspicious sessions
- Prevent continued attacker access

Decision Point:
- If attacker activity persists:
  - Escalate containment

---

### 4. MFA Reset & Validation

Runbook:
- [RB-004.4 MFA Reset & Validation](../runbooks/account-takeover/RB-004.4-mfa-reset-validation.md)

Actions:
- Reset MFA factors
- Remove rogue devices
- Validate secure MFA enrollment
- Review MFA bypass indicators
- Enforce MFA re-registration

---

### 5. OAuth & Application Consent Review

Runbook:
- [RB-004.5 OAuth & Application Consent Review](../runbooks/account-takeover/RB-004.5-oauth-application-consent-review.md)

Actions:
- Review OAuth grants
- Remove malicious applications
- Assess token abuse
- Review delegated permissions
- Validate third-party integrations

Decision Point:
- If malicious OAuth app identified:
  - Expand tenant-wide hunting

---

### 6. Privileged Access Assessment

Runbook:
- [RB-004.6 Privileged Access Assessment](../runbooks/account-takeover/RB-004.6-privileged-access-assessment.md)

Actions:
- Assess privilege exposure
- Review admin actions
- Identify privilege escalation
- Review lateral movement activity
- Validate IAM integrity

Decision Point:
- If privileged compromise identified:
  - Escalate to:
    - [PB-009 Privilege Escalation](../playbooks/PB-009-privilege-escalation.md)

---

### 7. Credential Exposure Investigation

Runbook:
- [RB-004.7 Credential Exposure Investigation](../runbooks/account-takeover/RB-004.7-credential-exposure-investigation.md)

Actions:
- Identify exposure source
- Review phishing activity
- Assess password reuse
- Review credential dumps
- Assess browser/token theft

Decision Point:
- If phishing identified:
  - Escalate to:
    - [PB-001 Phishing](../playbooks/PB-001-phishing.md)

---

### 8. Adjacent Account Hunting

Runbook:
- [RB-004.8 Adjacent Account Hunting](../runbooks/account-takeover/RB-004.8-adjacent-account-hunting.md)

Actions:
- Hunt for additional compromised accounts
- Review shared devices
- Assess token reuse
- Identify suspicious administrative activity
- Expand telemetry review

---

### 9. User Recovery & Access Restoration

Runbook:
- [RB-004.9 User Recovery & Access Restoration](../runbooks/account-takeover/RB-004.9-user-recovery-access-restoration.md)

Actions:
- Restore secure user access
- Validate account integrity
- Re-enable services
- Review user devices
- Monitor for reinfection or reuse

---

### 10. Post-Incident Identity Hardening

Runbook:
- [RB-004.10 Post-Incident Identity Hardening](../runbooks/account-takeover/RB-004.10-post-incident-identity-hardening.md)

Actions:
- Improve IAM detections
- Review MFA enforcement
- Reduce standing privilege
- Harden session policies
- Review OAuth governance
- Improve conditional access policies

---

## Escalation Paths

| Condition | Escalate To |
|----------|------------|
| Privileged account compromise | PB-009 Privilege Escalation |
| OAuth abuse identified | PB-019 Cloud Identity Compromise |
| Data exfiltration identified | PB-005 Data Exfiltration |
| Lateral movement identified | PB-010 Lateral Movement |
| Phishing identified | PB-001 Phishing |

---

## Outputs

- Impacted account inventory
- Authentication timeline
- Session revocation status
- Privilege exposure assessment
- OAuth review findings
- Recovery status
- Hardening recommendations

---

## Common Failure Modes

- Resetting passwords without revoking sessions
- Ignoring OAuth persistence
- Failing to assess adjacent account compromise
- Re-enabling compromised accounts too early
- Ignoring MFA fatigue indicators

---

## Automation Opportunities

- Automated session revocation
- OAuth risk scoring
- Identity anomaly detection
- Adjacent account hunting
- MFA reset workflows
- Conditional access enforcement

---

## Related

- PB-001 Phishing
- PB-005 Data Exfiltration
- PB-009 Privilege Escalation
- PB-010 Lateral Movement
- PB-019 Cloud Identity Compromise

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
