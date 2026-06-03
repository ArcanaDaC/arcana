# RB-004.9 User Recovery & Access Restoration

## Document Control
| Attribute | Value | Date |
| --- | --- | --- |
| Document Name | User Recovery & Access Restoration | |
| Version | v1.0 | |
| Owner | [Enter owner/team] | |
| Status | Draft | |
| Next Review Date | [Enter next review date] | |
| Approvals | [Enter approver(s)] | |
| Change Summary | Initial draft | |

## 1. Prerequisites
- Containment status
- Session revocation status
- MFA reset status
- Identity integrity assessment
- Endpoint assessment findings
- Access to identity provider
- Access to MFA platform
- Access to endpoint management platform
- Access to SIEM
- Access to service desk tooling

## 2. Step-by-Step Instructions

1. **Confirm Task Assignment**

2. **Notify Stakeholders**

3. **Access Target System/Resource**

4. **Document Current State**
   - Capture current containment status
   - Document current user access restrictions

5. **Preserve Evidence (if applicable)**
   - Document containment actions taken

6. **Execute Task Steps**
   - **6.1 Validate Containment Completion**
     - Confirm sessions revoked
     - Confirm tokens invalidated
     - Confirm OAuth abuse addressed
     - Confirm rogue devices removed
     - Confirm credentials reset

   - **6.2 Validate Endpoint Integrity**
     - Review malware investigation findings
     - Review endpoint telemetry
     - Review browser security posture
     - Review device compliance status

   - **6.3 Reset Credentials Securely**
     - Require strong password creation
     - Require MFA enforcement
     - Require identity verification
     - Require password reuse prevention

   - **6.4 Re-Enroll MFA**
     - Validate trusted MFA methods
     - Validate approved devices
     - Validate recovery methods
     - Validate conditional access enforcement

   - **6.5 Restore User Access**
     - Re-enable identity provider access
     - Re-enable SaaS access
     - Re-enable VPN access
     - Re-enable email access
     - Re-enable administrative access (if applicable)

   - **6.6 Monitor for Re-Compromise**
     - Monitor new suspicious logins
     - Monitor session anomalies
     - Monitor OAuth abuse
     - Monitor authentication failures
     - Monitor suspicious endpoint activity

7. **Verify Task Completion**
   - Confirm user recovery status documented
   - Verify access restoration timeline documented
   - Validate MFA validation status documented
   - Verify residual risk assessment documented

8. **Update Incident Documentation**
   - Record restoration actions
   - Document access restored
   - Update incident status

9. **Escalate if Issues Arise**
   - Escalate if reinfection or reuse observed
   - Escalate if endpoint integrity uncertain
   - Escalate if repeated suspicious logins observed

10. **Hand Off or Notify Next Responsible Party**
    - Notify user of account restoration
    - Provide security guidance
    - Provide MFA setup instructions

## 3. Post-Action
- Document all steps in incident record
- Participate in post-incident review if required

---

## Decision Points

| Condition | Action |
|----------|--------|
| Reinfection or reuse observed | Re-isolate immediately |
| Endpoint integrity uncertain | Delay restoration |
| Repeated suspicious logins observed | Expand investigation scope |

---

## Output

- User recovery status
- Access restoration timeline
- MFA validation status
- Residual risk assessment

---

## Common Failure Modes

- Restoring access before endpoint validation
- Reusing compromised MFA methods
- Ignoring browser token persistence

---

## Automation Hooks

- Auto-password reset workflows
- Auto-MFA enrollment validation
- Auto-risk monitoring
- Auto-session anomaly detection

---

## Related

- Playbook: [PB-004 Account Takeover](../../playbooks/PB-004-account-takeover.md)
- Previous: [RB-004.8 Adjacent Account Hunting](./RB-004.8-adjacent-account-hunting.md)
- Next: [RB-004.10 Post-Incident Identity Hardening](./RB-004.10-post-incident-identity-hardening.md)

---

## Contributor

**Vishal Thakur**  
GitHub: https://github.com/malienist

Contributed to the Arcana Incident Response Documentation Framework.
