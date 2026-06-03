# RB-004.5-OAuth & Application Consent Review

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | OAuth & Application Consent Review | |
| Version | v1.0 | |
| Owner | Enter owner/team | |
| Status | Draft | |
| Next Review Date | Enter next review date | |
| Approvals | Enter approver(s) | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- OAuth audit logs
- Application consent telemetry
- Identity provider logs
- SaaS integration inventory
- Session telemetry data
- Identity provider access
- OAuth administration portal access
- SIEM platform access
- Cloud audit logs access
- Threat intelligence platform access

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment** — Verify responsibility for OAuth and application consent review

2. **Notify Stakeholders** — Alert security and application teams of consent audit initiation

3. **Access Target System/Resource** — Prepare identity provider OAuth portal and SIEM for review

4. **Document Current State** — Record baseline of known applications and consents

5. **Preserve Evidence (if applicable)** — Capture OAuth configuration snapshots for audit trail

6. **Execute Task Steps**

   6.1. **Enumerate OAuth Applications**
   - Identify user-consented applications
   - Identify admin-consented applications
   - Document third-party integrations
   - Flag newly registered applications

   6.2. **Review Granted Permissions**
   - Assess mail access permissions
   - Assess file access permissions
   - Assess offline access permissions
   - Assess administrative scopes
   - Assess API access scopes

   6.3. **Identify Suspicious Applications**
   - Review for unknown publishers
   - Flag recently registered applications
   - Identify excessive permission requests
   - Review suspicious redirect URIs
   - Flag low-reputation applications

   6.4. **Review Token Activity**
   - Identify long-lived refresh tokens
   - Document persistent delegated access
   - Review API abuse activity
   - Identify unusual application behaviour

   6.5. **Remove Malicious Access**
   - Remove malicious applications
   - Revoke tokens
   - Revoke consents
   - Invalidate API credentials

   6.6. **Validate Tenant Integrity**
   - Confirm no malicious applications remain
   - Verify permissions reviewed
   - Confirm persistent access removed
   - Enforce user consent policies

7. **Verify Task Completion** — Confirm OAuth inventory complete and suspicious apps identified

8. **Update Incident Documentation** — Record application findings and revocation actions

9. **Escalate if Issues Arise** — Flag admin-consented malicious apps for immediate escalation

10. **Hand Off or Notify Next Responsible Party** — Pass to access management team for policy review

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Admin-consented malicious app identified | Immediate escalation |
| Multiple users impacted | Expand tenant-wide review |
| Persistent API abuse observed | Increase containment scope |

---

## Output

- OAuth application inventory
- Suspicious application findings
- Revoked application list
- Permission exposure assessment

---

## Common Failure Modes

- Ignoring refresh token persistence
- Failing to review admin-consented applications
- Removing apps without revoking tokens

---

## Automation Hooks

- Auto-OAuth inventory collection
- Auto-permission risk scoring
- Auto-consent anomaly detection
- Auto-token revocation

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.4 MFA Reset & Validation](./RB-004.4-mfa-reset-validation.md)
- Next: [RB-004.6 Privileged Access Assessment](./RB-004.6-privileged-access-assessment.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
