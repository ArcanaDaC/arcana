# RB-004.6-Privileged Access Assessment

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | Privileged Access Assessment | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Authentication logs
- Administrative activity logs
- Role assignment telemetry
- Endpoint telemetry
- Session activity logs
- Identity provider access
- SIEM platform access
- PAM platform access
- EDR platform access
- Cloud audit logs access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for privileged access assessment

2. **Notify Stakeholders** — Alert security and compliance teams of privilege review initiation

3. **Access Target System/Resource** — Prepare identity provider and PAM platforms for comprehensive review

4. **Document Current State** — Record baseline of privileged assignments and activity

5. **Preserve Evidence (if applicable)** — Capture IAM configuration for audit trail

6. **Execute Task Steps**

   6.1. **Identify Privileged Access Exposure**
   - Determine administrative roles assigned
   - Identify active privileged sessions
   - Assess privileged application access
   - Document shared administrative accounts

   6.2. **Review Administrative Activity**
   - Assess role assignment changes
   - Review policy modifications
   - Review access control changes
   - Review security configuration changes
   - Review administrative API activity

   6.3. **Identify Privilege Escalation Indicators**
   - Look for new privileged accounts
   - Identify group membership changes
   - Identify conditional access modifications
   - Identify MFA policy changes
   - Review service principal abuse

   6.4. **Review Lateral Movement Activity**
   - Identify remote administrative access
   - Identify cross-system authentication
   - Identify privileged session hopping
   - Identify administrative tool usage

   6.5. **Restrict or Remove Privileged Access**
   - Revoke sessions
   - Remove roles
   - Rotate credentials
   - Implement temporary administrative restrictions

   6.6. **Validate IAM Integrity**
   - Confirm no rogue administrators remain
   - Verify access policies intact
   - Verify administrative logging operational
   - Verify conditional access functioning correctly

7. **Verify Task Completion** — Confirm privilege exposure identified and remediation complete

8. **Update Incident Documentation** — Record administrative activity findings and access changes

9. **Escalate if Issues Arise** — Flag privilege escalation or IAM tampering for immediate escalation

10. **Hand Off or Notify Next Responsible Party** — Pass to access governance team for policy hardening

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Privilege escalation confirmed | Escalate to PB-009 |
| Widespread administrative activity observed | Expand investigation scope |
| IAM policy tampering identified | Immediate executive escalation |

---

## Output

- Privileged access assessment
- Administrative activity timeline
- Role exposure inventory
- IAM integrity assessment

---

## Common Failure Modes

- Failing to review inherited privilege
- Ignoring service account exposure
- Leaving privileged sessions active

---

## Automation Hooks

- Auto-role inventory collection
- Auto-privilege anomaly detection
- Auto-session revocation
- Auto-policy integrity validation

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.5 OAuth & Application Consent Review](./RB-004.5-oauth-application-consent-review.md)
- Next: [RB-004.7 Credential Exposure Investigation](./RB-004.7-credential-exposure-investigation.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
